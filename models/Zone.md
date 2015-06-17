[Index](../_index.md) » Zone

# (Class) [Spree::Zone](http://m.gymplayer.com/zone.rb)
* Collection of either countries or states
* Order's Shipping Address (country or a state) defines its zone
and limits available Shipping Methods
* Order's zone determines its:
  * *shipping zone*: Can limit available shipping methods
  * *tax zone*: Determines applicable tax rules
* Each shipping method is assigned to only one zone

#### Attributes
* `name`
* `description`
* `default_tax`
* `zone_members_count`
* `kind`

### Attributes `shipping_methods_zones`
* `shipping_method_id`
* `zone_id`

## Class Methods
### (Object) **default_tax**


### (Object) **match**(address)
Returns the matching zone with the highest priority zone type (State, Country, Zone.) Returns nil
 in the case of no matches.

### (Object) **potential_matching_zones**(zone)


## Instance Methods
### (Object) **<=>**(other)


###  (Boolean) **contains?**(target)
Indicates whether the specified zone falls entirely within the zone performing the check.
    
###  (Boolean) **country?**


### (Object) **country_ids**
    
    
### (Object) **country_ids=**(ids)


### (Object) **country_list**
convenience method for returning the countries contained within a zone

### (Boolean)  **include?**(address)
  
  
### (Object) **kind**


###  (Boolean) **state?**


### (Object) **state_ids**


### (Object) **state_ids=**(ids)


### (Object) **zoneables**
All zoneables belonging to the zone members. Will be a collection of either countries or states 
depending on the zone type.
