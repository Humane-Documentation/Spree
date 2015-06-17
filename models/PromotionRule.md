[Index](../_index.md) » PromotionRule

# (Class) [Spree::PromotionRule](http://m.gymplayer.com/promotion_rule.rb)

### Attributes
* `promotion_id`
* `user_id`
* `product_group_id`
* `type`
* `code`
* `preferences`

## Direct Subclasses
[Spree::Promotion::Rules::FirstOrder](Promotion/Rules/FirstOrder.md),
[Spree::Promotion::Rules::ItemTotal](Promotion/Rules/ItemTotal.md),
[Spree::Promotion::Rules::OneUsePerUser](Promotion/Rules/OneUsePerUser.md),
[Spree::Promotion::Rules::OptionValue](Promotion/Rules/OptionValue.md),
[Spree::Promotion::Rules::Product](Promotion/Rules/Product.md),
[Spree::Promotion::Rules::Taxon](Promotion/Rules/Taxon.md),
[Spree::Promotion::Rules::User](Promotion/Rules/User.md),
[Spree::Promotion::Rules::UserLoggedIn](Promotion/Rules/UserLoggedIn.md)

## Methods inherited from
* [Base](Base.md)

### Methods included from
* [Spree::Preferences::Preferable](Preferences/Preferable.md)

## Class Methods
### (Object) **for**(promotable)


## Instance Methods
###  (Boolean) **actionable?**(line_item)
This states if a promotion can be applied to the specified line item It is
true by default, but can be overridden by promotion rules to provide
conditions

###  (Boolean) **applicable?**(promotable)


### (Object) **eligibility_errors**


###  (Boolean) **eligible?**(promotable, options = {})

