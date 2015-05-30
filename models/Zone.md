## Zone Model
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
