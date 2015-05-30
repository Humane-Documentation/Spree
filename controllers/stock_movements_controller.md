# Stock Movements API

## Index
`admin_only`

To return a paginated list of all stock movements for a stock location pass that stock location id:
```
GET /api/stock_locations/1/stock_movements
```

### Parameters
* `page`: The page number of stock movements to display.
* `per_page`: The number of stock movements to return per page

##### Response
```
<%= headers 200 %>
<%= json(:stock_movement) do |h|
{ :stock_movements => [h],
  :count => 25,
  :pages => 5,
  :current_page => 1 }
end %>
```

## Search
`admin_only`
```
GET /api/stock_locations/1/stock_movements?q[quantity_eq]=10
```
* Search results are paginated
* Searching is provided through Ransack gem. `quantity_eq` here is called a [Predicate]
(https://github.com/ernie/ransack/wiki/Basic-Searching)

##### Response
```
<%= headers 200 %>
<%= json(:stock_movement) do |h|
 { :stock_movements => [h],
   :count => 25,
   :pages => 5,
   :current_page => 1 }
end %>
```

### Sorting results
Results can be returned in a specific order by specifying which field to sort by
```
GET /api/stock_locations/1/stock_movements?q[s]=quantity%20asc
```

## Show
`admin_only`

To view details for a stock movement pass that stock movement's id and its `stock_location_id`:
```
GET /api/stock_locations/1/stock_movements/1
```

##### Successful response
```
<%= headers 200 %>
<%= json :stock_movement %>
```

##### Not Found Response
```
<%= not_found %>
```

## Create
`admin_only`
```
POST /api/stock_locations/1/stock_movements
```
To create a new stock movement with quantity 10, action set to received, and stock_item_id 1:
```
<%= json \
  :stock_movement => {
    :quantity => "10",
    :stock_item_id => "1",
    :action => "received"
  } %>
```

##### Successful response
```
<%= headers 201 %>
<%= json(:stock_movement) %>
```

##### Failed Response
```
<%= headers 422 %>
<%= json
  :error => "Invalid resource. Please fix errors and try again.",
  :errors => {
  }
%>`

## Update
`admin_only`

To update a stock movement's details:
```
PUT /api/stock_locations/1/stock_movements/1
```
To update a stock movement's quantity:
```
<%= json \
  :stock_movement => {
    :quantity => "30",
  } %>
```

##### Successful response
```
<%= headers 201 %>
<%= json(:stock_movement) %>
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
DELETE /api/stock_locations/1/stock_movement/1
```

##### Response
```
<%= headers 204 %>`
