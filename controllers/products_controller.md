# Products API

## Index
* List products visible to authenticated user.
```
GET /api/products
```
* Products are paginated and can be iterated through by passing `page` parameter:
```
GET /api/products?page=2
```
* Non-admins only see products which have an `available_on` date in the past

### Parameters
* show_deleted (**boolean**)
    * `true` to show deleted products
    * `false` to hide them. Default but only available to users with an admin role
* `page`: The page number of products to display
* `per_page`: The number of products to return per page

##### Response
```
<%= headers 200 %>
<%= json(:product) do |h|
{ :products => [h],
  :count => 25,
  :pages => 5,
  :current_page => 1 }
end %>
```

## Search
```
GET /api/products?q[name_cont]=Spree
```
* Search results are paginated
* Searching is provided through Ransack gem. `name_cont` here is called a [Predicate]
(https://github.com/ernie/ransack/wiki/Basic-Searching)

##### Response
```
<%= headers 200 %>
<%= json(:product) do |h|
{ :products => [h],
  :count => 25,
  :pages => 5,
  :current_page => 1 }
end %>
```

### Sorting results
* Results can be returned in a specific order by specifying the field to sort by
```
GET /api/products?q[s]=sku%20asc
```
* Results can be sorted using an associated object's field too:
```
GET /api/products?q[s]=shipping_category_name%20asc
```

## Show
* To view the details for a single product pass that product\'s permalink:
```
GET /api/products/a-product
```
Or query by the product\'s id attribute:
```
GET /api/products/1
```
* The API will attempt a permalink lookup before an ID lookup

##### Successful response
```
<%= headers 200 %>
<%= json :product %>
```

##### Not Found Response
```
<%= not_found %>
```

## New
You can learn about the potential attributes (required and non-required) for a product:
```
GET /api/products/new
```

##### Response
```
<%= headers 200 %>
<%= json \
  :attributes => [
    :id, :name, :description, :price, :available_on, :permalink,
    :count_on_hand, :meta_description, :meta_keywords, :shipping_category_id, :taxon_ids
  ],
  :required_attributes => [:name, :price, :shipping_category_id]
 %>
```

## Create
`admin_only`
```
POST /api/products
```
To create a new product \"Headphones\" with a price of $100:
```
POST /api/products?product[name]=Headphones&product[price]=100&product[shipping_category_id]=1
```

##### Successful response
```
<%= headers 201 %>
```

##### Failed Response
```
<%= headers 422 %>
<%= json \
  :error => "Invalid resource. Please fix errors and try again.",
  :errors => {
    :name => ["can't be blank"],
    :price => ["can't be blank"],
    :shipping_category_id => ["can't be blank"]
  }%>`

## Update
`admin_only`

* To update a product\'s details:
```
PUT /api/products/a-product
```
* To update a product\'s name:
```
PUT /api/products/a-product?product[name]=Headphones
```

##### Successful response
```
<%= headers 201 %>
```

##### Failed Response
```
<%= headers 422 %>
<%= json \
  :error => "Invalid resource. Please fix errors and try again.",
  :errors => {
    :name => ["can't be blank"],
    :price => ["can't be blank"],
    :shipping_category_id => ["can't be blank"]
  }%>`

## Delete
`admin_only`
```
DELETE /api/products/a-product
```
This request, like a product \"deletion\" through admin interface, will not remove the record from
the database but sets the `deleted_at` field to the current time on the product and all its variants
```
<%= headers 204 %>`
