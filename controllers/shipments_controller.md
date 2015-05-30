# Shipments API

## Mine
* Retrieve a list of current user's shipments:
```
GET /api/shipments/mine
```
* Shipments are paginated and can be iterated through by passing a `page` parameter:
```
GET /api/shipments/mine?page=2
```

### Parameters
* `page`: The page number of shipments to display.
* `per_page`: The number of shipments to return per page.

##### Response
```
<%= headers 200 %>
<%= json(:shipment) do |h|
{ count: 25,
  current_page: 1,
  pages: 5,
  shipments: [h] }
end %>
```

## Create
`admin_only`

* The following attributes are required when creating a shipment:
    * `order_id`: number of the order to create a shipment for and is part of the URL string below
    * stock_location_id: shipment will be created at the selected stock location
    * variant_id: Shipment will include the variant selected
```
POST /api/shipments?shipment[order_id]=R1234567
```
* To create a shipment with stock_location_id `1`, variant_id `10` for order `R1234567`:
```
<%= json \
  :order_id => 123456,
  :stock_location_id => 1,
  :variant_id => 10
 %>
```

##### Response
```
<%= headers 200 %>
<%= json(:shipment) %>
```

## Update
`admin_only`
```
PUT /api/shipments/H123456789?shipment[tracking]=TRK9000
```

### Parameters
* unlock: When set to `yes`, the shipment's adjustment will be recalculated
* To update order ship method inspect order/shipments/shipping_rates for available
 shipping_rate_id values and use following api call:
```
PUT /api/shipments/H123456789?shipment[selected_shipping_rate_id]=162&shipment[unlock]=yes
```

##### Response
```
<%= headers 200 %>
<%= json(:shipment) %>
```

## Ready
`admin_only`
```
PUT /api/shipments/H123456789/ready
```
And you may choose to update shipment attributes as well:
```
PUT /api/shipments/H123456789/ready?shipment[number]=1234567
```

##### Response
```
<%= headers 200 %>
<%= json(:shipment) %>
```

## Ship
`admin_only`

To mark a shipment as shipped:
```
PUT /api/shipments/H123456789/ship
```
And you may choose to update shipment attributes as well:
```
PUT /api/shipments/H123456789/ship?shipment[tracking]=1234567
```

##### Response
```
<%= headers 200 %>
<%= json(:shipment_shipped) %>
```

## Add Variant
`admin_only`
```
PUT /api/shipments/H123456789/add?variant_id=1&quantity=1
```

##### Response
```
<%= headers 200 %>
<%= json(:shipment) %>
```

## Remove Variant
`admin_only`
```
PUT /api/shipments/H123456789/remove?variant_id=1&quantity=1
```

##### Response
```
<%= headers 200 %>
<%= json(:shipment) %>`
