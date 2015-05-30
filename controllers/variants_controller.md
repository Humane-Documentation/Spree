# Variants API

## Index
To return a paginated list of all variants within the store:
```
GET /api/variants
```
You can limit this to variants of a particular product by passing the product's permalink:
```
GET /api/products/ruby-on-rails-tote/variants
```
or
```
GET /api/variants?product_id=ruby-on-rails-tote
```

### Parameters
* show_deleted: (**boolean**)
    * `true` to show deleted variants
    * `false` to hide them. Default but only available to users with an admin role
* `page`: The page number of variants to display.
* `per_page`: The number of variants to return per page

##### Response
```
<%= headers 200 %>
<%= json(:variant) do |h|
{ :variants => [h],
  :count => 25,
  :pages => 5,
  :current_page => 1 }
end %>
```

## Search
```
GET /api/variants?q[sku_cont]=foo
```
You can limit this to showing variants for a particular product by passing a product id:
```
GET /api/products/ruby-on-rails-tote/variants?q[sku_cont]=foo
```
Or:
```
GET /api/variants?product_id=ruby-on-rails-tote&q[sku_cont]=foo
```
* Search results are paginated
* Searching is provided through Ransack gem. `sku_cont` here is called a [Predicate]
(https://github.com/ernie/ransack/wiki/Basic-Searching)

##### Response
```
<%= headers 200 %>
<%= json(:variant) do |h|
 { :variants => [h],
   :count => 25,
   :pages => 5,
   :current_page => 1 }
end %>
```

### Sorting results
Results can be returned in a specific order by specifying which field to sort by:
```
GET /api/variants?q[s]=price%20asc
```
It is also possible to sort results using an associated object's field:
```
GET /api/variants?q[s]=product_name%20asc
```

## Show
To view details of a single variant, use its id and the product's permalink as its `product_id`:
```
GET /api/products/ruby-on-rails-tote/variants/1
```
Or:
```
GET /api/variants/1?product_id=ruby-on-rails-tote
```

##### Successful response
```
<%= headers 200 %>
<%= json :variant %>
```

##### Not Found Response
```
<%= not_found %>
```

## New

You can learn the potential attributes (required and non-required) for a variant with this request:
```
GET /api/products/ruby-on-rails-tote/variants/new
```

##### Response
```
<%= headers 200 %>
<%= json \
  :attributes => [
    :id, :name, :count_on_hand, :sku, :price, :weight, :height,
    :width, :depth, :is_master, :cost_price, :permalink
  ],
  :required_attributes => []
 %>
```

## Create
`admin_only`
```
POST /api/products/ruby-on-rails-tote/variants
```
To create a new variant with SKU 12345 and a price of 19.99:
```
POST /api/products/ruby-on-rails-tote/variants/?variant[sku]=12345&variant[price]=19.99
```

##### Successful response
```
<%= headers 201 %>
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

To update a variant\'s details pass necessary parameters:
```
PUT /api/products/ruby-on-rails-tote/variants/2
```
For instance, to update a variant\'s SKU:
```
PUT /api/products/ruby-on-rails-tote/variants/2?variant[sku]=12345
```

##### Successful response
```
<%= headers 201 %>
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
DELETE /api/products/ruby-on-rails-tote/variants/2
```
Like a variant \"deletion\" through the admin interface, this will not remove the record from the
 database but simply sets `deleted_at` field to the current time on the variant
```
<%= headers 204 %>`
