[Index](../_index.md) » ShippingMethod

# (Class) [Spree::ShippingMethod](http://m.gymplayer.com/shipping_method.rb)
* Carrier services used to send the product. e.g. UPS Ground, FedEx 2Day, etc.
* Can have multiple shipping categories assigned
* An order's available shipping methods can be determined by shipping categories of items included
* Each method is only applicable to a specific `Zone` to prevent sending a package internationally
using domestic shipping method

#### Attributes
* `name`
* `display_on`
* `deleted_at`
* `tracking_url`
* `admin_name`
* `tax_category_id`
* `code`

> For more info see [Shipping Guide](../business_logic/shipping.md)

## Constants
DISPLAY =[:both, :front_end, :back_end]

DISPLAY_ON_FRONT_AND_BACK_END =
Used for #refresh_rates

DISPLAY_ON_FRONT_END =1

DISPLAY_ON_BACK_END =2

## Class Methods
### (Object) **calculators**## Instance Methods


### (Object) **available_to_display**(display_filter)


### (Object) **build_tracking_url**(tracking)


###  (Boolean) **frontend?**
Some shipping methods are only meant to be set via backend

###  (Boolean) **include?**(address)


### (Object) **tax_category**

