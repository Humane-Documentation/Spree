# Product Properties API

> Warning: Requests to this API succeed only if the user has access to the underlying products. If
the user isn't an admin and the product isn't available yet then they'll get a 404

## Index
* To retrieve a list of all product properties for a product:
```
GET /api/products/1/product_properties
```
* Product properties are paginated and can be iterated through by passing along a `page` parameter:
```
GET /api/products/1/product_properties?page=2
```

### Parameters
* `page`: The page number of product property to display.
* `per_page`: The number of product properties to return per page

##### Response
```
<%= headers 200 %>
<%= json(:product_property) do |h|
{ :product_properties => [h],
  :count => 10,
  :pages => 2,
  :current_page => 1 }
end %>
```

## Search
```
GET /api/products/1/product_properties?q[property_name_cont]=bag
```
* Search results are paginated
* Searching is provided through Ransack gem. `property_name_cont` here is called a [Predicate]
(https://github.com/ernie/ransack/wiki/Basic-Searching)

##### Response
```
<%= headers 200 %>
<%= json(:product_property) do |h|
 { :product_properties => [h],
   :count => 10,
   :pages => 2,
   :current_page => 1 }
end %>
```

### Sorting results
Results can be returned in a specific order by specifying the field to sort by
```
GET /api/products/1/product_properties?q[s]=property_name%20desc
```

## Show

To get information about a single product property:
```
GET /api/products/1/product_properties/1
```
Or you can use the property's name:
```
GET /api/products/1/product_properties/size
```

##### Response
```
<%= headers 200 %>
<%= json(:product_property) %>
```

## Create
`admin_only`
```
POST /api/products/1/product_properties?product_property[property_name]=size&product_property[value]=10
```
If a property with that name does not already exist, then it will be created

##### Response
```
<%= headers 201 %>
<%= json(:product_property) %>
```

## Update
```
PUT /api/products/1/product_properties/size?product_property[value]=10
```
Or you can use the property's id:
```
PUT /api/products/1/product_properties/1?product_property[value]=10
```

##### Response
```
<%= headers 200 %>
<%= json(:product_property) %>
```

## Delete
```
DELETE /api/products/1/product_properties/size
``````
<%= headers 204 %>`
