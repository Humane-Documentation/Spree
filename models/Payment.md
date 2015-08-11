[Index](../_index.md) » Payment

# (Class) [Spree::Payment](http://m.gymplayer.com/payment.rb)  
`Payment` tracks payments against `Order`s to decouple logic of processing payments from orders

### Attributes
* `amount`
* `order_id`
* `source_type`: Payment type used. e.g. `Spree::CreditCard` in case of a Gateway payment or nil in case the payment method doesn't require a source e.g. check
* `source_id`: Identifier within the `source_type` used. e.g. credit_card_id, gift_card_id
* `payment_method_id`
* `state` see [Payments Guide](../business_logic/payments_guide.md)
* `response_code`
* `avs_response`
* `number`: 8-character id given to a payment when created to prevent gateways from duplication
* `cvv_response_code`
* `cvv_response_message`

## Modules
* [Processing](Payment/Processing.md)

## Classes 
* [GatewayOptions](Payment/GatewayOptions.md)

## Constant
NON_RISKY_AVS_CODES =['B', 'D', 'H', 'J', 'M', 'Q', 'T', 'V', 'X', 'Y'].freeze

RISKY_AVS_CODES =['A', 'C', 'E', 'F', 'G', 'I', 'K', 'L', 'N', 'O', 'P', 'R', 'S', 'U', 'W', 'Z'].freeze

## Methods included from
* [Processing](Payment/Processing.md)

### Methods inherited from
* [Base](Base.md)

### Methods included from
* [Spree::Preferences::Preferable](Preferences/Preferable.md)

## Instance Attributes
### (Object) **request_env**
Returns the value of attribute request_env

### (Object) **source_attributes**
Returns the value of attribute source_attributes

## Instance Methods
### (Object) **actions**
    
    
### (Object) **amount=**(amount)
        

### (Object) **build_source**
see [github.com/spree/spree/issues/981](https://github.com/spree/spree/issues/981)
    
###  (Boolean) **can_credit?**


### (Object) **captured_amount**


### (Object) **credit_allowed**


### (Object) **currency**


###  (Boolean) **editable?**


###  (Boolean) **is_avs_risky?**
   

###  (Boolean) **is_cvv_risky?**
 

### (Object) **money** Also known as: display_amount


### (Object) **offsets_total**


### (Object) **payment_source**


### (Object) **transaction_id**
transaction_id is much easier to understand

### (Object) **uncaptured_amount**
