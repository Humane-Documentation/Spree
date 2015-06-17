[Index](../_index.md) » StockTransfer

# (Class) [Spree::StockTransfer](http://m.gymplayer.com/stock_transfer.rb)
* Allows movement of inventory in bulk from one stock location to another
* Done in the admin interface via (Configuration ? Stock Transfers) by selecting a source location,
a destination location, one or more variants and quantity for each variant individually if needed

#### Attributes
* `type`
* `reference`
* `source_location_id`
* `destination_location_id`
* `number`

## Instance Methods
### (Object) **destination_movements**


### (Object) **receive**(destination_location, variants)


### (Object) **source_movements**


### (Object) **to_param**


### (Object) **transfer**(source_location, destination_location, variants)

  

