## Stock Item (Model)
* Represent inventory at a stock location for a specific variant
* Created automatically for each `StockLocation`
* Stock item count on hand can be increased or decreased by creating stock movements

#### Attributes
* `stock_location_id`
* `variant_id`
* `count_on_hand`
* `backorderable`
* `deleted_at`
