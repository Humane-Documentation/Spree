# Checkout

## Checkout Steps
With the exception of Registration, each step here corresponds to a state of `Order` object:

1. Registration (only if using `spree_auth_devise`, toggled through
`Spree::Auth::Config[:registration_step]` configuration setting)
2. Address Information
3. Delivery Options (Shipping Method)
4. Payment
5. Confirmation

#### Step 1: Registration
* Prior to checkout, user will be prompted to login, create a new account or a select
"guest checkout" which allows users to specify only their email
* Spree allows guest checkout by default. Use the `allow_guest_checkout` preference to change the
default setting
* `spree_auth_devise` gem adds `check_registration` before filter to all `CheckoutController`
actions (except `registration` and `update_registration` actions), which redirects to a registration
page unless one of the following is true:
    * `Spree::Auth::Config[:registration_step]` preference is not `true`
    * user is already logged in
    * current order has an email address associated with it
* `check_registration` method is defined like this:
```
def check_registration
  return unless Spree::Auth::Config[:registration_step]
  return if spree_current_user or current_order.email
  store_location
  redirect_to spree.checkout_registration_path
end
```

#### Step 2: Address Information
* Allows user to add both their billing and shipping information
* Users can click "use billing address" option to use the same address for both. (Selecting this
hides the shipping address fields using JavaScript)
* State field can be disabled by using the `Spree::Config[:address_requires_state]` preference
* You can allow an "alternate phone" field by using `Spree::Config[:alternative_shipping_phone]`
 and `Spree::Config[:alternative_shipping]` fields
* The list of countries that appear in the country select box can also be configured. Spree will
list all countries by default, but you can configure exactly which countries you would like to
appear. The list can be limited to a specific set of countries by configuring the
`Spree::Config[:checkout_zone]` preference and setting its value to the name of a [Zone]
(../models/Zone.md) containing the countries you wish to use. Spree assumes that the list of
billing and shipping countries will be the same. You can always change this logic via an
extension if this does not suit your needs.

#### Step 3: Delivery Options

Spree assumes the list of shipping methods to be dependent on the shipping address

#### Step 4: Payment
> See [Payments Guide](payments.md)

#### Step 5: Confirmation
* Final opportunity for the customer to review their order before
submitting
* Users can return to any step in the process using the back button or clicking on a step in the
"progress breadcrumb"
* This step is disabled by default (except for payment methods that support
payment profiles), but can be enabled by overriding `confirmation_required?`
method in `Spree::Order`

## Checkout Architecture

### Checkout Routes
Three custom routes in spree_core handle all of the routing for a checkout:

1) `get '/checkout', :to => 'checkout#edit', :as => :checkout`

Maps to `edit` action of `CheckoutController` and requesting this redirects to current state of the
current order. e.g. if an order was in "address" state, a request would redirect to
`'/checkout/address'`

2) `get '/checkout/:state', :to => 'checkout#edit', :as => :checkout_state`

Same as route above

3) `put '/checkout/update/:state', :to => 'checkout#update', :as => :update_checkout`

Maps to `CheckoutController#update` action which updates order data during checkout

### CheckoutController
Drives the state of an order during checkout

##### Actions
Since there is no "checkout" model, `CheckoutController` is not a typical RESTful controller and
so `spree_core` and `spree_auth_devise` gems expose a few different actions for it:

* `edit` action renders checkout/edit.html.erb template which then renders a partial with the
current order state (e.g. `app/views/spree/checkout/address.html.erb`) showing order-state-specific
fields for the user to fill in
* `update` action:
  * Updates `current_order` with parameters passed from the current step
  * Transitions order state machine using `next` event after successfully updating the order
  * Executes callbacks based on the new state after successfully transitioning
  * Redirects to the next step unless `current_order.state` is `complete`, else redirect to the
  `order_path` for `current_order`

> If you add a new state to checkout flow you'll need a new partial for it

> For security, `Spree::CheckoutController` will not update an order once checkout is complete.
Therefore it's impossible for an order to be tampered with (e.g. changing quantity) after checkout.

##### Filters
`spree_core` and `spree_auth_devise` gems define several `before_filters` for `Spree::CheckoutController`:

* `load_order`: Assigns `@order` instance variable and sets `@order.state` to `params[:state]` value.
It also runs the "before" callbacks for the current state
* `check_authorization`: Verifies that `current_user` has access to `current_order`
* `check_registration`: Checks registration status of `current_user` and redirects to
registration step if necessary

