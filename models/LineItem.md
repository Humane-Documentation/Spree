[Index](../_index.md) » LineItem

# (Class) [Spree::LineItem](http://m.gymplayer.com/line_item.rb)
* Tracks an item within the context of an order; links orders and variants (products#variants)
* When a variant is added to an order, the price of that item is tracked along with the line item
 to preserve that data
* If the variant's price changes, the line item will have a record of the price at ordering time

### Attributes
* `variant_id`
* `order_id`
* `quantity`
* `price`
* `currency`
* `cost_price`
* `tax_category_id`
* `adjustment_total`
* `additional_tax_total`
* `promo_total`
* `included_tax_total`: amount if [Tax Included](../business_logic/inventory.md#Tax-Included)
taxation is in use
* `pre_tax_amount`

## Methods included from
* [DisplayMoney](DisplayMoney.md)

## Instance Attributes
### (Object) **target_shipment**
Returns the value of attribute target_shipment

## Instance Methods

### (Object) **amount** Also known as: subtotal

### (Object) **copy_price**


### (Object) **copy_tax_category**


### (Object) **discounted_amount**


### (Object) **final_amount** Also known as: total

### (Boolean)  **insufficient_stock?**


### (Object) **invalid_quantity_check**


### (Object) **options=**(options = {})


### (Object) **product**
Remove product default_scope `deleted_at: nil`###  (Boolean) **sufficient_stock?**

### (Object) **update_price**


### (Object) **variant**
Remove variant default_scope `deleted_at: nil`
