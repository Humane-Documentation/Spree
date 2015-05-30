# Zones API

## Index
To get a list of zones:
```
GET /api/zones
```
Zones are paginated and can be iterated through by passing a `page` parameter:
```
GET /api/zones?page=2
```

### Parameters
* `page`: The page number of zone to display.
* `per_page`: The number of zones to return per page

##### Response
```
<%= headers 200 %>
<%= json(:zone) do |h|
{ :zones => [h],
  :count => 25,
  :pages => 5,
  :current_page => 1 }
end %>
```

## Search
```
GET /api/zones?q[name_cont]=north
```
* Search results are paginated
* Searching is provided through Ransack gem. `name_cont` here is called a [Predicate]
(https://github.com/ernie/ransack/wiki/Basic-Searching)

##### Response
```
<%= headers 200 %>
<%= json(:zone) do |h|
 { :zones => [h],
   :count => 25,
   :pages => 5,
   :current_page => 1 }
end %>
```

### Sorting results
Results can be returned in a specific order by specifying the field to sort by
```
GET /api/zones?q[s]=name%20desc
```

## Show
To get information for a single zone:
```
GET /api/zones/1
```

##### Response
```
<%= headers 200 %>
<%= json(:zone) %>
```

## Create
`admin_only`
```
POST /api/zones
```
Assuming you want to create a zone containing a zone member which is a `Spree::Country` record
with the `id` 1:
```
<%= json \
  :zone => {
    :name => "North Pole",
    :zone_members => [
      {
        :zoneable_type => "Spree::Country",
        :zoneable_id => 1
      }]} %>
```

##### Response
```
<%= headers 201 %>
<%= json(:zone) %>
```

## Update
`admin_only`

To update a zone:
```
PUT /api/zones/1
```
To update zone and zone member information:
```
<%= json \
  :id => 1,
  :zone => {
    :name => "North Pole",
    :zone_members => [
      {
        :zoneable_type => "Spree::Country",
        :zoneable_id => 1
      }]} %>
```

##### Response
```
<%= headers 200 %>
<%= json(:zone) %>
```

## Delete
`admin_only`
```
DELETE /api/zones/1
```
This request will also delete any related `zone_member` records

##### Response
```
<%= headers 204 %>`
