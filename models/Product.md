## Product (Model)
* All sellable entities within a store
* Can have unique variations, called variants
* When deleted, a product will disappear though they remain in the product database and can be 
recovered via the admin interface. This creates a clone of the product with a new permalink and SKU

#### Attributes
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

#### UI Fields
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
* *Option Types*: Select any Option to associate a product with. See [Option Types](OptionType.md)
