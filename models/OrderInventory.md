[Index](../_index.md) » OrderInventory

# (Class) [Spree::OrderInventory](http://m.gymplayer.com/order_inventory.rb)

## Constructors
###  `[OrderInventory]()`) **initialize**(order, line_item)
Returns a new instance of OrderInventory

## Instance Attributes
### (Object) **line_item**
Returns the value of attribute line_item

### (Object) **order**
Returns the value of attribute order

### (Object) **variant**
Returns the value of attribute variant

## Instance Methods
### (Object) **inventory_units**


### (Object) **verify**(shipment = nil)
Only verify inventory for completed orders (as orders in frontend checkout have inventory 
assigned via `order.create_proposed_shipment`) or when shipment is explicitly passed

In case shipment is passed the stock location should only unstock or restock
items if the order is completed. That is so because stock items are always
unstocked when the order is completed through `shipment.finalize`
