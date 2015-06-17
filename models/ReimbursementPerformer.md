[Index](../_index.md) » ReimbursementPerformer

# (Class) [Spree::ReimbursementPerformer](http://m.gymplayer.com/reimbursement_performer.rb)

## Class Methods
### (Object) **perform**(reimbursement)
Actually perform the reimbursement

### (Object) **simulate**(reimbursement)
Simulate performing the reimbursement without actually saving anything or
refunding money, etc. This must return an array of objects that respond to the
following methods:
* #description
* #display_amount
so they can be displayed in the Admin UI appropriately.
