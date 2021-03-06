[Index](../_index.md) » ProductProperty

# (Class) [Spree::ProductProperty](http://m.gymplayer.com/product_property.rb)
* Distinguishing characteristics for a product that don't change across its variants such as
description, permalink, availability, shipping category, etc.
* Provide additional information about a product to help customers make a better purchase decision
* You can retrieve a property value on a `Product` by calling `property` and passing its name:
```bash
product.property("material")
=> "100% Cotton"
```
* You can set a property on a product by calling the `set_property` method:
```
product.set_property("material", "100% cotton")
```

#### Examples
* Product: T-Shirt
* Property: "material", "fit type"

### Attributes
* `value`: e.g. *15" x 18" x 6"* or *90% Cotton, 10% Nylon*
* `product_id`
* `property_id`
* `position`

## Methods inherited from
* [Base](Base.md)

### Methods included from
* [Spree::Preferences::Preferable](Preferences/Preferable.md)

## Instance Methods
### (Object) **property_name**
virtual attributes for use with AJAX completion stuff

### (Object) **property_name=**(name)

        self.property = property


