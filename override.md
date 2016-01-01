# Override

## Validations
To remove all validations:
```ruby
clear_validators!
```

Assuming we have
```ruby
validates :zzzzz, presence: true
```

```ruby
  _validators[:zzzzz]
    .find { |v| v.is_a? ActiveRecord::Validations::PresenceValidator }
    .attributes
    .delete(:zzzzz)
```

It's possible to skip validations with
```ruby
@dummy.save_without_validation
```