# Order (Model)
A new order is initiated when a customer places a product in their shopping cart

### Attributes
* `number`: unique identifier for this order, begins with `R` and then a 9 numbers, can
 be used to find the order with `Order.find_by_number(number)`
* `item_total`: sum of all line items for this order
* `total`: sum of `item_total` and `adjustment_total`
* `state`: See Order State Machine below
* `adjustment_total`: sum of all adjustments on this order
* `user_id`: ID for user associated with the odrder if known
* `completed_at`: timestamp of when the order was completed
* `bill_address_id`: ID for related `Address` object with billing address information
* `ship_address_id`: ID for related `Address` object with shipping address information
* `payment_total`: total value of all finalized payments
* `shipping_method_id`: ID for related `ShippingMethod` object
* `shipment_state`: current shipment state. See [shipments model](Shipment.md)
* `payment_state`: current payment state. See [payments model](Payment.md)
* `email`: email address for the user who placed this order
* `special_instructions`: Will only appear if `Config[:shipping_instructions]` is set to `true`
* `currency`: Determined by `Config[:currency]` value that was set at order time
* `last_ip_address`: last IP address used to update this order in the frontend
* `created_by_id`: ID of whatever *object* created this order
* `shipment_total`: total value of all shipments' costs
* `additional_tax_total`: sum of all shipments' and line items' `additional_tax`
* `promo_total`: sum of all shipments', line items' and promotions' `promo_total`
* `channel`: channel specified if importing orders from other stores. e.g. amazon.
* `included_tax_total`: sum of all shipments' and line items' `included_tax`
* `item_count`: total value of line items' quantity
* `approver_id`: ID of user who approved this order
* `approved_at`
* `confirmation_delivered`: Boolean of confirmation email delivery
* `considered_risky`
* `guest_token`: token corresponding to the one stored in guest's cookies
* `canceled_at`
* `canceler_id`: ID of user that canceled this order
* `store_id`: ID of `Store` in which this order was created
* `state_lock_version`

### Methods
* `outstanding_balance`: calculated by taking `total` and subtracting `payment_total`
* `display_item_total`: A "pretty" version of `item_total`. If `item_total` was `10.0`,
 `display_item_total` would be `$10.00`
* `display_adjustment_total`: Same as above for `adjustment_total`
* `display_total`: Same as above for `total`
* `display_outstanding_balance`: Same as above for `outstanding_balance`

## Order States
1. `cart`: One or more products have been added to the shopping cart
2. `address`: Order is awaiting billing and shipping address data
3. `delivery`: Order is awaiting shipping method selection
4. `payment`: Order is awaiting payment data. Triggered if `payment_required?` returns `true`
5. `confirm`: Order is awaiting confirmation. Triggered if `confirmation_required?` returns `true`
6. `complete`:  reached in one of two ways:
    * No payment is required on the order
    * Payment is required on the order, and at least the order total has been received as payment

* An order cannot continue to the next state until the previous state has been satisfied
* you can transition an order by calling `next` on it. If `false` returns, then it doesn't meet
the criteria for the next state. Check the result of the `errors` method call
* Intermediary states can be configured using the Checkout Flow API (checkout)

## Order Statuses
Statuses include all order states and add to them:
* `canceled`: Either customer or store admin has chosen to cancel the order
* `awaiting return`: Customer has elected to return products, but they have not yet been received.
* `return`: Return has been processed
* `resumed`: Formerly canceled order has been reactivated






## Adjustments

