[Index](../_index.md) » OrderUpdater

# (Class) [Spree::OrderUpdater](http://m.gymplayer.com/order_updater.rb)

## Constructors
###  `[OrderUpdater]()`) **initialize**(order)
Returns a new instance of OrderUpdater

## Instance Attributes
### (Object) **order** (readonly)
Returns the value of attribute order

## Instance Methods
### (Object) **persist_totals**


### (Object) **recalculate_adjustments**


### (Object) **run_hooks**


### (Object) **update**
This is a multi-purpose method for processing logic related to changes in the
Order. It is meant to be called from various observers so that the Order is
aware of changes that affect totals and other values stored in the Order.

This method should never do anything to the Order that results in a save call
on the object with callbacks (otherwise you will end up in an infinite
recursion as the associations try to save and then in turn try to call
`update!` again.)

### (Object) **update_adjustment_total**


### (Object) **update_item_count**


### (Object) **update_item_total**


### (Object) **update_order_total**


### (Object) **update_payment_state**
Updates the `payment_state` attribute according to the following logic:

paid when `payment_total` is equal to `total` balance_due when `payment_total`
is less than `total` credit_owed when `payment_total` is greater than `total`
failed when most recent payment is in the failed state

The `payment_state` value helps with reporting, etc. since it provides a quick
and easy way to locate Orders needing attention.

### (Object) **update_payment_total**


### (Object) **update_shipment_state**
Updates the `shipment_state` attribute according to the following logic:

shipped when all Shipments are in the “shipped” state partial when at least
one Shipment has a state of “shipped” and there is another Shipment with a
state other than “shipped” or there are InventoryUnits associated with the order that have a 
state of "sold" but are not associated with a Shipment.

ready when all Shipments are in the “ready” state backorder when there is
backordered inventory associated with an order pending when all Shipments are
in the “pending” state

The `shipment_state` value helps with reporting, etc. since it provides a
quick and easy way to locate Orders needing attention.

### (Object) **update_shipment_total**


### (Object) **update_shipments**
give each of the shipments a chance to update themselves

### (Object) **update_totals**
Updates the following Order total values:

`payment_total` The total value of all finalized Payments (NOTE: non-finalized
Payments are excluded) `item_total` The total value of all LineItems
`adjustment_total` The total value of all adjustments (promotions, credits,
etc.) `promo_total` The total value of all promotion adjustments `total` The
so-called “order total.” This is equivalent to `item_total` plus
`adjustment_total`.
