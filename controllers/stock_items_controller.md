# Stock Items API

## Index
`admin_only`

To return a paginated list of all stock items for a stock location pass that stock location id:
```
GET /api/stock_locations/1/stock_items
```

### Parameters
* `page`: The page number of stock items to display.
* `per_page`: The number of stock items to return per page

##### Response
```
<%= headers 200 %>
<%= json(:stock_item) do |h|
{ :stock_items => [h],
  :count => 25,
  :pages => 5,
  :current_page => 1 }
end %>
```

## Search
`admin_only`
```
GET /api/stock_locations/1/stock_items?q[variant_id_eq]=10
```
* Search results are paginated
* Searching is provided through Ransack gem. `variant_id_eq` here is called a [Predicate]
(https://github.com/ernie/ransack/wiki/Basic-Searching)

##### Response
```
<%= headers 200 %>
<%= json(:stock_item) do |h|
 { :stock_items => [h],
   :count => 25,
   :pages => 5,
   :current_page => 1 }
end %>
```

### Sorting results
Results can be returned in a specific order by specifying which field to sort by
```
GET /api/stock_locations/1/stock_items?q[s]=variant_id%20asc
```

## Show
`admin_only`

To view details for a single stock item, use that stock item's id and its `stock_location_id`:
```
GET /api/stock_locations/1/stock_items/2
```

##### Successful response
```
<%= headers 200 %>
<%= json :stock_item %>
```

##### Not Found Response
```
<%= not_found %>
```

## Create
`admin_only`
```
POST /api/stock_locations/1/stock_items
```
* To create a new stock item with a count_on_hand of 10, variant_id 1 :
```
<%= json \
  :stock_item => {
    :count_on_hand => "10",
    :variant_id => "1",
    :backorderable => "true"
  } %>
```

##### Successful response
```
<%= headers 201 %>
<%= json(:stock_item) %>
```

##### Failed Response
```
<%= headers 422 %>
<%= json
  :error => "Invalid resource. Please fix errors and try again.",
  :errors => {
  }%>`

## Update
`admin_only`

* Note that using this endpoint, count_on_hand is APPENDED to its current value
* Sending a request with a negative count_on_hand will subtract the current value
* To force a value for count_on_hand, include force: true in your request to replace the current
value in the database
* To update a stock item's details:
```
PUT /api/stock_locations/1/stock_items/2
```
* To update a stock item's count_on_hand:
```
<%= json \
  :stock_item => {
    :count_on_hand => "30",
  } %>
```

Or alternatively with the force attribute:
```
<%= json \
  :stock_item => {
    :count_on_hand => "30",
    :force => true,
  } %>
```

##### Successful response
```
<%= headers 201 %>
<%= json(:stock_item) %>
```

##### Failed Response
```
<%= headers 422 %>
<%= json
  :error => "Invalid resource. Please fix errors and try again.",
  :errors => {
  }
%>`

## Delete
`admin_only`
```
DELETE /api/stock_locations/1/stock_items/2
```

##### Response
```
<%= headers 204 %>`
