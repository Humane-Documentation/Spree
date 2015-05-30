# Taxonomies API

## Index
Get a list of all taxonomies, including root nodes and immediate children for the root node:
```
GET /api/taxonomies
```

### Parameters
* `page`: The page number of taxonomy to display.
* `per_page`: The number of taxonomies to return per page

##### Response
```
<%= headers 200 %>
<%= json(:taxonomy) do |h|
{ :taxonomies => [h],
  :count => 25,
  :pages => 5,
  :current_page => 1 }
end %>
```

## Search
```
GET /api/taxonomies?q[name_cont]=brand
```
* Search results are paginated
* Searching is provided through Ransack gem. `name_cont` here is called a [Predicate]
(https://github.com/ernie/ransack/wiki/Basic-Searching)

##### Response
```
<%= headers 200 %>
<%= json(:taxonomy) do |h|
 { :taxonomies => [h],
   :count => 5,
   :pages => 2,
   :current_page => 1 }
end %>
```

### Sorting results
Results can be returned in a specific order by specifying which field to sort by
```
GET /api/taxonomies?q[s]=name%20asc
```
It is also possible to sort results using an associated object's field.
```
GET /api/taxonomies?q[s]=root_name%20desc
```

## Show
To get info for a single taxonomy, including its root node and immediate children of root node:
```
GET /api/taxonomies/1
```

##### Response
```
<%= headers 200 %>
<%= json(:taxonomy) %>
```

## Create
`admin_only`
```
POST /api/taxonomies
```
For instance, if you want to create a taxonomy with the name \"Brands\":
```
POST /api/taxonomies?taxonomy[name]=Brand
```
If you\'re creating a taxonomy without a root taxon, a root taxon will automatically be
created for you with the same name as the taxon

##### Response
```
<%= headers 201 %>
<%= json(:new_taxonomy) %>
```

## Update
`admin_only`
```
PUT /api/taxonomies/1
```
For instance, to update a taxonomy\'s name:
```
PUT /api/taxonomies/1?taxonomy[name]=Brand
```

##### Response
```
<%= headers 200 %>
<%= json(:taxonomy) %>
```

## Delete
`admin_only`
```
DELETE /api/taxonomies/1
```

##### Response
```
<%= headers 204 %>
```

## List taxons
List taxons underneath the root taxon for a taxonomy (and their immediate children) for a taxonomy:
```
GET /api/taxonomies/1/taxons
```

##### Response
```
<%= headers 200 %>
<%= json(:taxon_with_children) { |h| [h] } %>
```

## A single taxon

To see information about a taxon and its immediate children:
```
GET /api/taxonomies/1/taxons/1
```

##### Response
```
<%= headers 200 %>
<%= json(:taxon_with_children) %>
```


## Taxon Create
`admin_only`
```
POST /api/taxonomies/1/taxons
```
To create a new taxon with the name "Brands":
```
POST /api/taxonomies/1/taxons?taxon[name]=Brands
```

##### Response
```
<%= headers 201 %>
<%= json(:taxon_without_children) %>
```


## Taxon Update
`admin_only`
```
PUT /api/taxonomies/1/taxons/1
```
For example, to update the taxon's name to "Brand":
```
PUT /api/taxonomies/1/taxons/1?taxon[name]=Brand
```

##### Response
```
<%= headers 200 %>
<%= json(:taxon_with_children) %>
```

## Taxon Delete
`admin_only`

    DELETE /api/taxonomies/1/taxons/1
```
<%= warning "This will cause all child taxons to be deleted as well." %>
```

##### Response
```
<%= headers 204 %>`
