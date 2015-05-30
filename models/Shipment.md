## Shipment (Model)
* `Shipment` object is created during checkout to track shipping method the order it applies to

### Attributes
* `tracking`: identifier for shipping provider (i.e. FedEx, UPS, etc)
* `number`: unique identifier, begins with "H" and ends in an 11-digit number. Can be used to find
the order by calling `Shipment.find_by(number: number)`.=
* `cost`
* `shipped_at`
* `order_id`
* `address_id`
* `state`
* `stock_location_id`: ID of Stock Location where shipment will be sourced from
* `adjustment_total`
* `additional_tax_total`
* `promo_total`
* `included_tax_total`
* `pre_tax_amount`

### States
* `pending`: shipment has backordered inventory units and or order isn't paid
* `ready`: shipment has no backordered inventory units and order is paid
* `shipped`
* `canceled`: All order shipments are cancelled and products will be restocked. Shipment resumes
only if order is "resumed"

> For more info see [Shipping Guide](../business_logic/shipping.md)
