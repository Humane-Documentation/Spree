## Address (Model)
* Tracks address info, mainly for orders but can also be tied to `User` objects that come from
`spree_auth_devise` extension
* Easy way to get the state info for the address is to call `state_text` on that object

### Attributes
* `firstname`
* `lastname`
* `company`
* `address1`
* `address2`
* `city`
* `zipcode`
* `phone`
* `state_name`: address must link to a `State` (if there were any)
* `alternative_phone`
* `company`: address must link to a `Country`
* `state_id`
* `country_id`
