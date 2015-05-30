## Stock Location (Model)
* Any location from where inventory is shipped
* Each `StockLocation` has many `stock_items` and `stock_movements`
* Created in the admin interface via (Configuration ? Stock Locations)
* A `StockItem` is added to newly created `StockLocation` for every variant in an application

#### Attributes
* `name`
* `default`
* `address1`
* `address2`
* `city`
* `state_id`
* `state_name`
* `country_id`
* `zipcode`
* `phone`
* `active`
* `backorderable_default`
* `propagate_all_variants`
* `admin_name`
