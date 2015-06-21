# Authorization

Spree uses [CanCan](https://github.com/ryanb/cancan) gem for authorization. If you are
unfamiliar with it see Ryan Bates'
[excellent screencast](http://railscasts.com/episodes/192-authorization-with-cancan)

## Default Authorization Rules
From Spree's `ability.rb`:
```
if user.respond_to?(:has_spree_role?) && user.has_spree_role?('admin')
  can :manage, :all
else
  #############################
  can [:read,:update,:destroy], Spree.user_class, :id => user.id
  can :create, Spree.user_class
  #############################
  can :read, Order do |order, token|
    order.user == user || order.token && token == order.token
  end
  can :update, Order do |order, token|
    order.user == user || order.token && token == order.token
  end
  can :create, Order
  can :read, Address do |address|
    address.user == user
  end
  #############################
  can :read, Product
  can :index, Product
  #############################
  can :read, Taxon
  can :index, Taxon
  #############################
end
```
These rules have the following effects for Spree users:
* Admin role can access anything
* Anyone can create a `User`
* Only the user associated with an account can perform read or update operations for itself
* Anyone can create an `Order`
* Only the user associated with the order can perform read or update operations on it
* Anyone can read product pages and look at lists of `Products` (including search operations)
* Anyone can read or view a list of `Taxons`

> ### Enforcing Rules
CanCan is only effective in enforcing authorization rules if it's asked, so if the
source code does not check permissions there is no way to deny access based on them.
This is done by adding the appropriate code to controllers. For more see the
[CanCan Wiki](https://github.com/ryanb/cancan/wiki)

## Spree REST API
REST API behaves differently than a standard user:
* An admin has to create an access key before any user (including him/her) can query the
REST API unless if `Spree::Api::Config[:requires_authentication]` is set to `false` as that
enables read-only requests for all users
* For actions that modify data a user needs an *API key* and a *user record* with
permissions to perform those actions
* It's up to you to communicate the API key
* This authentication has to occur on every request made through the REST API as no session
 or cookies are created or stored for a REST API

## Authorization Customization
### From the Application
> Taken from spree_auth_devise README

To have your own permission inside a Spree application you can use the `register_ability` method:
* Create your custom CanCan Ability class, e.g. `app/models/your_ability_class.rb`:
```
class YourAbilityClass
  include CanCan::Ability
  def initialize user
    # direct permissions
     can :create, SomeRailsObject
     # or permissions by group
     if spree_user.has_spree_role? "admin"
       can :create, SomeRailsAdminObject
     end
   end
end
```
* Register it in Spree's initializer `config/initializers/spree.rb`
```
Spree::Ability.register_ability(YourAbilityClass)
```
* Use CanCan like you normally would inside your application, e.g.
```
<% if can? :show SomeRailsObject %>
<% end %>
```

### From an Extension
#### Permissions
If you want users to have permissions to perform an operation (e.g. attach custom artwork to an
order), add the relevant rules to an `AbilityDecorator` and then register these abilities.

##### *Example*
The following restricts access so only owner of an artwork can update it or view it:
```
class AbilityDecorator
  include CanCan::Ability
  def initialize(user)
    can :read, Artwork do |artwork|
      artwork.order && artwork.order.user == user
    end
    can :update, Artwork do |artwork|
      artwork.order && artwork.order.user == user
    end
  end
end
Spree::Ability.register_ability(AbilityDecorator)
```

#### Roles in the Admin Namespace
If you want a custom role to access a particular admin panel then specify that this role *can*
access both :admin and the name of the action being authorized

##### *Example*
if you want Sales Representatives to be able to access Admin Orders panel but
nothing else in the Admin namespace, specify the following in an `AbilityDecorator`:
```
class AbilityDecorator
  include CanCan::Ability
  def initialize(user)
    if user.respond_to?(:has_spree_role?) && user.has_spree_role?('sales_rep')
      can [:admin, :index, :show], Spree::Order
    end
  end
end
Spree::Ability.register_ability(AbilityDecorator)
```
This is required by the following code in Spree's `Admin::BaseController`:
```
def authorize_admin
  if respond_to?(:model_class, true) && model_class
    record = model_class
  else
    record = Object
  end
  authorize! :admin, record
  authorize! action, record
end
```

> ### Admin Custom Controllers
CanCan **cannot** detect the model used to authorize controllers under Admin namespace. If you
need to create custom controllers for models under Admin namespace, you'll need to specify the
model your controller manipulates by defining `model_class` method in that controller:
```
module Spree
  module Admin
    class WidgetsController < BaseController
      def index
        # Relevant code in here
      end
    private
      def model_class
        Widget
      end
    end
  end
end
```

## Tokenized Permissions
* It may be desirable to restrict access to a resource without requiring the user to
authenticate to have that access
* An example is "guest checkouts" where users supply an email without creating an account
and Spree restricts access of that order to them using a "tokenized" URL
* Spree `TokenizedPermission` model is used to grant access to various resources through a
secure token
* `Spree::TokenResource` module is used to add tokenized access to any Spree
resource
```
module Spree
  module Core
    module TokenResource
      module ClassMethods
        def token_resource
          has_one :tokenized_permission, :as => :permissable
          delegate :token, :to => :tokenized_permission, :allow_nil => true
          after_create :create_token
        end
      end
      def create_token
        permission = build_tokenized_permission
        permission.token = token = ::SecureRandom::hex(8)
        permission.save!
        token
      end
      def self.included(receiver)
        receiver.extend ClassMethods
      end
    end
  end
end
ActiveRecord::Base.class_eval { include Spree::Core::TokenResource }
```

##### *Example*
`Order` is a model where this interface is already in use. The following shows how to add
this functionality with a `token_resource` declaration:
```
Spree::Order.class_eval do
  token_resource
end
```
CanCan permissions for `Order` shows how tokens are used to grant access when the user isn't
authenticated:
```
  # To read or update this order you must be authenticated
  # or supply the correct authorizing token
can :read, Spree::Order do |order, token|
  order.user == user || order.token && token == order.token
end
can :update, Spree::Order do |order, token|
  order.user == user || order.token && token == order.token
end
can :create, Spree::Order
```
The final step is to ensure the token is passed to CanCan when the authorization is performed,
which is done in the controller:
```
authorize! action, resource, session[:access_token]
```
