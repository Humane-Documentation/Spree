# Geography

Spree store make decisions about [shipping](shipping.md) and [taxation](taxation.md) policies using:

### Countries
See [Country model](../models/Country.md)

### States
See [State model](../models/State.md)

### Zones
See [Zone model](../models/Zone.md)

> Add new states and countries to zones so the system can accurately calculate tax and shipping
options

*  `Spree::Config` preferences allows control of appearing address fields such as 
* State field can be disabled by using the `Spree::Config[:address_requires_state]` preference
* You can allow an "alternate phone" field by using `Spree::Config[:alternative_shipping_phone]`
 and `Spree::Config[:alternative_shipping]` fields
* The list of countries that appear in the country select box can also be configured. Spree will
list all countries by default, but you can configure exactly which countries you would like to
appear. The list can be limited to a specific set of countries by configuring the
`Spree::Config[:checkout_zone]` preference and setting its value to the name of a [Zone]
(../models/Zone.md) containing the countries you wish to use. Spree assumes that the list of
billing and shipping countries will be the same. You can always change this logic via an
extension if this does not suit your needs.