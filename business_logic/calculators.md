# Calculators

* Used for subclasses of various methods that deal with calculations
* Spree has 5 default Calculators:
    * Flat rate (per order)
    * Flat rate (per item/product)
    * Flat percent
    * Flexible rate (flat rate for first product then a different flat rate for each additional)
    * Price sack

## Default Calculators
### Flat Percent Per Item Total Calculator
Takes an order and calculates an amount

###### *Formula*
[item total] x [flat percentage]

###### *Use*
```
calculator.preferred_flat_percent = 10
```

###### *Example*
If an order had an item total of $31 and the calculator was configured to have a flat percent
amount of 10, the discount would be $31 x 10% = $3.10

### Flat Rate Calculator
Computes a flat rate discount

###### *Preferences*
* `amount`
* `currency`

###### *Use*
```
calculator.preferred_amount = 10
calculator.currency = "USD"
```

### Flexi Rate Calculator
Computes a discount for the first item then a different discount for subsequent items up to a limit

###### *Preferences*
* `first_item`: discounted price of the first item(s)
* `additional_item`: discounted price of subsequent items
* `max_items`: maximum number of items this discount applies to

###### *Formula (up to `max_items`):*
[first item discount] + (([items_count*] - 1) x [additional item discount])

###### *Example*
if you have ten items, your `first_item` preference is $10, your `additional_items` preference
is $5, and your `max_items` is 4, total discount would be $10 * 1 + $5 * 3 + $0 * 6 = $25

### Per Item Calculator
Computes a discount for each order's item included in a store's list of discounted items
Depends on its `calculable` responding to a `promotion` method which:

1. return a `Spree::Promotion` (or similar) object
2. Object returns a list of rules, which should respond to a `products` method
3. This returns a result of matching products
4. List is compared against line items for the order being calculated
5. If any of the matching products are included in the order, they are eligible for this calculator

###### *Preferences*
* `amount` per item to calculate
* `currency`

###### *Formula*
[matching product quantity] x [amount]

###### *Example*
Assuming an `amount` of 5 and there's an order with the following line items:
- Product A: $15.00 x 2 (within matching products)
- Product B: $10.00 x 1 (within matching products)
- Product C: $20.00 x 4 (excluded from matching products)

The calculation would be: (2 x 5) + (1 x 5) = 15

### Percent Per Item Calculator
Identical to Per Item Calculator except it's a percentage, not a flat-rate

###### *Example*
Assuming a calculator amount of 10% and an order of:
- Product A: $15.00 x 2 (within matching products)
- Product B: $10.00 x 1 (within matching products)
- Product C: $20.00 x 4 (excluded from matching products)

The calculation would be ($15 x 2 x 10%) + ($10 x 10%) = $4.

### Price Sack Calculator
Computes a discount for an order when it's over a certain amount

###### *Preferences*
* `minimal_amount`: minimum amount for line items total to trigger the calculator
* `discount_amount`: amount to discount if line items total equals or is greater than `minimal_amount`
* `normal_amount`: amount to discount from order if line items total is less than the `minimal_amount`
* `currency`: currency for calculator, defaults to the store currency `Config[:currency]`

###### *Example*
Suppose you have a Price Sack calculator with a `minimal_amount` preference of $50, a
`normal_amount` preference of $2, and a `discount_amount` of $5.
An order with a line items total of $60 would result in a discount of $5 for the whole order.
An order of $20 would result in a discount of $2.

## Creating a Custom Calculator
* Inherit from `Calculator` class and define `description` and `compute` methods:
```
    class CustomCalculator < Spree::Calculator
      def self.description
        #Human readable description of the calculator
      end
      def compute(object=nil)
        #Returns the value after performing the required calculation
      end
    end
```
* Register calculator as a `tax_rates`, `shipping_methods`, or
`promotion_actions_create_adjustments` by calling this at the end of
`config/initializers/application.rb`:
```
config = Rails.application.config
# assuming this for calculator: `app/models/spree/calculator/shipping/amazing_calculator.rb`
config.spree.calculators.shipping_methods << Calculator::Shipping::AmazingCalculator
```
* If you wish to make a calculator's method dependent on something from the order, re-define
its `available?` method:
```
class CustomCalculator < Spree::Calculator
  def available?(object)
    object.currency == "USD"
  end
end
```

## Calculated Adjustments
If you wish to use Spree's calculator functionality in a model
* Include `Spree::Core::CalculatedAdjustments` module into the model:
```
    class Plan < ActiveRecord::Base
      include Spree::Core::CalculatedAdjustments
    end
```
* Register calculators for this class  `config.spree.calculators.plans << CustomCalculator`
* Access  calculators by calling this method:
```
Plan.calculators
```

Each object for this new class will need a calculator associated so adjustments can be
calculated on them

This module provides a `has_one` association to a `calculator` object, as well as some convenience helpers for creating and updating adjustments for objects.

Assuming that an object has a calculator associated with it first, creating an adjustment is simple:
```
plan.create_adjustment("#{plan.name}", <target object>, <calculable object>)
```
To update this adjustment:
```
plan.update_adjustment(<adjustment object>, <calculable object>)
```
To work out what the calculator would compute an amount to be:
```
plan.compute_amount(<calculable object>)
```
`create_adjustment`, `update_adjustment` and `compute_amount` will call `compute` on the
`Calculator` object. `calculable` amount is whatever object your `CustomCalculator` class supports
