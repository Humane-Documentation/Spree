[Index](../_index.md) » Reimbursement

# (Class) [Spree::Reimbursement](http://m.gymplayer.com/reimbursement.rb)

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

## Modules
* [ReimbursementTypeValidator](Reimbursement/ReimbursementTypeValidator.md)

## Classes 
* [Credit](Reimbursement/Credit.md),
* [IncompleteReimbursementError](Reimbursement/IncompleteReimbursementError.md)
* [ReimbursementTypeEngine](Reimbursement/ReimbursementTypeEngine.md)


## Class Attributes
#### (class_attribute) reimbursement_tax_calculator
The reimbursement_tax_calculator property should be set to an object that responds to "call"
and accepts a reimbursement object. Invoking "call" should update the tax fields on the
associated ReturnItems.
This allows a store to easily integrate with third party tax services.
    
#### (class_attribute) reimbursement_simulator_tax_calculator:
A separate attribute here allows you to use a more performant calculator for estimates
and a different one (e.g. one that hits a 3rd party API) for the final caluclations.
    
#### (class_attribute) reimbursement_models
The reimbursement_models property should contain an array of all models that provide
reimbursements.
This allows a store to incorporate custom reimbursement methods that Spree doesn't know about.
Each model must implement a "total_amount_reimbursed_for" method.
Example:
Refund.total_amount_reimbursed_for(reimbursement)
See the `reimbursement_generator` property regarding the generation of custom reimbursements.
        
#### (class_attribute) reimbursement_performer
The reimbursement_performer property should be set to an object that responds to the following methods:
- #perform
- #simulate
see ReimbursementPerformer for details.
This allows a store to customize their reimbursement methods and logic.
            
#### (class_attribute) reimbursement_success_hooks
These are called if the call to "reimburse!" succeeds.
            
#### (class_attribute) reimbursement_failure_hooks
These are called if the call to "reimburse!" fails.

## Class Methods
#### (Object) **build_from_customer_return**(customer_return)


## Instance Methods
### (Object) **calculated_total**
rounding down to handle edge cases for consecutive partial returns where rounding
might cause us to try to reimburse more than was originally billed

### (Object) **display_total**


### (Object) **paid_amount**


### (Object) **perform!**
    

### (Object) **return_items_requiring_exchange**


### (Object) **simulate**
    
    
### (Object) **unpaid_amount**
If there are multiple different reimbursement types for a single reimbursement we open ourselves to
a one-cent rounding error for every type over the first one. This is due to how we round 
unpaid_amount and how each reimbursement type will round as well. Since at this point the payments
and credits have already been processed, we should allow the reimbursement to show as 'reimbursed'
and not 'errored'.
