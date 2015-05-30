# Return Authorizations API
`admin_only`

## Index
To list all return authorizations for an order:
```
GET /api/orders/R1234567/return_authorizations
```
Return authorizations are paginated and can be iterated through by passing a `page` parameter:
```
GET /api/orders/R1234567/return_authorizations?page=2
```

### Parameters
* `page`: The page number of return authorization to display.
* `per_page`: The number of return authorizations to return per page

##### Response
```
<%= headers 200 %>
<%= json(:return_authorization) do |h|
{ :return_authorizations => [h],
  :count => 2,
  :pages => 1,
  :current_page => 1 }
end %>
```

## Search
```
GET /api/orders/R1234567/return_authorizations?q[reason_cont]=damage
```
* Search results are paginated
* Searching is provided through Ransack gem. `reason_cont` here is called a [Predicate]
(https://github.com/ernie/ransack/wiki/Basic-Searching)

### Sorting results
Results can be returned in a specific order by specifying which field to sort by
```
GET /api/orders/R1234567/return_authorizations?q[s]=amount%20asc
```

##### Response
```
<%= headers 200 %>
<%= json(:return_authorization) do |h|
 { :return_authorizations => [h],
   :count => 1,
   :pages => 1,
   :current_page => 1 }
end %>
```

## Show
To get information for a single return authorization:
```
GET /api/orders/R1234567/return_authorizations/1
```

##### Response
```
<%= headers 200 %>
<%= json(:return_authorization) %>
```

## Create
`admin_only`
```
POST /api/orders/R1234567/return_authorizations
```
To create a return authorization with a number:
```
POST /api/orders/R1234567/return_authorizations?return_authorization[number]=123456
```

##### Response
```
<%= headers 201 %>
<%= json(:return_authorization) %>
```

## Update
`admin_only`

* To update a return authorization:
```
PUT /api/orders/R1234567/return_authorizations/1
```
* To update a return authorization's number:
```
PUT /api/orders/R1234567/return_authorizations/1?return_authorization[number]=123456
```

##### Response
```
<%= headers 200 %>
<%= json(:return_authorization) %>
```

## Delete
`admin_only`
```
DELETE /api/orders/R1234567/return_authorizations/1
```

##### Response
```
<%= headers 204 %>`
