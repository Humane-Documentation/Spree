[Index](../_index.md) » StockItem

# (Class) [Spree::StockItem](http://m.gymplayer.com/stock_item.rb)
* Represent inventory at a stock location for a specific variant
* Created automatically for each `StockLocation`
* Stock item count on hand can be increased or decreased by creating stock movements

#### Attributes
* `stock_location_id`
* `variant_id`
* `count_on_hand`
* `backorderable`
* `deleted_at`

## Instance Methods
### (Object) **adjust_count_on_hand**(value)


###  (Boolean) **available?**
Tells whether it's available to be included in a shipment

### (Object) **backordered_inventory_units**


###  (Boolean) **in_stock?**


### (Object) **reduce_count_on_hand_to_zero**


### (Object) **set_count_on_hand**(value)


### (Object) **variant**


### (Object) **variant_name**

