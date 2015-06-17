[Index](../_index.md) » Address

# (Model) [Spree::Address](https://github.com/spree/spree/blob/master/core/app/models/spree/address.rb)
* Tracks address address info, mainly for orders but can also be tied to `User` objects that come 
from `spree_auth_devise` extension
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

## Class Methods
### (Object) **build_default**


### (Object) **default**(user = nil, kind = "bill")


## Instance Methods
### (Object) **==**(other_address)


### (Object) **active_merchant_hash**
Generates an ActiveMerchant compatible address hash

### (Object) **clone**


###  (Boolean) **empty?**


### (Object) **full_name**
Can modify an address if it's not been used in an order (but checkouts
controller has finer control) def editable?

###  (Boolean) **require_phone?**


###  (Boolean) **require_zipcode?**


###  (Boolean) **same_as?**(other) Also known as: same_as### (Object) **state_text**


### (Object) **to_s**
