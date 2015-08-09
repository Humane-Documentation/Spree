[Index](../_index.md) » State

# (Class) [Spree::State](http://m.gymplayer.com/state.rb)

#### Attributes
* `name`
* `abbr` e.g. "CA", "NY"
* `country_id`

## Class Methods
### (Object) **find_all_by_name_or_abbr**(name_or_abbr)


### (Object) **states_group_by_country_id**
table of { country.id => [ state.id , state.name ] }, arrays sorted by name blank is added 
elsewhere, if needed

## Instance Methods
### (Object) **<=>**(other)


### (Object) **to_s**

