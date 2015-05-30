# Payments API

## Index
* To see details about an order's payments:
```
GET /api/orders/R1234567/payments
```
* Payments are paginated and can be iterated through by passing a `page` parameter:
```
GET /api/orders/R1234567/payments?page=2
```

### Parameters
* `page`: The page number of payment to display.
* `per_page`: The number of payments to return per page

##### Response
```
<%= headers 200 %>
<%= json(:payment) do |h|
{ :payments => [h],
  :count => 2,
  :pages => 2,
  :current_page => 1 }
end %>
```

## Search
```
GET /api/orders/R1234567/payments?q[response_code_cont]=123
```
* Search results are paginated
* Searching is provided through Ransack gem. `response_code_cont` here is called a [Predicate]
(https://github.com/ernie/ransack/wiki/Basic-Searching)

##### Response
```
<%= headers 200 %>
<%= json(:payment) do |h|
{ :payments => [h],
  :count => 2,
  :pages => 2,
  :current_page => 1 }
end %>
```

### Sorting results
* Results can be returned in a specific order by specifying the field to sort by
```
GET /api/payments?q[s]=state%20desc
```
* It is also possible to sort results using an associated object's field
```
GET /api/payments?q[s]=order_number%20asc
```

## New
To create a new payment you need to know available payment methods and attributes. To find them out:
```
GET /api/orders/R1234567/payments/new
```

##### Response
```
<%= headers 200 %>
<%= json \
  :attributes =>
  ["id", "source_type", "source_id", "amount",
   "payment_method_id", "response_code", "state",
   "avs_response", "created_at", "updated_at"],
  :payment_methods => [Spree::Resources::PAYMENT_METHOD] %>
```
## Create
```
POST /api/orders/R1234567/payments?payment[payment_method_id]=1&payment[amount]=10
```

##### Response
```
<%= headers 201 %>
<%= json(:payment) %>
```

## Show
To get information for a particular payment:
```
GET /api/orders/R1234567/payments/1
```

##### Response
```
<%= headers 200 %>
<%= json(:payment) %>
```

## Authorize
To authorize a payment:
```
PUT /api/orders/R1234567/payments/1/authorize
```

##### Response
```
<%= headers 200 %>
<%= json :payment %>
```

##### Failed Response
```
<%= headers 422 %>
<%= json :error => "There was a problem with the payment gateway: [text]" %>
```

## Capture
```
PUT /api/orders/R1234567/payments/1/capture
```
> warning "Capturing a payment is typically done shortly after authorizing the payment. If you
  are auto-capturing payments, you may be able to use the purchase endpoint instead."

##### Response
```
<%= headers 200 %>
<%= json :payment %>
```

##### Failed Response
```
<%= headers 422 %>
<%= json :error => "There was a problem with the payment gateway: [text]" %>
```

## Purchase
To make a purchase with a payment:
```
PUT /api/orders/R1234567/payments/1/purchase
```
> warning "Purchasing a payment is typically done only if you are not authorizing payments
 before-hand. If you are authorizing payments, then use the authorize and capture endpoints instead."


##### Response
```
<%= headers 200 %>
<%= json :payment %>
```

##### Failed Response
```
<%= headers 422 %>
<%= json :error => "There was a problem with the payment gateway: [text]" %>
```

## Void
To void a payment:
```
PUT /api/orders/R1234567/payments/1/void
```

##### Response
```
<%= headers 200 %>
<%= json :payment %>
```

##### Failed Response
```
<%= headers 422 %>
<%= json :error => "There was a problem with the payment gateway: [text]" %>
```

## Credit
To credit a payment:
```
PUT /api/orders/R1234567/payments/1/credit?amount=10
```

##### Response
```
<%= headers 200 %>
<%= json :payment %>
```

##### Failed Response
```
<%= headers 422 %>
<%= json :error => "There was a problem with the payment gateway: [text]" %>
```

##### Credit Over Limit Response
If the payment is over its credit allowed limit:
```
<%= headers 422 %>
<%= json :error => "This payment can only be credited up to [amount]. Please specify an amount
 less than or equal to this number." %>
 ```
