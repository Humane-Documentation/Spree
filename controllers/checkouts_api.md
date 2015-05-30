# Checkouts API
An API to advance an existing order's state so sending a `PUT` request to `/api/checkouts/:number`
 will advance an order's state or, failing that, report any errors

## Checkouts Steps
### Creating An Order
```
POST /api/orders.json
```
Any time you update the order or move a checkout step you'll get a response similar as below
plus new associated objects such as addresses, payments, shipments..

##### Response
```
<%= headers 201 %>
<pre class="highlight"><code class="language-javascript">{
  "id": 4,
  "number": "R307128032",
  "item_total": "0.0",
  "total": "0.0",
  "ship_total": "0.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": 1,
  "created_at": "2014-07-06T18:52:33.724Z",
  "updated_at": "2014-07-06T18:52:33.752Z",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "spree@example.com",
  "special_instructions": null,
  "channel": "spree",
  "included_tax_total": "0.0",
  "additional_tax_total": "0.0",
  "display_included_tax_total": "$0.00",
  "display_additional_tax_total": "$0.00",
  "tax_total": "0.0",
  "currency": "USD",
  "display_item_total": "$0.00",
  "total_quantity": 0,
  "display_total": "$0.00",
  "display_ship_total": "$0.00",
  "display_tax_total": "$0.00",
  "token": "n0kZnXjRfjnhZMY5ijhiOA",
  "checkout_steps": [
    "address",
    "delivery",
    "complete"
  ],
  "permissions": {
    "can_update": true
  },
  "bill_address": null,
  "ship_address": null,
  "line_items": [],
  "payments": [],
  "shipments": [],
  "adjustments": []
}
```

### Adding line items to an order Step
Pass line item attributes:
```
<pre class="highlight"><code class="language-javascript">{
  "line_item": {
    "variant_id": 1,
    "quantity": 5
  }}
```
to this api endpoint:
```
POST /api/orders/:number/line_items.json
```
```
<%= headers 201 %>
<pre class="highlight"><code class="language-javascript">{
  "id": 3,
  "quantity": 5,
  "price": "15.99",
  "variant_id": 1,
  "single_display_amount": "$15.99",
  "display_amount": "$79.95",
  "total": "79.95",
  "variant": {
    "id": 1,
    "name": "Ruby on Rails Tote",
    "sku": "ROR-00011",
    "price": "15.99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "cost_price": "17.0",
    "slug": "ruby-on-rails-tote",
    "description": "Nihil et itaque adipisci sed ea dolorum.",
    "track_inventory": true,
    "display_price": "$15.99",
    "options_text": "",
    "in_stock": true,
    "option_values": [],
    "images": [
      {
        "id": 21,
        "position": 1,
        "attachment_content_type": "image/jpeg",
        "attachment_file_name": "ror_tote.jpeg",
        "type": "Spree::Image",
        "attachment_updated_at": "2014-07-06T18:37:34.534Z",
        "attachment_width": 360,
        "attachment_height": 360,
        "alt": null,
        "viewable_type": "Spree::Variant",
        "viewable_id": 1,
        "mini_url": "/spree/products/21/mini/ror_tote.jpeg?1404671854",
        "small_url": "/spree/products/21/small/ror_tote.jpeg?1404671854",
        "product_url": "/spree/products/21/product/ror_tote.jpeg?1404671854",
        "large_url": "/spree/products/21/large/ror_tote.jpeg?1404671854"
      },
      {
        "id": 22,
        "position": 2,
        "attachment_content_type": "image/jpeg",
        "attachment_file_name": "ror_tote_back.jpeg",
        "type": "Spree::Image",
        "attachment_updated_at": "2014-07-06T18:37:34.921Z",
        "attachment_width": 360,
        "attachment_height": 360,
        "alt": null,
        "viewable_type": "Spree::Variant",
        "viewable_id": 1,
        "mini_url": "/spree/products/22/mini/ror_tote_back.jpeg?1404671854",
        "small_url": "/spree/products/22/small/ror_tote_back.jpeg?1404671854",
        "product_url": "/spree/products/22/product/ror_tote_back.jpeg?1404671854",
        "large_url": "/spree/products/22/large/ror_tote_back.jpeg?1404671854"
      }
    ],
    "product_id": 1
  },
  "adjustments": []
}
```

### Updating an order Step (Optional)
* To update an order you must be authenticated as the order's user:
```
PUT /api/orders/:number.json
```
* An order can also be updated using its token:
```
PUT /api/orders/:number.json?order_token=abcdef123456
```
* Requests from a non-admin or non-authorized user will get a 401

### Next Step
* To transition to a next step:
```
PUT /api/checkouts/:number/next.json
```
* Successful requests get a 200 response similar to order creation, with the state updated

##### Failed Response
```
<%= headers 422 %>
<%= json(:order_failed_transition) %>
```

### Delivery Step
* To advance to `delivery` an order needs both a shipping and billing address. To update addresses:
```
PUT /api/checkouts/:number.json
```
* This is an example of required address attributes and the format:
```
<%= json \
  :order => {
    :bill_address_attributes => {
      :firstname  => 'John',
      :lastname   => 'Doe',
      :address1   => '7735 Old Georgetown Road',
      :city       => 'Bethesda',
      :phone      => '3014445002',
      :zipcode    => '20814',
      :state_id   => 48,
      :country_id => 49
    },
    :ship_address_attributes => {
      :firstname  => 'John',
      :lastname   => 'Doe',
      :address1   => '7735 Old Georgetown Road',
      :city       => 'Bethesda',
      :phone      => '3014445002',
      :zipcode    => '20814',
      :state_id   => 48,
      :country_id => 49
    }}%>
```

