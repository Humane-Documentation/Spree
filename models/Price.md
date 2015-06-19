[Index](../_index.md) » Price

# (Class) [Spree::Price](http://m.gymplayer.com/price.rb)
* Tracks a price for a particular currency and variant combination. For instance, a Variant may be available for $15 and also for 7 Euros
* For a product, only variant's with a *price in the site's currency* will be visible in the frontend. If no variants has that then the product will be invisible
* To see the price of a product in the current currency (`Config[:currency]`), call `price` method on the instance:
```shell
product.price
=> "15.99"
```
* To find the currencies a product is available in, call `prices` to get related `Price` objects:
```shell
product.prices
=> [#<Spree::Price id: 2 ...]
```

### Attributes
* `variant_id`
* `amount`
* `currency`
* `deleted_at`

## Methods included from
* [DisplayMoney](DisplayMoney.md)
* [VatPriceCalculation](VatPriceCalculation.md)

### Methods inherited from
* [Base](Base.md)

### Methods included from
* [Spree::Preferences::Preferable](Preferences/Preferable.md)

## Instance Methods
### (Object) **display_price_including_vat_for**(zone)


### (Object) **money**


### (Object) **price**


### (Object) **price=**(price)


### (Object) **price_including_vat_for**(zone)


### (Object) **variant**
Remove variant default_scope `deleted_at: nil`
