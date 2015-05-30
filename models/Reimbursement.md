# Reimbursement Model

| Inherits   | [Base][1]                                                                          |
|------------|------------------------------------------------------------------------------------|
|------------|Object < ActiveRecord::Base < [Base][1] < Spree::Reimbursement                      |
| Includes   |                                                                                    |
| Defined in | app/models/spree/reimbursement.rb                                                  |

### Attributes
* `number`
* `reimbursement_status`
* `customer_return_id`
* `order_id`
* `total`

#### Defined Under Namespace
**Modules:** [ReimbursementTypeValidator][2] **Classes:** [Credit][3], 
[IncompleteReimbursementError][4], [ReimbursementTypeEngine][5]

#### Methods inherited from [Base][1]
[page][6]

#### Methods included from [Preferences::Preferable][7]
[#clear_preferences][8], [#default_preferences][9], [#defined_preferences][10], [#get_preference][11],
[#has_preference!][12], [#has_preference?][13], [#preference_default][14], [#preference_type][15], 
[#set_preference][16]

## Class Attributes
#### (`class_attribute`): reimbursement_tax_calculator
The reimbursement_tax_calculator property should be set to an object that responds to "call"
and accepts a reimbursement object. Invoking "call" should update the tax fields on the
associated ReturnItems.
This allows a store to easily integrate with third party tax services.
    
#### (`class_attribute`): reimbursement_simulator_tax_calculator:
A separate attribute here allows you to use a more performant calculator for estimates
and a different one (e.g. one that hits a 3rd party API) for the final caluclations.
    
#### (`class_attribute`): reimbursement_models
The reimbursement_models property should contain an array of all models that provide
reimbursements.
This allows a store to incorporate custom reimbursement methods that Spree doesn't know about.
Each model must implement a "total_amount_reimbursed_for" method.
Example:
Refund.total_amount_reimbursed_for(reimbursement)
See the `reimbursement_generator` property regarding the generation of custom reimbursements.
        
        
#### (`class_attribute`) :reimbursement_performer
The reimbursement_performer property should be set to an object that responds to the following methods:
- #perform
- #simulate
see ReimbursementPerformer for details.
This allows a store to customize their reimbursement methods and logic.
            
#### (`class_attribute`) :reimbursement_success_hooks
These are called if the call to "reimburse!" succeeds.
            
#### (`class_attribute`) :reimbursement_failure_hooks
These are called if the call to "reimburse!" fails.

## Class Method Details
#### (`Object`) **build_from_customer_return**(customer_return)

## Instance Method Details
#### (`Object`) **calculated_total**
rounding down to handle edge cases for consecutive partial returns where rounding
might cause us to try to reimburse more than was originally billed
      
#### (`Object`) **display_total**

#### (`Object`) **paid_amount**

#### (`Object`) **perform!**

#### (`Object`) **return_items_requiring_exchange**

#### (`Object`) **simulate**

#### (`Object`) **unpaid_amount**
If there are multiple different reimbursement types for a single reimbursement we open ourselves to
a one-cent rounding error for every type over the first one. This is due to how we round 
unpaid_amount and how each reimbursement type will round as well. Since at this point the payments
and credits have already been processed, we should allow the reimbursement to show as 'reimbursed'
and not 'errored'.


[1]: Base.html "Spree::Base (class)"
[2]: Reimbursement/ReimbursementTypeValidator.html "Spree::Reimbursement::ReimbursementTypeValidator (module)"
[3]: Reimbursement/Credit.html "Spree::Reimbursement::Credit (class)"
[4]: Reimbursement/IncompleteReimbursementError.html "Spree::Reimbursement::IncompleteReimbursementError (class)"
[5]: Reimbursement/ReimbursementTypeEngine.html "Spree::Reimbursement::ReimbursementTypeEngine (class)"
[6]: Base.html#page-class_method "Spree::Base.page (method)"
[7]: Preferences/Preferable.html "Spree::Preferences::Preferable (module)"
[8]: Preferences/Preferable.html#clear_preferences-instance_method "Spree::Preferences::Preferable#clear_preferences (method)"
[9]: Preferences/Preferable.html#default_preferences-instance_method "Spree::Preferences::Preferable#default_preferences (method)"
[10]: Preferences/Preferable.html#defined_preferences-instance_method "Spree::Preferences::Preferable#defined_preferences (method)"
[11]: Preferences/Preferable.html#get_preference-instance_method "Spree::Preferences::Preferable#get_preference (method)"
[12]: Preferences/Preferable.html#has_preference%21-instance_method "Spree::Preferences::Preferable#has_preference! (method)"
[13]: Preferences/Preferable.html#has_preference%3F-instance_method "Spree::Preferences::Preferable#has_preference? (method)"
[14]: Preferences/Preferable.html#preference_default-instance_method "Spree::Preferences::Preferable#preference_default (method)"
[15]: Preferences/Preferable.html#preference_type-instance_method "Spree::Preferences::Preferable#preference_type (method)"
[16]: Preferences/Preferable.html#set_preference-instance_method "Spree::Preferences::Preferable#set_preference (method)"
