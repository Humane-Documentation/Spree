## Payment Method (Model)
* Represents options for making a payment online or offline
* Mostly gateway options but also include default support for a Check payment which can 
be used for offline payments
* Third-party extensions provide support for other options

### Attributes
* `type`: subclass of `PaymentMethod` represented. Uses rails single table inheritance
* `name`
* `description`
* `active`: Setting it `false` deactivates this payment method and hides it in frontend
* `deleted_at`
* `display_on`: Setting it `front` shows it only in the frontend, `back` shows it only in the
backend and setting it `both` shows it in both
* `auto_capture`
* `preferences`

### Methods
#### PaymentMethod.available
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

#### PaymentMethod.auto_capture?
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
