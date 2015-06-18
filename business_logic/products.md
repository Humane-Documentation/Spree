# Products Guide

## Components
### Product (Model)
See [here](../models/Product.md)

## Variants
See [here](../models/Variant.md)

## Master Variants
* Created whenever a new product is created so every product has a single master variant
* Stores master price and sku, size and weight, etc.
* Stores on_hand inventory levels/units only when there are no variants for the product
* Does not have option values associated with it
* Master variants sole purpose is having a consistent API when associating variants and
`orders#line-items`. Otherwise line items would need to track a polymorphic association which can
 be a product or a variant

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
```shell
bundle exec rake paperclip:refresh:thumbnails CLASS=Spree::Image
```
* To change the image displayed when a product has no image, create new versions of the files within [app/assets/images/noimage]

## Option Types and Option Values
See [here](../models/OptionType.md)

## Product Properties
See [here](../models/ProductProperty.md)

## Multi-Currency
* `Price` objects track a price for a particular currency and variant combination. For instance,
a Variant may be available for $15 and �7
* Presence or lack of a price for a variant in a currency will determine if the variant is visible
in the frontend. If no variants of a product have a particular price value for the site's current
currency, that product will not be visible in the frontend.
* You may see what price a product would be in the current currency (`Config[:currency]`) by calling
the `price` method on that instance:
```shell
product.price
=> "15.99"
```
* To find the currencies a product is available in, call `prices` to get related `Price` objects:
```shell
product.prices
=> [#<Spree::Price id: 2 ...]
```

## Prototypes
See [here](../models/Prototype.md)

## Taxons and Taxonomies
* `Taxonomy`: the category tree - a hierarchical list of individual Taxons
* Each `Taxonomy` relates to one `Taxon` that is its root node
* `Taxon`: a single child node which exists at a given point within a `Taxonomy`
* Each `Taxon` can contain many or no child taxons
* Admins can define many Taxonomies and link a product to multiple Taxons from each Taxonomy
* By default, both Taxons and Taxonomies are ordered by their `position` attribute
* Taxons use [Nested set model](http://en.wikipedia.org/wiki/Nested_set_model) for their hierarchy.
The `lft` and `rgt` columns in the `spree_taxons` table represent the locations within the hierarchy
of the item. This logic is handled by awesome_nested_set gem
* Taxons link to products through a `Classification` model that when a product is deleted, all links
from it to its taxons are deleted automatically. Similarly, when a taxon is deleted all links to
products are deleted automatically
* Linking to a taxon in a controller or a template should be done using `nested_taxons_path` helper
which will use the taxon's permalink to generate a URL such as `/t/categories/brand`
