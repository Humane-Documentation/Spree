# Authentication

## spree_auth_devise
`spree_auth_devise` gem uses the authentication library [Devise](https://github.com/plataformatec/devise)
which provides functionalities to Spree such as:
- Basic authentication
- Strong password encryption (with ability to specify your algorithms)
- "Remember me" cookies
- "Forgot my password" emails
- Token-based access (for REST API)

### New Installation
* If it wasn't added automatically, add the following to your Gemfile
```
gem 'spree_auth_devise', github: 'spree/spree_auth_devise'
```
* Install and run the migrations:
```shell
bundle && bundle exec rake spree_auth:install:migrations
bundle exec rake db:migrate
```
* In `config/initializers/spree.rb` change `Spree.user_class = 'Spree::LegacyUser'` to
`Spree.user_class = 'Spree::User'`
In order to set up the admin user for the application you should then run:
```shell
bundle exec rake spree_auth:admin:create
```

#### Default Configurations
* Passwords are stored in the database encrypted with salt
* User authentication is done through the database query
* User registration is enabled and user's login is available immediately (no validation emails)
* A remember me and password recovery tool is built in and enabled through Devise

Devise can be further configured extensively. See [Devise wiki](https://github.com/plataformatec/devise/wiki) for more

### Existing Application Installation
> Taken from spree_auth_devise README

If installing Spree inside a host application in which you want your own permission
setup, you can use spree_auth_devise `register_ability` method:
* Create your own CanCan Ability class, e.g. `app/models/your_ability_class.rb`:
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
* Register your class in spree initializer `config/initializers/spree.rb`
```
Spree::Ability.register_ability(YourAbilityClass)
```
* Inside of your application you can then use CanCan like you normally would:
```
<% if can? :show SomeRailsObject %>
<% end %>
```

#### Confirmable
> Taken from spree_auth_devise README

To enable Devise's Confirmable module, which will send the user an email with a link to confirm
their account, you must do the following:
* Add this line to an initializer in your Rails project (typically `config/initializers/spree.rb`):
```
Spree::Auth::Config[:confirmable] = true
```
* Add a Devise initializer to your Rails project (typically `config/initializers/devise.rb`):
```
Devise.setup do |config|
  # Required so users don't lose their carts when they need to confirm.
  config.allow_unconfirmed_access_for = 1.days
  # Fixes the bug where Confirmation errors result in a broken page.
  config.router_name = :spree
  # Add any other devise configurations here, as they will override the defaults provided by spree_auth_devise.
end
```

## Custom Authentication
### `User` Model
* This guide assumes you have a pre-existing model inside your application that represents your
users. This model could be provided by gems such as [Devise](https://github.com/plataformatec/devise) or
[Sorcery](https://github.com/NoamB/sorcery)
* This guide also assumes that the application that this *User* model exists in is already a Spree
application
* This model **does not** need to be called *User*, but for guide purposes we'll use *User*

#### Initial Setup
* Edit Spree's initializer at *config/initializers/spree.rb* changing this line:

```Spree.user_class = "Spree::User"```

To this:

```Spree.user_class = "User"```

* Run the custom user generator for Spree:

```shell
bundle exec rails g spree:custom_user User
```

This creates two files. The first is a migration that adds necessary Spree fields to your users
table. The second is an extension that lives at *lib/spree/authentication_helpers.rb* to
*Spree::Core::AuthenticationHelpers* module. These tell the generator that you want to use the
*User* class as the class that represents users in Spree.
* Run the new migration:

```shell
bundle exec rake db:migrate
```

* Define methods to tell Spree where to find your application's authentication routes.

#### Authentication Helpers
Some authentication helpers of Spree's might need override. *lib/spree/authentication_helpers.rb*
contains methods to help. Each will return values common in Rails applications *but* may need
customizing:
```
module Spree
  module AuthenticationHelpers
     def self.included(receiver)
       receiver.send :helper_method, :spree_login_path
       receiver.send :helper_method, :spree_signup_path
       receiver.send :helper_method, :spree_logout_path
       receiver.send :helper_method, :spree_current_user
     end
     # Tell Spree who the current user of a request is
     def spree_current_user
       current_person
     end
     # Location of the login/sign in form in your application
     def spree_login_path
       main_app.login_path
     end
     # Location of the sign up form in your application
     def spree_signup_path
       main_app.signup_path
     end
     # Location of the logout feature of your application
     def spree_logout_path
       main_app.logout_path
     end
   end
end
Spree::BaseController.send      :include, Spree::AuthenticationHelpers
Spree::Api::BaseController.send :include, Spree::AuthenticationHelpers
ApplicationController.send      :include, Spree::AuthenticationHelpers
```
* URLs inside `spree_login_path`, `spree_signup_path` and `spree_logout_path` methods **must**
have *main_app* prefixed if they're inside your application. Spree otherwise attempts to route to
a `login_path`, `signup_path` or `logout_path` inside of itself, which does not exist. By
prefixing with `main_app`, you tell it to look at the application's routes
* You need to define the `login_path`, `signup_path` and `logout_path` routes inside your
application's `routes.rb` using code like this (if you're using Devise):
```
devise_scope :person do
  get '/login', :to => "devise/sessions#new"
  get '/signup', :to => "devise/registrations#new"
  delete '/logout', :to => "devise/sessions#destroy"
end
```
If you're not using Devise, do not use the *devise_scope* method and change the controllers and
actions for these routes

* You can customize `spree_login_path`, `spree_signup_path` and `spree_logout_path` methods
inside *lib/spree/authentication_helpers.rb* to use routing helper methods already provided
by the authentication setup you have, if you wish.

> Any modifications to files in *lib* while the server is running will require a restart

## `User` Model
Once you have specified `Spree.user_class` correctly, there will be
some new methods added to your `User` class:

* Methods added for `has_and_belongs_to_many` association, called `spree_roles`. This
association will retrieve all the roles that a user has for Spree
* Methods added for `spree_orders` association which returns all orders associated with the
user in Spree. There's also a `last_incomplete_spree_order` method which returns the last
incomplete spree order for the user. This is used internally to persist order data across a
user's login sessions
* Methods added for associations for address information for a user. When a user places an
order, the address information for that order will be linked to that user so that it is available
for subsequent orders
* `spree_api_key` getter and setter methods used for the API key that is used with Spree
* `generate_spree_api_key!` and `clear_spree_api_key` methods which generate and then clear the
Spree API key
* `has_spree_role?` method which can be used to check if a user has a specific role. This is used
internally to check if the user is authorized to perform specific actions, such as accessing the
admin section. Admin users of your system should be assigned the Spree admin role, like this:
```
user = User.find_by(email: "master@example.com")
user.spree_roles << Spree::Role.find_or_create_by(name: "admin")
```
To test this use `has_spree_role?` method; if the following returns *true* then the user has admin
permissions within Spree:
```
user.has_spree_role?("admin")
```

## Login link
To make the login link appear on Spree pages, you will need to use a Deface override.

* Create *app/overrides/auth_login_bar.rb* with this inside it:
```
Deface::Override.new(:virtual_path => "spree/shared/_nav_bar",
  :name => "auth_shared_login_bar",
  :insert_before => "li#search-bar",
  :partial => "spree/shared/login_bar",
  :disabled => false,
  :original => 'eb3fa668cd98b6a1c75c36420ef1b238a1fc55ad')
```
* This overrides partial *spree/shared/login_bar* with a new one
*app/views/spree/shared/_login_bar.html.erb* (you can change the name) which contains:
```erb
<%% if spree_current_user %>
  <li>
    <%%= link_to Spree.t(:logout), spree_logout_path, :method => :delete %>
  </li>
<%% else %>
  <li>
    <%%= link_to Spree.t(:login), spree_login_path %>
  </li>
  <li>
    <%%= link_to Spree.t(:signup), spree_signup_path %>
  </li>
<%% end %>
```
* This will use URL helpers you defined in *lib/spree/authentication_helpers.rb* to
define three links that will be visible on all customer-facing pages:
    * Link to allow users to logout
    * Link to allow them to login
    * Link to allow them to signup

## Signup Promotion
Signup promotion event in Spree will not work if you're not using standard authentication.
To fix this set a session variable, in whatever controller deals with signup, after successful
signup code to trigger a notification event:
```
session[:spree_user_signup] = true
```
This informs Spree event notifiers of this event to apply a signup promotion to the current order.
