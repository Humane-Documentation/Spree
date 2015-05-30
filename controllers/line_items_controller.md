# Line Items API

## Create
```
POST /api/orders/R1234567/line_items?line_item[variant_id]=1&line_item[quantity]=1
```
This creates a new line item representing a single item for variant with id 1.

##### Response
```
<%= headers 201 %>
<%= json(:line_item) %>
```

## Update
```
PUT /api/orders/R1234567/line_items/1?line_item[variant_id]=1&line_item[quantity]=1
```
This updates line item with ID 1 for the order, updating the line item's `variant_id`
to 1, and its `quantity` to 1

##### Response
```
<%= headers 200 %>
<%= json(:line_item) %>
```

## Delete
```
DELETE /api/orders/R1234567/line_items/1
```

##### Response
```
<%= headers 204 %>
```
