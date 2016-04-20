[Index](../_index.md) » Variant

# (Class) [Spree::Variant](http://m.gymplayer.com/variant.rb)
> Variant is also document under [Product Guide](../../Products)

* A variant tracks a group of individual properties (Option Types) of a `Product` such as height,
 width, depth, and cost price
* These properties are unique to each variant and so are on top of `Product Properties` that apply
 to all variants of a product
* All variants can access the product properties directly (via reverse delegation)
* Inventory units are tied to Variant. Other variants have option values and may have inventory units
* Sum of `on_hand` each variant's inventory level determine `on_hand` level for the product
* `sku` field holds product's stock code

#### Example
Variants: "Small, Red", "Small, Green", "Small, Blue", "Medium, Red", "Medium, Green"...

## Variants Variants

### Master Variants
* Created whenever a new product is created so every product has a single master variant
* Stores master price and sku, size and weight, etc.
* Stores on_hand inventory levels/units only when there are no variants for the product
* Does not have option values associated with it
* Master variants sole purpose is having a consistent API when associating variants and
`orders#line-items`. Otherwise line items would need to track a polymorphic association which can
 be a product or a variant

### Normal Variants
All non-master variants are  based on `option_type` and `option_value` combinations

## Images
* Images link to a product through its master variant.
* sub-variants may also have their own unique images
* Creation and storage of several size versions of each image is handled via the Paperclip plugin:
```
:styles => {
  :mini => '48x48>',
  :small => '100x100>',
  :product => '240x240>',
  :large => '600x600>'
}
```
* Image sizes can be changed by altering the value of `Config[:attachment_styles]`and regenerating
the paperclip thumbnails with this Bash command:
```bash
bundle exec rake paperclip:refresh:thumbnails CLASS=Spree::Image
```
* To change the image displayed when a product has no image, create new versions of the files within [app/assets/images/noimage]


#### Attributes
* `sku`
* `weight`
* `height`
* `width`
* `depth`
* `deleted_at`
* `is_master`
* `product_id`
* `cost_price`
* `cost_currency`
* `position`
* `track_inventory`
* `tax_category_id`
* `stock_items_count`

## Class Methods
### (Object) **active**(currency = nil)


### (Object) **having_orders**


## Instance Methods
### (Object) **amount_in**(currency)


###  (Boolean) **can_supply?**(quantity = 1)


### (Object) **cost_price=**(price)


###  (Boolean) **deleted?**
use deleted? rather than checking the attribute directly. this allows extensions to override
deleted? if they want to provide their own definition.

### (Object) **descriptive_name**


### (Object) **exchange_name**
Default to master name

###  (Boolean) **in_stock?**


###  (Boolean) **is_backorderable?**


### (Object) **name_and_sku**


### (Object) **on_backorder**
returns number of units currently on backorder for this variant.

### (Object) **option_value**(opt_name)


### (Object) **options=**(options = {})


### (Object) **options_text**


### (Object) **price_in**(currency)


### (Object) **price_modifier_amount**(options = {})


### (Object) **price_modifier_amount_in**(currency, options = {})


### (Object) **product**
Product may be created with deleted_at already set, which would make AR's default finder return
nil. This is a stopgap for that little problem.

### (Object) **set_option_value**(opt_name, opt_value)


###  (Boolean) **should_track_inventory?**
Shortcut method to determine if inventory tracking is enabled for this variant. This considers
both variant tracking flag and site-wide inventory tracking settings

### (Object) **sku_and_options_text**


### (Object) **tax_category**


### (Object) **total_on_hand**


### (Object) **weight=**(weight)

