[Index](../_index.md) » TaxRate

# (Class) [Spree::TaxRate](http://m.gymplayer.com/tax_rate.rb)


#### Attributes
* `amount`: Percentage amount charged based on sales price
* `zone_id`: Zone in which order address must be located
* `tax_category_id`: Tax category a product must belong to to be taxable
* `included_in_price`: Whether product prices are inclusive of this tax
* `name`
* `show_rate_in_label`
* `deleted_at`

## Class Methods
### (Object) **adjust**(order, items)
Deletes all tax adjustments, then applies all applicable rates to relevant items.
This method is best described by the documentation on #potentially_applicable?

### (Object) **match**(order_tax_zone)
Gets the array of TaxRates appropriate for the specified tax zone
      
### (Object) **potential_rates_for_zone**(zone)


### (Object) **included_tax_amount_for**(zone, category)


### (Object) **store_pre_tax_amount**(item, rates)
Pre-tax amounts must be stored so that we can calculate correct rate amounts
in the future. For example: 
[github.com/spree/spree/issues/4318#issuecomment-34723428](https://github.com/spree/spree/issues/4318#issuecomment-34723428)

## Instance Methods
### (Object) **adjust**(order, item)


### (Object) **compute_amount**(item)


### (Boolean) **potentially_applicable?**(order_tax_zone)

