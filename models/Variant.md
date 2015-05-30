# Variant Model

> Variant is document in detail under [Product](./Product)

#### Attributes
* `sku`
* `weight`
* `height`
* `width`
* `depth`
* `deleted_at`
* `is_master`
* `product_id`
* `cost_price`
* `cost_currency`
* `position`
* `track_inventory`
* `tax_category_id`
* `stock_items_count`


| Inherits   | Base                                                                               |
|------------|------------------------------------------------------------------------------------|
|------------|Object < ActiveRecord::Base < [Base][1] < Spree::Variant                            |
| Includes   | [DefaultPrice][2]                                                                  |
| Defined in | app/models/spree/variant.rb                                                        |


### Methods inherited from [Base][1]

[page][3]

### Methods included from [Preferences::Preferable][4]

[#clear_preferences][5], [#default_preferences][6], [#defined_preferences][7], [#get_preference][8], 
[#has_preference!][9], [#has_preference?][10], [#preference_default][11], [#preference_type][12], 
[#set_preference][13]

## Class Method Details

### (`Object`) **active**(currency = nil)

### (`Object`) **having_orders**

## Instance Method Details

### (`Object`) **amount_in**(currency)

### (`Boolean`) **can_supply?**(quantity = 1)

### (`Object`) **cost_price=**(price)

### (`Boolean`) **deleted?**
use deleted? rather than checking the attribute directly. this allows extensions to override deleted? 
if they want to provide their own definition.

### (`Object`) **descriptive_name**

### (`Object`) **exchange_name**

### (`Boolean`) **in_stock?**

### (`Boolean`) **is_backorderable?**

### (`Object`) **name_and_sku**

### (`Object`) **on_backorder**
returns number of units currently on backorder for this variant.

### (`Object`) **option_value**(opt_name)

### (`Object`) **options=**(options = {})

### (`Object`) **options_text**

### (`Object`) **price_in**(currency)

### (`Object`) **price_modifier_amount**(options = {})

### (`Object`) **price_modifier_amount_in**(currency, options = {})

### (`Object`) **product**
Product may be created with `deleted_at` already set, which would make AR's default finder return 
nil. 
This is a stopgap for that little problem.

### (`Object`) **set_option_value**(opt_name, opt_value)

### (`Boolean`) **should_track_inventory?**
Shortcut method to determine if inventory tracking is enabled for this variant This considers both 
variant tracking flag and site-wide inventory tracking settings

### (`Object`) **sku_and_options_text**

### (`Object`) **tax_category**

### (`Object`) **total_on_hand**

### (`Object`) **weight=**(weight)

[1]: Base.html "Spree::Base (class)"
[2]: DefaultPrice.html "Spree::DefaultPrice (module)"
[3]: Base.html#page-class_method "Spree::Base.page (method)"
[4]: Preferences/Preferable.html "Spree::Preferences::Preferable (module)"
[5]: Preferences/Preferable.html#clear_preferences-instance_method "Spree::Preferences::Preferable#clear_preferences (method)"
[6]: Preferences/Preferable.html#default_preferences-instance_method "Spree::Preferences::Preferable#default_preferences (method)"
[7]: Preferences/Preferable.html#defined_preferences-instance_method "Spree::Preferences::Preferable#defined_preferences (method)"
[8]: Preferences/Preferable.html#get_preference-instance_method "Spree::Preferences::Preferable#get_preference (method)"
[9]: Preferences/Preferable.html#has_preference%21-instance_method "Spree::Preferences::Preferable#has_preference! (method)"
[10]: Preferences/Preferable.html#has_preference%3F-instance_method "Spree::Preferences::Preferable#has_preference? (method)"
[11]: Preferences/Preferable.html#preference_default-instance_method "Spree::Preferences::Preferable#preference_default (method)"
[12]: Preferences/Preferable.html#preference_type-instance_method "Spree::Preferences::Preferable#preference_type (method)"
[13]: Preferences/Preferable.html#set_preference-instance_method "Spree::Preferences::Preferable#set_preference (method)"
