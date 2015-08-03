[Index](../_index.md) » Payment

# (Class) [Spree::Payment](http://m.gymplayer.com/payment.rb)  
`Payment` tracks payments against `Order`s to decouple logic of processing payments from orders

### Attributes
* `amount`
* `order_id`
* `source_id`: Payment `source` indicates how the payment was made
* `source_type`
* `payment_method_id`
* `state` see below
* `response_code`
* `avs_response`
* `number`: 8-character id given to a payment when created to prevent gateways from duplication
* `cvv_response_code`
* `cvv_response_message`

### States
![](payment_states.png)

| State        | Description                                                | Callable with        |
|--------------|------------------------------------------------------------|----------------------|
| `checkout`   | still in checkout                                          |                      |
| `processing` | Temporary state to prevent double submission               | `started_processing` |
| `pending`    | Processed but incomplete (eg. authorized but not captured) | `pend`               |
| `failed`     | Payment rejected (e.g. card was declined)                  | `failure`            |
| `void`       | These payments do NOT count against order total            | `void`               |
| `completed`  | These payments count against order total                   | `complete`           |

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
