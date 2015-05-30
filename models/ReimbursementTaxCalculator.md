# Reimbursement Tax Calculator Model

Tax calculation is broken out at this level to allow easy integration with 3rd party
taxation systems.  Those systems are usually geared toward calculating all items at once
rather than one at a time.

To use an alternative tax calculator do this:
```
Spree::ReturnAuthorization.reimbursement_tax_calculator = calculator_object
```
where `calculator_object` is an object that responds to "call" and accepts a reimbursement object
