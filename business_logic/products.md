# Products Guide

## Components
### Taxonomy (Model)
See [here](../models/Taxonomy.md)

### Taxon (Model)
See [here](../models/Taxon.md)

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

## Price
See [here](../models/Price.md)

## Product Properties
See [here](../models/ProductProperty.md)

## Prototypes
See [here](../models/Prototype.md)
