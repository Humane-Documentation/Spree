## Shipping Category (Model)
* If shipping cost for all products is the same, all products are assigned one shipping category
* Useful when shipping costs vary depending on product(s) selected so they cannot be 
shipped in the same box. e.g. "Default", "Over-sized"..
* During checkout, shipping categories of products determine which calculator will
be used to price each Shipping Method
* Can be created in the admin interface ("Configuration" -> "Shipping Categories") and then
assigned to products ("Products" -> "Edit")

### Attributes
* `name`

> For more info see [Shipping Guide](../business_logic/shipping.md)
