[Index](../_index.md) » ReimbursementType

# (Class) [Spree::ReimbursementType](http://m.gymplayer.com/reimbursement_type.rb)

### Attributes
* `name`
* `active`
* `mutable`
* `type`: subclass , e.g. `Spree::ReimbursementType::OriginalPayment`

## Direct Subclasses
* [Credit](ReimbursementType/Credit.md)
* [Exchange](ReimbursementType/Exchange.md)
* [OriginalPayment](ReimbursementType/OriginalPayment.md)

## Modules
* [ReimbursementHelpers](ReimbursementType/ReimbursementHelpers.md)

## Classes 
* [Credit](ReimbursementType/Credit.md),
* [Exchange](ReimbursementType/Exchange.md),
* [OriginalPayment](ReimbursementType/OriginalPayment.md)

## Constants
ORIGINAL ='original'

## Class Methods
### (Object) **reimburse**(reimbursement, return_items, simulate)
This method will reimburse the return items based on however it child
implements it By default it takes a reimbursement, the return items it needs
to reimburse, and if it is a simulation or a real reimbursement. This should
return an array
