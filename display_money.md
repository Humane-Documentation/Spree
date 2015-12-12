[Index](../_index.md) » DisplayMoney

# (Concern) [Spree::DisplayMoney](http://m.gymplayer.com/concerns/spree/display_money.rb)

## Methods
### `money_methods`
Takes a list of methods that the base object wants to be able to use
to display with Spree::Money, and turns them into display_* methods.
Intended to help clean up some of the presentational logic that exists
at the model layer.
    
    
#### Examples
Decorate a method, with the default option of using the base object's 
currency
```ruby
    extend Spree::DisplayMoney
    money_methods :tax_amount, :price
```
Decorate a method, but with some additional options
```ruby
    extend Spree::DisplayMoney
    money_methods tax_amount: { currency: "CAD", no_cents: true }, :price
```