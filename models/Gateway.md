[Index](../_index.md) » Gateway

# (Class) [Spree::Gateway](http://m.gymplayer.com/gateway.rb)

### Attributes
* `type`: Tracks added payment methods
* `name`
* `description`
* `active` 
* `environment`: defaults to development
* `server`: defaults to "test"
* `test_mode`
* `preferences`

### Gateway Options
* `email` and `customer`: email address related to the order
* `ip`: Last IP address for the order
* `order_id`: Order's `number` attribute, plus the `identifier` for each payment
* `shipping`: total shipping cost for the order, in cents
* `tax`: total tax cost for the order, in cents
* `subtotal`: items total for the order, in cents
* `currency`: 3-character currency code for the order
* `discount`: promotional discount applied to the order
* `billing_address`: A hash containing billing address information
* `shipping_address`: A hash containing shipping address information

##### Billing & Shipping Addresses Fields:
* `name`: The combined `first_name` and `last_name` from the address
* `address1`: first line
* `address2`: second line
* `city`
* `state`: abbreviated state name, if not, complete name from related `State` object. If not,
`state_name` attribute from the address
* `country`: ISO name, e.g. "US", "AU"
* `phone`

## Direct Subclasses
* [Bogus](Gateway/Bogus.md), [Test](Gateway/Test.md)

## Classes 
* [Bogus](Gateway/Bogus.md), [BogusSimple](Gateway/BogusSimple.md), [Test](Gateway/Test.md)

## Constants
FROM_DOLLAR_TO_CENT_RATE =100.0

### Constants inherited from
* [PaymentMethod](PaymentMethod.md)

## Methods inherited from
* [PaymentMethod](PaymentMethod.md)

## Dynamic Method Handling
This class handles dynamic methods through the `method_missing` method

### (Object) **method_missing**(method, *args)


## Class Methods
### (Object) **current**
instantiates the selected gateway and configures with the options stored in the database 

## Instance Methods
### (Object) **disable_customer_profile**(source)


### (Object) **exchange_multiplier**


### (Object) **method_type**


### (Object) **options**


###  (Boolean) **payment_profiles_supported?**


### (Object) **payment_source_class**


### (Object) **provider**


### (Object) **reusable_sources**(order)

  
### (Object) **sources_by_order**(order)


###  (Boolean) **supports?**(source)

