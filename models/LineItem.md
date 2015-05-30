## Line Item  (Model)
* Tracks an item within the context of an order; links orders and variants (products#variants)
* When a variant is added to an order, the price of that item is tracked along with the line item
 to preserve that data
* If the variant's price changes, the line item will have a record of the price at ordering time

### Attributes
* `variant_id`
* `order_id`
* `quantity`
* `price`
* `currency`
* `cost_price`
* `tax_category_id`
* `adjustment_total`
* `additional_tax_total`
* `promo_total`
* `included_tax_total`: amount if [Tax Included](../business_logic/inventory.md#Tax-Included)
taxation is in use
* `pre_tax_amount`
