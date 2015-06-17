[Index](../_index.md) » Calculator

# (Class) [Spree::Calculator](http://m.gymplayer.com/calculator.rb)
Used for several subclasses that deal with various types of calculations.

### Attributes
* `type`: the calculator class used
* `calculable_id`
* `calculable_type`: `TaxRate` or `ShippingMethod`..
* `preferences`

## Direct Subclasses
[FakeCalculator](../FakeCalculator.md),
[DefaultTax](Calculator/DefaultTax.md),
[FlatPercentItemTotal](Calculator/FlatPercentItemTotal.md),
[FlatRate](Calculator/FlatRate.md), [FlexiRate](Calculator/FlexiRate.md),
[FreeShipping](Calculator/FreeShipping.md),
[PercentOnLineItem](Calculator/PercentOnLineItem.md),
[PercentPerItem](Calculator/PercentPerItem.md),
[PriceSack](Calculator/PriceSack.md),
[TieredFlatRate](Calculator/TieredFlatRate.md),
[TieredPercent](Calculator/TieredPercent.md),
[ReturnsCalculator](ReturnsCalculator.md),
[ShippingCalculator](ShippingCalculator.md)


## Modules
* [Returns](Calculator/Returns.md)

## Classes 
* [DefaultTax](Calculator/DefaultTax.md),
[FlatPercentItemTotal](Calculator/FlatPercentItemTotal.md),
[FlatRate](Calculator/FlatRate.md),
[FlexiRate](Calculator/FlexiRate.md),
[FreeShipping](Calculator/FreeShipping.md),
[PercentOnLineItem](Calculator/PercentOnLineItem.md),
[PercentPerItem](Calculator/PercentPerItem.md),
[PriceSack](Calculator/PriceSack.md),
[Shipping](Calculator/Shipping.md),
[TieredFlatRate](Calculator/TieredFlatRate.md),
[TieredPercent](Calculator/TieredPercent.md)

## Class Methods
### (Object) **calculators**
Returns all calculators applicable for kind of work

### (Object) **description**
overwrite to provide description for your calculators

### (Object) **register**(*klasses)

## Instance Methods
###  (Boolean) **available?**(object)

### (Object) **compute**(computable)
This method calls a compute_<computable> method. must be overriden in concrete
calculator.

It should return amount computed based on #calculable and the computable
parameter


### (Object) **description**


### (Object) **to_s**

> See [Calculator Guide](../business_logic/calculators.md) for more info
