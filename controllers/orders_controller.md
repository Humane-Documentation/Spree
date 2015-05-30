# Orders API

## Index
```
<%= admin_only %>
```
* To retrieve a list of orders:
```
GET /api/orders
```
* Orders are paginated and can be iterated through by passing along a `page` parameter:
```
GET /api/orders?page=2
```

##### Parameters
* `page`: The page number of order to display
* `per_page`: The number of orders to return per page

##### Response
```
<%= headers 200 %>
<%= json(:order) do |h|
{ :orders => [h],
  :count => 25,
  :pages => 5,
  :current_page => 1 }
end %>
```

## Search
```
GET /api/orders?q[email_cont]=bob
```
* Search results are paginated
* Searching is provided through Ransack gem. `email_cont` here is called a [Predicate]
(https://github.com/ernie/ransack/wiki/Basic-Searching)

##### Response
```
<%= headers 200 %>
<%= json(:order) do |h|
 { :orders => [h],
   :count => 25,
   :pages => 5,
   :current_page => 1 }
end %>
```

### Sorting results
* Results can be returned in a specific order by specifying the field to sort by
```
GET /api/orders?q[s]=number%20desc
```
* It is also possible to sort results using an associated object's field
```
GET /api/orders?q[s]=user_name%20asc
```

## Show
* To view the details for a single product use the order\'s number:
```
GET /api/orders/R123456789
```
* Orders will only be accessible to admins and users who own them. If a user attempts to access an
order that does not belong to them they'll see an authorization error
* Users may pass in the order's token to be authorized to view an order or perform any other action:
```
GET /api/orders/R123456789?order_token=abcdef123456
```

##### Successful Response
```
<%= headers 200 %>
<%= json :order_show %>
```

##### Not Found Response
```
<%= not_found %>
```

##### Authorization Failure
```
<%= authorization_failure %>
```

## Show (delivery)
When an order is in "delivery" state additional shipments info will be returned:
```
<%= json(:shipment) do |h|
 { :shipments => [h] }
end %>
```

## Create
```
POST /api/orders
```
If you wish to create an order with a line item matching a variant with ID \"1\" and quantity 5:
```
POST /api/orders
{
  "order": {
    "line_items": [
      { "variant_id": 1, "quantity": 5 }
    ]}}
```

##### Successful response
```
<%= headers 201 %>
```

##### Failed response
```
<%= headers 422 %>
<%= json \
  :error => "Invalid resource. Please fix errors and try again.",
  :errors => {
    :name => ["can't be blank"],
    :price => ["can't be blank"]
  }
%>
```

## Update Address
To add address info to an order see checkouts#checkout-transitions

## Empty
To empty an order\'s cart:
```
PUT /api/orders/R1234567/empty
```
All line items will be removed from the cart and order\'s info will be cleared. Inventory that
was previously depleted by this order will be repleted
