# Shipping Method (Model)
* Carrier services used to send the product. e.g. UPS Ground, FedEx 2Day, etc.
* Can have multiple shipping categories assigned
* An order's available shipping methods can be determined by shipping categories of items included
* Each method is only applicable to a specific `Zone` to prevent sending a package internationally
using domestic shipping method

#### Attributes
* `name`
* `display_on`
* `deleted_at`
* `tracking_url`
* `admin_name`
* `tax_category_id`
* `code`

> For more info see [Shipping Guide](../business_logic/shipping.md)
