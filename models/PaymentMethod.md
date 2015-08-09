[Index](../_index.md) » PaymentMethod

# (Class) [Spree::PaymentMethod](http://m.gymplayer.com/payment_method.rb)

## Attributes
* `type`: subclass of `PaymentMethod` represented. Uses rails single table inheritance
* `name`
* `description`
* `active`: Setting it `false` deactivates this payment method and hides it in frontend
* `deleted_at`
* `display_on`: Setting it `front` shows it only in the frontend, `back` shows it only in the
backend and setting it `both` shows it in both
* `auto_capture`
* `preferences`

## Direct Subclasses
[Gateway](Gateway.md), [GatewayWithPassword](GatewayWithPassword.md),
[Check](PaymentMethod/Check.md)


## Classes 
* [Check](PaymentMethod/Check.md)

## Constants
DISPLAY =[:both, :front_end, :back_end]

## Methods
## Methods inherited from
* [Base](Base.md)

### Methods included from
* [Spree::Preferences::Preferable](Preferences/Preferable.md)

## Class Methods
### (Boolean) **active?**


### (Object) **available**(display_on = 'both')
Showing a payment method on either frontend, backend or both depends on meeting
`PaymentMethod.available` method criterion:
```
def self.available(display_on = 'both')
  all.select do |p|
    p.active &&
    (p.display_on == display_on.to_s || p.display_on.blank?)
  end
end
```

### (Object) **find_with_destroyed**(*args)


### (Object) **providers**## Instance Methods


###  (Boolean) **auto_capture?**
* Depends on `Config[:auto_capture]` preference. If it's set `true` payments will be automatically
captured during processing. If it's set `false` payments will be only authorized
* If `Config[:auto_capture]` is set `true` but you don't want a specific `PaymentMethod` to be
auto-capturable then override `auto_capture?` in its subclass:
```
class FancyPaymentMethod < Spree::PaymentMethod
  def auto_capture?
    false
  end
end
```

### (Object) **cancel**(response)
Raises: (`::NotImplementedError`)

### (Object) **method_type**


###  (Boolean) **payment_profiles_supported?**


### (Object) **payment_source_class**
The class that will process payments for this payment type, used for @payment.source e.g. CreditCard
in the case of a the Gateway payment type nil means the payment method doesn't require a source e.g.
check

Raises: (`::NotImplementedError`)

### (Object) **provider_class**
Raises: (`::NotImplementedError`)

### (Object) **reusable_sources**(order)
Custom gateways should redefine this method. See Gateway implementation as an example

### (Boolean)  **source_required?**


###  (Boolean) **supports?**(source)
