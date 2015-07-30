[Index](../_index.md) » OptionType

# (Class) [Spree::OptionType](http://m.gymplayer.com/option_type.rb)
* Options that distinguish variants, so a a product must be assigned at least 
one option type to create variants out of it
* Each `OptionType` has one or more `OptionValues` (see example)
* Created at the store level (i.e. can be used with any product)

#### Example
Product: Baseball Jersey

| Option Type | Option Values                                     |
|-------------|---------------------------------------------------|
| Size        | Large, Small                                      |
| Wrap        | Stars, Owls, Pink Paisley, Purple Paisley, Skulls |

### Attributes
* `name`: internal, descriptive name
* `presentation`: "Display" term shown to users
* `position`

## Instance Methods
### (Object) **touch_all_products**
