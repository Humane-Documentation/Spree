# Tax Category (Model)
* Grouping products which are taxed the same way
* Products can be linked to Tax Categories
* A product must belong to a tax category to be taxable
* A `tax_category` can have many `tax_rates`
* One Tax Category can be set as default for the system so if a product doesn't have a related tax
 category, the default tax category would be used
* A product must belong to a tax category to be taxable
* A `tax_category` can have many `tax_rates`
* One Tax Category can be set as default for the system so if a product doesn't have a related tax
 category, the default tax category would be used

#### Attributes
* `name`
* `description`
* `is_default`
* `deleted_at`
* `tax_code`
