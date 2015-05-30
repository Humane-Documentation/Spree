# Tax Rate Model
* Percentage amount charged based on sales price
* Contains other information:
    * Tax category a product must belong to to be taxable
    * Zone in which order address must be located
    * Whether product prices are inclusive of this tax
* A zone might have multiple `tax_rates`
* Taxes will be calculated based on best matching zone for the order
* When an order is placed, any product that with a tax zone matching the order's zone will be taxed

Tax rates can _potentially_ be applicable to an order. We do not know if they are/aren't until we 
attempt to apply these rates to the items contained within the Order itself. For instance, if a rate 
passes the criteria outlined in this method, but then has a tax category that doesn't match against any 
of the line items inside of the order, then that tax rate will not be applicable to anything. For 
instance:

### Zones:

* Spain (default tax zone)
* France

Tax rates: (note: amounts below do not actually reflect real VAT rates) 21% inclusive - "Clothing" - 
 Spain 18% inclusive - "Clothing" - France 10% inclusive - "Food" - Spain 8% inclusive - "Food" - 
 France 5% inclusive - "Hotels" - Spain 2% inclusive - "Hotels" - France

Order has: Line Item #1 - Tax Category: Clothing Line Item #2 - Tax Category: Food

Tax rates that should be selected:

21% inclusive - "Clothing" - Spain 10% inclusive - "Food" - Spain

If the order's address changes to one in France, then the tax will be recalculated:

18% inclusive - "Clothing" - France 8% inclusive - "Food" - France

Note here that the "Hotels" tax rates will not be used at all. This is because there are no items which 
have the tax category of "Hotels".

Under no circumstances should negative adjustments be applied for the Spanish tax rates.

Those rates should never come into play at all and only the French rates should apply.

#### Attributes
* `amount`
* `zone_id`
* `tax_category_id`
* `included_in_price`
* `name`
* `show_rate_in_label`
* `deleted_at`


Inherits::  [Base][1]

* Object
* ActiveRecord::Base
* [Base][1]
* Spree::TaxRate
show all

Includes:
[AdjustmentSource][2], [CalculatedAdjustments][3]

Defined in:
app/models/spree/tax_rate.rb

### Methods inherited from [Base][1]

[page][4]

### Methods included from [Preferences::Preferable][5]

[#clear_preferences][6], [#default_preferences][7], [#defined_preferences][8], [#get_preference][9], [#has_preference!][10], [#has_preference?][11], [#preference_default][12], [#preference_type][13], [#set_preference][14]

## Class Method Details

### (`Object`) **adjust**(order, items)

This method is best described by the documentation on #potentially_applicable?

### (`Object`) **match**(order_tax_zone)
Gets the array of TaxRates appropriate for the specified order

### (`Object`) **potential_rates_for_zone**(zone)

### (`Object`) **store_pre_tax_amount**(item, rates)

## Instance Method Details

### (`Object`) **adjust**(order, item)

### (`Object`) **compute_amount**(item)

### (`Boolean`) **potentially_applicable?**(order_tax_zone)




[1]: Base.html "Spree::Base (class)"
[2]: AdjustmentSource.html "Spree::AdjustmentSource (module)"
[3]: CalculatedAdjustments.html "Spree::CalculatedAdjustments (module)"
[4]: Base.html#page-class_method "Spree::Base.page (method)"
[5]: Preferences/Preferable.html "Spree::Preferences::Preferable (module)"
[6]: Preferences/Preferable.html#clear_preferences-instance_method "Spree::Preferences::Preferable#clear_preferences (method)"
[7]: Preferences/Preferable.html#default_preferences-instance_method "Spree::Preferences::Preferable#default_preferences (method)"
[8]: Preferences/Preferable.html#defined_preferences-instance_method "Spree::Preferences::Preferable#defined_preferences (method)"
[9]: Preferences/Preferable.html#get_preference-instance_method "Spree::Preferences::Preferable#get_preference (method)"
[10]: Preferences/Preferable.html#has_preference%21-instance_method "Spree::Preferences::Preferable#has_preference! (method)"
[11]: Preferences/Preferable.html#has_preference%3F-instance_method "Spree::Preferences::Preferable#has_preference? (method)"
[12]: Preferences/Preferable.html#preference_default-instance_method "Spree::Preferences::Preferable#preference_default (method)"
[13]: Preferences/Preferable.html#preference_type-instance_method "Spree::Preferences::Preferable#preference_type (method)"
[14]: Preferences/Preferable.html#set_preference-instance_method "Spree::Preferences::Preferable#set_preference (method)"
