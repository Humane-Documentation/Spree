[Index](../_index.md) » Adjustment

# (Class) Spree::Adjustment
Adjustment
Extended by:

    [DisplayMoney](DisplayMoney.md)](https://github.com/spree/spree/blob/master/core/app/models/spree/adjustment.rb)

## Methods included from [DisplayMoney](DisplayMoney.md)

[money_methods](DisplayMoney.md#money_methods-instance_method)

## Instance Methods
###  (Boolean) **closed?**
### (Object) **currency**
###  (Boolean) **promotion?**
### (Object) **update!**(target = adjustable)

Passing a target here would always be recommended as it would avoid hitting
the database again and would ensure you're compute values over the specific
object amount passed here.
