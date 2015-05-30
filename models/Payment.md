## Payment Model
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
| State        | Description                                                | Callable with        |
|--------------|------------------------------------------------------------|----------------------|
| `checkout`   | still in checkout                                          |                      |
| `processing` | Temporary state to prevent double submission               | `started_processing` |
| `pending`    | Processed but incomplete (eg. authorized but not captured) | `pend`               |
| `failed`     | Payment rejected (e.g. card was declined)                  | `failure`            |
| `void`       | These payments do NOT count against order total            | `void`               |
| `completed`  | These payments count against order total                   | `complete`           |
