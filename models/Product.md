[Index](../_index.md) » Product

# (Class) [Spree::Product](http://m.gymplayer.com/product.rb)
* All sellable entities within a store
* Can have unique variations, called variants
* When deleted, a product will disappear though they remain in the product database and can be 
recovered via the admin interface. This creates a clone of the product with a new permalink and SKU

## Attributes
* `name`
* `description`
* `available_on`: first date product is available for sale. If not set it will not appear for sale
* `deleted_at`: date the product is no longer available for sale
* `slug`: An SEO slug based on the product's name and is placed into its URL
* `meta_description`: description targeted at search engines
* `meta_keywords`: words/phrases targeted at search engines
* `tax_category_id`: See [Tax Categories](TaxCategory.md)
* `shipping_category_id`: See [Shipping Categories](ShippingCategory.md)
* `promotionable`
* `meta_title`

## UI Fields
* *Name*
* *Description*
* *Permalink*: What's appended to the end of a URL when someone visits the product page. You can 
change it but be cautious to avoid naming collisions with other products in your database
* *Available On*
* *Meta Description*
* *Meta Keywords*
* *Master Price*
* *Cost Price*: What the item costs to purchase or produce
* *Cost Currency*: Useful if the currency used when purchasing a product is different from the store
* *SKU*
* *Weight*: In ounces. May be used to calculate shipping cost
* *Height*: In inches. May be used to calculate shipping cost
* *Width*: In inches. May be used to calculate shipping cost
* *Depth*: In inches. May be used to calculate shipping cost
* *Shipping Categories*
* *Tax Category*
* *Taxons*: See [Taxonomies Guide](Taxonomy.md)
* *Option Types*: Select any Option to associate a product with. See [Option Type](OptionType.md)

## Methods inherited from
* [Base](Base.md)

### Methods included from
* [Spree::Preferences::Preferable](Preferences/Preferable.md)

## Instance Attributes

### (Object) **option_values_hash**
Returns the value of attribute option_values_hash

### (Object) **prototype_id**
Adding properties and option types on creation based on a chosen prototype

## Class Methods
### (Object) **active**(currency = nil)


### (Object) **add_search_scope**(name, &block)


### (Object) **add_simple_scopes**(scopes)


### (Object) **available**(available_on = nil, currency = nil)
Can't use add_search_scope for this as it needs a default argument

### (Object) **distinct_by_product_ids**(sort_order = nil)
    
    
### (Object) **like_any**(fields, values)
        

### (Object) **property_conditions**(property)


### (Object) **simple_scopes**## Instance Methods


###  (Boolean) **available?**
determine if product is available. deleted products and products with nil or future available_on 
date are not available

### (Object) **categorise_variants_from_option**(opt_type)
split variants list into hash which shows mapping of opt value onto matching variants eg 
categorise_variants_from_option(color) => -> […], “blue” -> […]

###  (Boolean) **deleted?**
use deleted? rather than checking the attribute directly. this allows extensions to override 
deleted? if they want to provide their own definition.

### (Object) **duplicate**
for adding products which are closely related to existing ones define “duplicate_extra” for 
site-specific actions, eg for additional fields
    
###  (Boolean) **empty_option_values?**
    

### (Object) **ensure_option_types_exist_for_values_hash**
Ensures option_types and product_option_types exist for keys in option_values_hash
    
###  (Boolean) **has_variants?**
the master variant is not a member of the variants array

### (Object) **master**
Master variant may be deleted (i.e. when the product is deleted) which would make AR's default
finder return nil. This is a stopgap for that little problem

### (Object) **possible_promotions**
    

### (Object) **property**(property_name)
    
    
    

### (Object) **set_property**(property_name, property_value, property_presentation = property_name)

  
### (Object) **tax_category**
    

### (Object) **total_on_hand**
    

### (Object) **variants_and_option_values**(current_currency = nil)
Suitable for displaying only variants that has at least one option value. There may be scenarios
where an option type is removed and along with it all option values. At that point all variants
associated with only those values should not be displayed to frontend users. Otherwise it breaks the
idea of having variants   
