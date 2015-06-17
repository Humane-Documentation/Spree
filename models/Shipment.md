[Index](../_index.md) » Shipment

# (Class) [Spree::Shipment](http://m.gymplayer.com/shipment.rb)
* `Shipment` object is created during checkout to track shipping method the order it applies to

### Attributes
* `tracking`: identifier for shipping provider (i.e. FedEx, UPS, etc)
* `number`: unique identifier, begins with "H" and ends in an 11-digit number. Can be used to find
the order by calling `Shipment.find_by(number: number)`.=
* `cost`
* `shipped_at`
* `order_id`
* `address_id`
* `state`
* `stock_location_id`: ID of Stock Location where shipment will be sourced from
* `adjustment_total`
* `additional_tax_total`
* `promo_total`
* `included_tax_total`
* `pre_tax_amount`

### States
* `pending`: shipment has backordered inventory units and or order isn't paid
* `ready`: shipment has no backordered inventory units and order is paid
* `shipped`
* `canceled`: All order shipments are cancelled and products will be restocked. Shipment resumes
only if order is "resumed"

> For more info see [Shipping Guide](../business_logic/shipping.md)
## Classes 
* [ManifestItem](Shipment/ManifestItem.md)

## Methods included from
* [DisplayMoney](DisplayMoney.md)

## Instance Attributes
### (Object) **special_instructions**
Returns the value of attribute special_instructions

## Instance Methods
### (Object) **add_shipping_method**(shipping_method, selected = false)


### (Object) **after_cancel**


### (Object) **after_resume**


###  (Boolean) **backordered?**


### (Object) **currency**


### (Object) **determine_state**(order)
Determines the appropriate `state` according to the following logic:
pending unless order is complete and `order.payment_state` is `paid` shipped
if already shipped (ie. does not change the state) ready all other cases

### (Object) **discounted_cost** Also known as: discounted_amount


### (Boolean)  **editable_by?**(user)


### (Object) **final_price**


### (Object) **final_price_with_items**


### (Object) **finalize!**
    

###  (Boolean) **include?**(variant)


### (Object) **inventory_units_for**(variant)


### (Object) **inventory_units_for_item**(line_item, variant = nil)


### (Object) **item_cost**


### (Object) **line_items**


### (Object) **manifest**
    
    
### (Object) **process_order_payments**
    
    
###  (Boolean) **ready_or_pending?**


### (Object) **refresh_rates**(shipping_method_filter = ShippingMethod::DISPLAY_ON_FRONT_END)


### (Object) **selected_shipping_rate**


### (Object) **selected_shipping_rate_id**


### (Object) **selected_shipping_rate_id=**(id)
    

### (Object) **set_up_inventory**(state, variant, order, line_item)


### (Object) **shipped=**(value)


### (Object) **shipping_method**


### (Object) **tax_category**


### (Object) **tax_total**
Only one of either included_tax_total or additional_tax_total is set This
method returns the total of the two. Saves having to check if tax is included
or additional.
    
### (Object) **to_package**


### (Object) **tracking_url**


### (Object) **transfer_to_location**(variant, quantity, stock_location)
    
    
### (Object) **transfer_to_shipment**(variant, quantity, shipment_to_transfer_to)
    
  
### (Object) **update!**(order)
Updates various aspects of the Shipment while bypassing any callbacks. Note that this method takes
an explicit reference to the Order object. This is necessary because the association actually has a
stale (and unsaved) copy of the Order and so it will not yield the correct results.
    
### (Object) **update_amounts**
    

### (Object) **update_attributes_and_order**(params = {})
Update Shipment and make sure Order states follow the shipment changes
