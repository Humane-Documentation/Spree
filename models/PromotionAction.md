# Promotion Action Model
* Base class for all types of promotion action.
* PromotionActions perform the necessary tasks when a promotion is activated by an event and 
determined to be eligible.

#### Attributes
* `promotion_id`
* `position`
* `type`
* `deleted_at`

Inherits::  [Base][1]

* Object
* ActiveRecord::Base
* [Base][1]
* Spree::PromotionAction

Defined in:
: app/models/spree/promotion_action.rb


##  Instance Method Summary

* \- (Object) **perform**(options = {})

This method should be overriden in subclass Updates the state of the order or performs some other 
action depending on the subclass options will contain the payload from the event that activated the 
promotion.

### Methods inherited from [Base][1]

[page][2]

### Methods included from [Spree::Preferences::Preferable][3]

[#clear_preferences][4], [#default_preferences][5], [#defined_preferences][6], [#get_preference][7], 
[#has_preference!][8], [#has_preference?][9], [#preference_default][10], [#preference_type][11], 
[#set_preference][12]

## Instance Method Details

### (`Object`) **perform**(options = {})

This method should be overriden in subclass Updates the state of the order or performs some other 
action depending on the subclass options will contain the payload from the event that activated the 
promotion. This will include the key :user which allows user based actions to be performed in addition 
to actions on the order

[1]: Base.html "Spree::Base (class)"
[2]: Base.html#page-class_method "Spree::Base.page (method)"
[3]: Preferences/Preferable.html "Spree::Preferences::Preferable (module)"
[4]: Preferences/Preferable.html#clear_preferences-instance_method "Spree::Preferences::Preferable#clear_preferences (method)"
[5]: Preferences/Preferable.html#default_preferences-instance_method "Spree::Preferences::Preferable#default_preferences (method)"
[6]: Preferences/Preferable.html#defined_preferences-instance_method "Spree::Preferences::Preferable#defined_preferences (method)"
[7]: Preferences/Preferable.html#get_preference-instance_method "Spree::Preferences::Preferable#get_preference (method)"
[8]: Preferences/Preferable.html#has_preference%21-instance_method "Spree::Preferences::Preferable#has_preference! (method)"
[9]: Preferences/Preferable.html#has_preference%3F-instance_method "Spree::Preferences::Preferable#has_preference? (method)"
[10]: Preferences/Preferable.html#preference_default-instance_method "Spree::Preferences::Preferable#preference_default (method)"
[11]: Preferences/Preferable.html#preference_type-instance_method "Spree::Preferences::Preferable#preference_type (method)"
[12]: Preferences/Preferable.html#set_preference-instance_method "Spree::Preferences::Preferable#set_preference (method)"
