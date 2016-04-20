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

## Model Callbacks
```ruby
# remove `Model.`
Model.skip_callback(:destroy, :before, :check_if_admin), :prepend => :true
```

## Methods
#### Removing
##### `undef`
`#=> NoMethodError`
##### `remove_method`
`#=> nil`

For example
```ruby
num = Number.new
num << 4 #=> [4]
num.include? #=> "Just kidding"
Number.class_eval("remove_method :include?")
num.include? 4 #=> true
Number.class_eval("undef include?")
num.include? 4 #=> NoMethodError
```

#### Removing Alias


```ruby
alias_method :fake?, :original?
```
can be removed with
```ruby
remove_method :fake?
```
However, if `alias_method` overwrites an existing method
```ruby
# assuming :original? is already a method 
alias_method :fake?, :original?
alias_method :original?, :temproary_original?
```
To restore the first state:
```ruby
alias_method :original?, :fake?
remove_method :fake?  # optional
```





---

```ruby

```
```ruby

```
```ruby

```

