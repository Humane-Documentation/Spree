# Override

## Validations


#### Skipping All Validations
It's possible to skip validations with
```ruby
@dummy.save_without_validation
```

#### Removing All Validations 
To remove all validations:
```ruby
clear_validators!
```

#### Removing Specific Validation
E.g.
```ruby
validates :zzzzz, presence: true
```
Can be removed with
```ruby
  _validators[:zzzzz]
    .find { |v| v.is_a? ActiveRecord::Validations::PresenceValidator }
    .attributes
    .delete(:zzzzz)
```