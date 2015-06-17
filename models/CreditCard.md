[Index](../_index.md) » CreditCard

# (Class) [Spree::CreditCard](http://m.gymplayer.com/credit_card.rb)

### Attributes
* `month`
* `year`
* `cc_type`
* `last_digits`
* `address_id`
* `gateway_customer_profile_id`
* `gateway_payment_profile_id`
* `name`
* `user_id`
* `payment_method_id`
* `default`

## Constants
CARD_TYPES ={
      visa: /^4[0-9]{12}(?:[0-9]{3})?$/,
      master: /(^5[1-5][0-9]{14}$)|(^6759[0-9]{2}([0-9]{10})$)|(^6759[0-9]{2}([0-9]{12})$)|(^6759[0-9]{2}([0-9]{13})$)/,
      diners_club: /^3(?:0[0-5]|[68][0-9])[0-9]{11}$/,
      american_express: /^3[47][0-9]{13}$/,
      discover: /^6(?:011|5[0-9]{2})[0-9]{12}$/,
      jcb: /^(?:2131|1800|35\d{3})\d{11}$/
    }

## Instance Attributes
### (Object) **encrypted_data**
Returns the value of attribute encrypted_data

### (Object) **imported**
Returns the value of attribute imported

### (Object) **number**
Returns the value of attribute number

###  `String`) **track_data**
ActiveMerchant::Billing::CreditCard added this accessor used by some gateways.
More info: [github.com/spree/spree/issues/6209](https://github.com/spree/spree
/issues/6209)

Returns or sets the track data for the card

### (Object) **verification_value**
Returns the value of attribute verification_value

## Instance Methods
### (Object) **actions**
###  (Boolean) **can_capture?**(payment)
Indicates whether its possible to capture the payment

###  (Boolean) **can_credit?**(payment)
Indicates whether its possible to credit the payment. Note that most gateways
require that the payment be settled first which generally happens within 12-24
hours of the transaction.

###  (Boolean) **can_void?**(payment)
Indicates whether its possible to void the payment.

### (Object) **cc_type=**(type)
cc_type is set by jquery.payment, which helpfully provides different types
from Active Merchant. Converting them is necessary.### (Object) **display_number**
Show the card number, with all but last 4 numbers replace with “X”. (XXXX-
XXXX-XXXX-4338)

### (Object) **expiry=**(expiry)


### (Object) **first_name**
ActiveMerchant needs first_name/last_name because we pass it a
Spree::CreditCard and it calls those methods on it. Looking at the
ActiveMerchant source code we should probably be calling #to_active_merchant
before passing the object to ActiveMerchant but this should do for now.###  (Boolean) **has_payment_profile?**

### (Object) **last_name**


### (Object) **month**
As of rails 4.2 string columns always return strings, perhaps we should change
these to integer columns on db level

### (Object) **set_last_digits**


### (Object) **to_active_merchant**
 

### (Object) **try_type_from_number**


###  (Boolean) **verification_value?**


### (Object) **year**

