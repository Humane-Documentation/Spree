[Index](../_index.md) » StockLocation

# (Class) [Spree::StockLocation](http://m.gymplayer.com/stock_location.rb)
* Any location from where inventory is shipped
* Each `StockLocation` has many `stock_items` and `stock_movements`
* Created in the admin interface via (Configuration ? Stock Locations)
* A `StockItem` is added to newly created `StockLocation` for every variant in an application

#### Attributes
* `name`
* `default`
* `address1`
* `address2`
* `city`
* `state_id`
* `state_name`
* `country_id`
* `zipcode`
* `phone`
* `active`
* `backorderable_default`
* `propagate_all_variants`
* `admin_name`

## Instance Methods
###  (Boolean) **backorderable?**(variant)


### (Object) **count_on_hand**(variant)


### (Object) **fill_status**(variant, quantity)


### (Object) **move**(variant, quantity, originator = nil)


### (Object) **propagate_variant**(variant)
Wrapper for creating a new stock item respecting the backorderable config

### (Object) **restock**(variant, quantity, originator = nil)


### (Object) **restock_backordered**(variant, quantity, originator =nil)


### (Object) **set_up_stock_item**(variant)
Return either an existing stock item or create a new one. Useful in scenarios
where the user might not know whether there is already a stock item for a
given variant

### (Object) **state_text**


###  `[StockItem](StockItem.md)`) **stock_item**(variant_id)
* Returns an instance of StockItem for the variant id
* Parameters: variant_id (`String`) -- The id of a variant.
* Returns: (`[StockItem](StockItem.md)`) -- Corresponding StockItem for the StockLocation's variant.

###  `[StockItem](StockItem.md)`) **stock_item_or_create**(variant)
* Attempts to look up StockItem for the variant, and creates one if not found.
This method accepts an instance of the variant. Other methods in this model
attempt to pass a variant, but controller actions can pass just the variant id
as a parameter.
* Parameters: variant (`[Variant](Variant.md)`) -- Variant instance.
* Returns: (`[StockItem](StockItem.md)`) -- Corresponding StockItem for the StockLocation's variant
  
### (Object) **unstock**(variant, quantity, originator = nil)

