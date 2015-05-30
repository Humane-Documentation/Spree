# Authorization

## REST API
REST API behaves differently than a standard user:
* An admin has to create an access key before any user can query the REST API. This includes the
admin unless `Spree::Api::Config[:requires_authentication]` is set to `false`. In that case
read-only requests in the API will be possible for all users
* For actions that modify data a user will need to have an API key and then their user record needs
to have permission to perform those actions
* It's up to you to communicate the API key. As an added measure, this authentication has to occur on
every request made through the REST API as no session or cookies are created or stored for a REST API

## CanCan
Spree uses [CanCan](https://github.com/ryanb/cancan) gem for authorization. If you are unfamiliar
with it, you should take a look at Ryan Bates' [excellent screencast]
(http://railscasts.com/episodes/192-authorization-with-cancan) on the topic.

### Default Rules
The following is taken from `ability.rb` and provides insight into the default authorization rules:
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
The above rule set has the following practical effects for Spree users
* Admin role can access anything (rest of the rules are ignored)
* Anyone can create a `User`, only the user associated with an account can perform read or update
 operations for that user
* Anyone can create an `Order`, only the user associated with the order can perform read or update
 operations
* Anyone can read product pages and look at lists of `Products` (including search operations)
* Anyone can read or view a list of `Taxons`

### Enforcing Rules
CanCan is only effective in enforcing authorization rules if it's asked. i.e. if the
source code does not check permissions there is no way to deny access based on those permissions.
This is done by adding the appropriate code to controllers. For more see the [CanCan Wiki]
(https://github.com/ryanb/cancan/wiki).

### Custom Rules
We modified CanCan to make it easier for extension developers and users to add custom
authorization rules.

For instance, if you have an "artwork extension" that allows users to attach custom artwork to an
order, you will need to add rules so they have permissions to do so.

The trick is to add an `AbilityDecorator` to your extension and then register these abilities.
The following restricts access so only the owner of the artwork can update it or view it.
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

### Custom Roles in the Admin Namespace
* Spree authorizes all of its administrative panels with two CanCan authorization commands: `:admin`
and the name of the action being authorized
* If you want a custom role to access a particular admin panel then specify that your role *can*
access both :admin and the name of the action on the relevant resource

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

### Admin Custom Controllers
CanCan cannot detect the model used to authorize controllers under Admin namespace. If you need
to create custom controllers for models under Admin namespace, you'll need to specify the model
your controller manipulates by defining `model_class` method in that controller:
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
It may be desirable to restrict access to a particular resource without requiring a user to
authenticate to have that access. Spree allows these "guest checkouts" where users supply an email
and aren't required to create an account. To restrict access of that order to the original
customer use a "tokenized" URL.

Spree `TokenizedPermission` model is used to grant access to various resources through a secure
token. This works in conjunction with `Spree::TokenResource` module which can add tokenized
access to any Spree resource.
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
`Order` is a model where this interface is already in use. The following shows how to add this
functionality with a `token_resource` declaration:
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