##### Response
Shipments and shipping rates available will be returned inside a `shipments` key inside the order:
```
<%= headers 200 %>
<pre class="highlight"><code class="language-javascript">{
  ...
  "shipments": [
    {
      "id": 4,
      "tracking": null,
      "number": "H22035832422",
      "cost": "15.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R181010551",
      "stock_location_name": "default",
      "shipping_rates": [
        {
          "id": 10,
          "name": "UPS Ground (USD)",
          "cost": "5.0",
          "selected": false,
          "shipping_method_id": 1,
          "display_cost": "$5.00"
        },{
          "id": 11,
          "name": "UPS Two Day (USD)",
          "cost": "10.0",
          "selected": false,
          "shipping_method_id": 2,
          "display_cost": "$10.00"
        },{
          "id": 12,
          "name": "UPS One Day (USD)",
          "cost": "15.0",
          "selected": true,
          "shipping_method_id": 3,
          "display_cost": "$15.00"
        }],
      "selected_shipping_rate": {
        "id": 12,
        "name": "UPS One Day (USD)",
        "cost": "15.0",
        "selected": true,
        "shipping_method_id": 3,
        "display_cost": "$15.00"
      },
      "shipping_methods": [
        {
          "id": 1,
          "name": "UPS Ground (USD)",
          "zones": [
            {
              "id": 2,
              "name": "North America",
              "description": "USA + Canada"
            }],
          "shipping_categories": [
            {
              "id": 1,
              "name": "Default"
            }]},{
          "id": 2,
          "name": "UPS Two Day (USD)",
          "zones": [
            {
              "id": 2,
              "name": "North America",
              "description": "USA + Canada"
            }],
          "shipping_categories": [
            {
              "id": 1,
              "name": "Default"
            }]},{
          "id": 3,
          "name": "UPS One Day (USD)",
          "zones": [
            {
              "id": 2,
              "name": "North America",
              "description": "USA + Canada"
            }],
          "shipping_categories": [
            {
              "id": 1,
              "name": "Default"
            }]}],
      "manifest": [
        {
          "quantity": 3,
          "states": {
            "on_hand": 3
          },
          "variant_id": 1
        }]}],
  ...
```

### Payment Step
* To advance User needs to select a shipping rate for each shipment for the order returned from
`delivery` step. Retrievable with:
```
GET /api/orders/:number.json
```
* First shipping rate is selected by default so to advance to `payment` state:
```
PUT /api/checkouts/:number/next.json
```
* To both select a shipping rate and advance the order's state to `payment`:
```
PUT /api/checkouts/:number.json
```
With parameters such as these:
```
<%= json (
  {
    order: {
      shipments_attributes: {
        "0" => {
          selected_shipping_rate_id: 1,
          id: 1
        }
      }
    }
  }) %>
```
* Ensure you select a shipping rate for each shipment in the order. `id` above is of the single
shipment you are choosing a shipping rate for

### Confirm Step
* To advance to `confirm` an order needs to have a payment created by passing parameters such as:
```
<%= json \
  :order => {
    :payments_attributes => [{
      :payment_method_id => "1"
    }]},
  :payment_source => {
    "1" => {
      "number" => "4111111111111111",
      "month" => "1",
      "year" => "2017",
      "verification_value" => "123",
      "name" => "John Smith"
    }}
%>
```
* Numbered key in `payment_source` hash corresponds to `payment_method_id` in `payment_attributes`
* You can use an existing card for an order by submitting the credit card id:
```
<%= json \
  :order => {
    :existing_card => "1"
  }%>
```
* For 2-2-stable checkout api the request to submit a payment via api/checkouts is different:
```
<%= json \
  :order => {
    :payments_attributes => {
      :payment_method_id => "1"
    },
    :payment_source => {
      "1" => {
        "number" => "4111111111111111",
        "month" => "1",
        "year" => "2017",
        "verification_value" => "123",
        "name" => "John Smith"
      }}}%>
```
* If an order already has a payment you can directly advance it to `confirm`:
```
PUT /api/checkouts/:number.json
```

##### Response
```
<%= headers 200 %>
<pre class="highlight"><code class="language-javascript">{
  ...
  "state": "confirm",
  ...
  "payments": [
    {
      "id": 3,
      "source_type": "Spree::CreditCard",
      "source_id": 2,
      "amount": "65.37",
      "display_amount": "$65.37",
      "payment_method_id": 1,
      "response_code": null,
      "state": "checkout",
      "avs_response": null,
      "created_at": "2014-07-06T19:55:08.308Z",
      "updated_at": "2014-07-06T19:55:08.308Z",
      "payment_method": {
        "id": 1,
        "name": "Credit Card"
      },
      "source": {
        "id": 2,
        "month": "1",
        "year": "2017",
        "cc_type": null,
        "last_digits": "1111",
        "name": "John Smith"
      }}],
  ...
```

### Complete Step
To advanced to the final state `complete`:
```
PUT /api/checkouts/:number.json
```
You should get a 200 response with all the order info
