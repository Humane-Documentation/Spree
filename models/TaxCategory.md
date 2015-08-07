[Index](../_index.md) » TaxCategory

# (Class) [Spree::TaxCategory](http://m.gymplayer.com/tax_category.rb)
* Grouping products which are taxed the same way
* A product must belong to a tax category to be taxable
* A `tax_category` can have many `tax_rates`
* One Tax Category can be set as default so if a product doesn't have a related tax
 category, the default tax category would apply

#### Attributes
* `name`
* `description`
* `is_default`
* `deleted_at`
* `tax_code`

## Instance Methods
### (Object) **set_default_category**
