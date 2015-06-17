[Index](../_index.md) » InventoryUnit

# (Class) [Spree::InventoryUnit](http://m.gymplayer.com/inventory_unit.rb)
Back-ordered, sold, or shipped products are stored as individual `InventoryUnit` objects to have
relevant information attached to them

### Attributes
* `state`: either `on_hand`, `backordered`, `returned` or `shipped`
* `variant_id`
* `order_id`
* `shipment_id`
* `pending`
* `line_item_id`

## Class Methods
### (Object) **backordered_for_stock_item**(stock_item)

This was refactored from a simpler query because the previous implementation
led to issues once users tried to modify the objects returned. That's due to
ActiveRecord `joins(shipment: :stock_location)` only returning readonly
objects

Returns an array of backordered inventory units as per a given stock item

### (Object) **finalize_units!**(inventory_units)
## Instance Methods
### (Object) **additional_tax_total**


### (Object) **current_or_new_return_item**


### (Object) **find_stock_item**


### (Object) **included_tax_total**


### (Object) **variant**
Remove variant default_scope `deleted_at: nil`
