[Index](../_index.md) » OptionType

# (Class) [Spree::OptionType](http://m.gymplayer.com/option_type.rb)
* Product options that distinguish variants
* Created at the store level (i.e. can be used with any product)
* Option types are product options that distinguish variants
* Each Option Type owns one or more Option Values
* A product must be assigned at least one option type to create variants out of it

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
