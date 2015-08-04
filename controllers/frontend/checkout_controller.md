# Checkout Controller

## Filters
`spree_core` and `spree_auth_devise` gems define several `before_filters` for `Spree::CheckoutController`:

* `load_order`: Assigns `@order` instance variable and sets `@order.state` to `params[:state]` value.
It also runs the "before" callbacks for the current state
* `check_authorization`: Verifies that `current_user` has access to `current_order`
* `check_registration`: Checks registration status of `current_user` and redirects to
registration step if necessary

## Actions
Since there is no "checkout" model, `CheckoutController` is not a typical RESTful controller and
so `spree_core` and `spree_auth_devise` gems expose a few different actions for it:

### `edit`
Renders checkout/edit.html.erb template which then renders a partial with the
current order state (e.g. `app/views/spree/checkout/address.html.erb`) showing order-state-specific fields for the user to fill in

### `update`
* Updates `current_order` with parameters passed from the current step
* Transitions order state machine using `next` event after successfully updating the order
* Executes callbacks based on the new state after successfully transitioning
* Redirects to the next step unless `current_order.state` is `complete`, else redirect to the
  `order_path` for `current_order`

> For security, `Spree::CheckoutController` will not update an order once checkout is complete.
Therefore it's impossible for an order to be tampered with (e.g. changing quantity) after checkout.

## Routes
* `get '/checkout', :to => 'checkout#edit', :as => :checkout`

Maps to `edit` action of `CheckoutController` and requesting this redirects to current state of the
current order. e.g. if an order was in "address" state, a request would redirect to
`'/checkout/address'`

* `get '/checkout/:state', :to => 'checkout#edit', :as => :checkout_state`

Same as previous route

* `put '/checkout/update/:state', :to => 'checkout#update', :as => :update_checkout`

Maps to `CheckoutController#update` action which updates order data during checkout

