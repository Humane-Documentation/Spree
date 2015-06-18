[Index](../_index.md) » Prototype

# (Class) [Spree::Prototype](http://m.gymplayer.com/prototype.rb)
* A Product template to quickly add new products that differ *only* in`OptionType` and or `Property`
* A way to share `OptionType` and `Property` combinations amongst different products. For instance,
if you're creating lots of shirt products, you may wish to maintain "Size" and "Color" option
types as well as a "Fitting Type" property

> See [Prototype User Guide](https://guides.spreecommerce.com/user/product_prototypes.html) for
creation details

#### Examples
Store received a shipment of picture frames with a variety of brands, sizes, colors and materials
but are similar in everything else. This is a prime use case for prototypes.

### Attributes
* `name`

### Attributes `properties_prototypes`
* `prototype_id`
* `property_id`


### Attributes `option_types_prototypes`
* `prototype_id`
* `option_type_id`

### Attributes `taxons_prototypes`
* `taxon_id`
* `prototype_id`

## Methods
### Methods inherited from
* [Base](Base.md)

### Methods included from
* [Spree::Preferences::Preferable](Preferences/Preferable.md)
