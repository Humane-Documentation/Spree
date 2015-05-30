## Inventory Unit (Model)
Back-ordered, sold, or shipped products are stored as individual `InventoryUnit` objects to have
relevant information attached to them

### Attributes
* `state`: either `on_hand`, `backordered`, `returned` or `shipped`
* `variant_id`
* `order_id`
* `shipment_id`
* `pending`
* `line_item_id`
