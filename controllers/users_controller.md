# Users API

List users visible to the authenticated user. Non-admins will only see their own user,
unless they have custom permissions to see other users. Admins can see all users
```
GET /api/users
```
Users are paginated and can be iterated through by passing along a `page` parameter:
```
GET /api/users?page=2
```

##### Response
```
<%= headers 200 %>
<%= json(:user) do |h|
    { :users => [h], :count => 25, :pages => 5, :current_page => 1 }
end %>
```

## A single user

To view the details for a single user, make a request using that user\'s id:
```
GET /api/users/1
```

##### Successful response
```
<%= headers 200 %> <%= json :user %>
```

##### Not Found Response
```
<%= not_found %>
```

## Pre-creation of a user

Learn about potential attributes (required and non-required) for a user:
```
text GET /api/users/new
```

##### Response
```
<%= headers 200 %>
<%= json :attributes => ["<attribute1>", "<attribute2>"], :required_attributes => [] %>
```

## Creating a new new
`admin_only`

To create a new user through the API, pass necessary parameters:
```
POST /api/users
```
To create new user with email \"spree@example.com\" and password \"password\":
```
POST /api/users?user[email]=spree@example.com&user[password]=password
```

##### Successful response
```
<%= headers 201 %>
```

##### Failed Response
```
<%= headers 422 %>
<%= json :error => "Invalid resource. Please fix errors and try again.",
         :errors => { :email => ["can't be blank"] } %>
```

## Updating a user
`admin_only`

To update a user\'s details, pass necessary parameters:
```
PUT /api/users/1
```
For instance, to update a user\'s password:
```
text PUT /api/users/1?user[password]=password
```

##### Successful response
```
<%= headers 201 %>
```

##### Failed Response
```
<%= headers 422 %>
<%= json :error => "Invalid resource. Please fix errors and try again.",
         :errors => { :email => ["can't be blank"] } %>
```

## Deleting a user
`admin_only`
```
DELETE /api/users/1
```

##### Response
```
<%= headers 204 %>`
