# Stock Locations API

## Index
`admin_only`
```
GET /api/stock_locations
```
Stock locations are paginated and can be iterated through by passing `page` parameter:
```
GET /api/stock_locations?page=2
```

### Parameters
* `page`: The page number of stock location to display.
* `per_page`: The number of stock locations to return per page

##### Response
```
<%= headers 200 %>
<%= json(:stock_location) do |h|
{ :stock_locations => [h],
  :count => 5,
  :pages => 1,
  :current_page => 1 }
end %>
```

## Search
`admin_only`
```
GET /api/stock_locations?q[name_cont]=default
```
* Search results are paginated
* Searching is provided through Ransack gem. `name_cont` here is called a [Predicate]
(https://github.com/ernie/ransack/wiki/Basic-Searching)

##### Response
```
<%= headers 200 %>
<%= json(:stock_location) do |h|
{ :stock_locations => [h],
  :count => 5,
  :pages => 1,
  :current_page => 1 }
end %>
```

## Show
`admin_only`

To get information for a single stock location:
```
GET /api/stock_locations/1
```

##### Response
```
<%= headers 200 %>
<%= json(:stock_location) %>
```

## Create
`admin_only`
```
POST /api/stock_locations
```
Assuming in this instance that you want to create a stock location with a name of `East Coast`:
```
<%= json \
  :stock_location => {
    :name => "East Coast",
    :action => "true"
  } %>
```

##### Response
```
<%= headers 201 %>
<%= json(:stock_location) %>
```

## Update
`admin_only`

* To update a stock location:
```
PUT /api/stock_locations/1
```
* To update stock location information:
```
<%= json \
  :stock_location => {
    :name => "North Pole",
    :action => "false"
  } %>
```

##### Response
```
<%= headers 200 %>
<%= json(:stock_location) %>
```

## Delete
`admin_only`
```
DELETE /api/stock_locations/1
```
This deletes any related `stock item` records

##### Response
```
<%= headers 204 %>`
