# Countries API

## Index
* Retrieve a list of all countries:
```
GET /api/countries
```
* Countries are paginated and can be iterated through by passing a `page` parameter:
```
GET /api/countries?page=2
```

### Parameters
* `page`: The page number of country to display.
* `per_page`: The number of countries to return per page

##### Response
```
<%= headers 200 %>
<%= json(:country) do |h|
{ :countries => [h],
  :count => 25,
  :pages => 5,
  :current_page => 1 }
end %>
```

## Search
* Search results are paginated
* To search for a particular country:
```
GET /api/countries?q[name_cont]=united
```
* Results can be returned in a specific order by specifying the field to sort by:
```
GET /api/countries?q[s]=name%20desc
```
* Searching is provided through Ransack gem. `name_cont` here is called a [Predicate]
(https://github.com/ernie/ransack/wiki/Basic-Searching)

##### Response
```
<%= headers 200 %>
<%= json(:country) do |h|
 { :countries => [h],
   :count => 25,
   :pages => 5,
   :current_page => 1 }
end %>
```

## Show
Retrieve details about a particular country:
```
text
GET /api/countries/1
```

##### Response
```
<%= headers 200 %>
<%= json(:country) %>
```