#### `Order` Model & State Machine
* `Spree::Order` state machine is the foundation of the checkout process and it utilizes
[state_machine](https://github.com/pluginaweek/state_machine) gem (used in other places too such as
`Spree::Shipment` and `Spree::InventoryUnit`)
* Checkout flow is defined in `app/models/spree/order/checkout.rb`
  * A `Spree::Order` object has an initial state of 'cart'
  * Several events can transition `Spree::Order` to different order states
  * There's no separate model or DB table for a 'cart' so the "shopping cart" is
  actually an in-progress `Spree::Order`
  * An order is considered in-progress or incomplete when its `completed_at` attribute is `nil`
  * Incomplete/abandoned orders can be filtered during reporting and it's possible to write a quick script
  to periodically purge incomplete orders

## Checkout Customization

#### 1) Adding Logic Before or After a Step
* `state_machine` gem allows implementing callbacks before or after transitioning to a particular
step
* The callbacks work similarly to [Active Record Callbacks]
(http://guides.rubyonrails.org/active_record_callbacks.html) so you can specify a method or block
of code to be executed prior to or after a transition
* If the method executed in a `before_transition` returns false the transition will not execute

##### *Example*
If you wanted to verify that users provide valid zip codes before transitioning to delivery step:

1. Implement a `valid_zip_code?` method
2. Tell the state machine to run this method before that transition by placing this in
`app/models/spree/order_decorator.rb`:
```
Spree::Order.state_machine.before_transition :to => :delivery,
                                             :do => :valid_zip_code?
```
This callback now prevents transitioning to `delivery` step if `valid_zip_code?` returned false

#### 2) Customizing the View for a Step
* Each default checkout steps has a partial under `app/views/spree/checkout`
* Changing the view for a step is as simple as overriding its relevant partial
* Alternatively, if the relevant partial has a usable theme hook, you can add your
functionality using [Deface](https://github.com/spree/deface)

## Checkout Flow DSL
* Allows defining different checkout steps and customizing checkout flow without touching
unrelated admin states (*such as "canceled" and "resumed" which an order can transition to*)
* Provides shorter syntax compared with overriding the entire `Spree::Order` state machine
* default checkout flow is defined like this:
```
checkout_flow do
  go_to_state :address
  go_to_state :delivery
  go_to_state :payment, if: ->(order) {
    order.update_totals
    order.payment_required?
  }
  go_to_state :confirm, if: ->(order) { order.confirmation_required? }
  go_to_state :complete
  remove_transition :from => :delivery, :to => :confirm
```
* You can pass a block on each checkout step definition and add logic to see if it's required
dynamically (e.g. confirmation might only be necessary when using Payment Profiles)
* These conditional states present a situation where an order could transition
from delivery to payment, confirm or complete step. We prevented delivery to confirm transition
using `remove_transition` method of the Checkout DSL
* Resulting transitions between states look like the image below:
* Two helper methods are provided on `Spree::Order` instances for convenience:
  * `checkout_steps`: Returns array list of all currently possible states of the checkout
  * `has_step?`: Used to check if the current order fulfills the requirements for a specific state

### Checkout Flow Customization
To add or remove steps to the checkout flow, you can use the `insert_checkout_step` and
`remove_checkout_step` helpers respectively

#### `insert_checkout_step` Helper
Takes a `before` or `after` option to determine where to insert the step:
```
insert_checkout_step :new_step, :before => :address
# or
insert_checkout_step :new_step, :after => :address
```

#### `remove_checkout_step` Helper
Removes just one checkout step at a time:
```
remove_checkout_step :address
remove_checkout_step :delivery
```
What will happen here is that when a user goes to checkout, they will be asked to (potentially)
fill in their payment details and then (potentially) confirm the order. This is default.
If they're not required to provide payment or confirmation for this order then checking out this
order results in immediate completion.

#### `checkout_flow` Helper
completely redefines the flow of the checkout:
```
checkout_flow do
  go_to_state :payment
  go_to_state :complete
end
```

#### Checkout View
After creating a checkout step, you'll need to create a partial for the checkout controller to
load for your custom step. e.g. if your additional checkout step is `new_step` you'll need to a
`spree/checkout/_new_step.html.erb` partial.

#### Checkout "Breadcrumb"
Spree automatically creates a progress "breadcrumb" based on available checkout states from
`Spree::Order#checkout_steps` method. If you add a new state you'll want to add its translations
in the relevant translation in `config/locales` directory of your extension or application:
```
en:
  order_state:
    new_step: New Step
```

> Use of the breadcrumb is entirely optional and doesn't need to correspond to checkout states
nor does every state need to be represented. Feel free to customize this behavior as well.
