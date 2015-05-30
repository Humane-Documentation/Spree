# States API

## Index
* To get a list of states:
```
GET /api/states
```
* States are paginated and can be iterated through by passing a `page` parameter:
```
GET /api/states?page=2
```
* As well as a `per_page` parameter to control how many results will be returned:
```
GET /api/states?per_page=100
```
* You can scope the states by country by passing along a `country_id` parameter:
```
GET /api/states?country_id=1
```

##### Response
```
<%= headers 200 %>
<%= json(:state) do |h|
{ :states => [h],
  :count => 25,
  :pages => 5,
  :current_page => 1 }
end %>
```

## Show
To find out about a single state:
```
GET /api/states/1
```

##### Response
```
<%= headers 200 %>
<%= json(:state) %>`
