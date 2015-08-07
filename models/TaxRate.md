[Index](../_index.md) » TaxRate

# (Class) [Spree::TaxRate](http://m.gymplayer.com/tax_rate.rb)
* A zone might have multiple `tax_rates`
* Taxes will be calculated based on best matching zone for the order
* When an order is placed, any product with a tax zone matching the order's zone will be taxed

Tax rates can *potentially* be applicable to an order but this can't be determined until we 
attempt to apply these rates to the order's items. For instance, if a rate 
passes the criteria outlined in this method, but then has a tax category that doesn't match against any 
of the line items inside of the order, then that tax rate will not be applicable to anything

##### *Example*

* Spain (default tax zone)
* France


| Tax Rate | Type      | Category | Country |
|----------|-----------|----------|---------|
| 21%      | inclusive | Clothing | Spain   |
| 18%      | inclusive | Clothing | France  |
| 10%      | inclusive | Food     | Spain   |
| 8%       | inclusive | Food     | France  |
| 5%       | inclusive | Hotels   | Spain   |
| 2%       | inclusive | Hotels   | France  |

If an order had 2 line items, one from Clothing  category and the other from Food category, the tax rates that should be selected:

| Tax Rate | Type      | Category | Country |
|----------|-----------|----------|---------|
| 21%      | inclusive | Clothing | Spain   |
| 10%      | inclusive | Food     | Spain   |

If the order's address changes to one in France, then the tax will be recalculated:

| Tax Rate | Type      | Category | Country |
|----------|-----------|----------|---------|
| 18%      | inclusive | Clothing | France  |
| 8%       | inclusive | Food     | France  |

* Under no circumstances should negative adjustments be applied for the Spanish tax rates
* Those rates should never come into play at all and only the French rates should apply

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

