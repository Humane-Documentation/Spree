[Index](../_index.md) » Promotion

# (Class) [Spree::Promotion](http://m.gymplayer.com/promotion.rb)

### Attributes `promotions`
* `description`
* `expires_at`
* `starts_at`
* `name`
* `type`
* `usage_limit`
* `match_policy`
* `code`
* `advertise`
* `path`
* `promotion_category_id`

### Attributes `orders_promotions`
* `order_id`
* `promotion_id`


### Attributes `products_promotion_rules`
* `product_id`
* `promotion_rule_id`

## Modules
* [Actions](Promotion/Actions.md), [Rules](Promotion/Rules.md)

## Constants
MATCH_POLICIES =%w(all any)

UNACTIVATABLE_ORDER_STATES =["complete", "awaiting_return", "returned"]

## Methods inherited from
* [Base](Base.md)

### Methods included from
* [Spree::Preferences::Preferable](Preferences/Preferable.md)

## Instance Attributes
### (Object) **eligibility_errors** (readonly)
Returns the value of attribute eligibility_errors

## Class Methods
### (Object) **active**


### (Object) **advertised**


### (Boolean) **order_activatable?**(order)


### (Object) **with_coupon_code**(coupon_code)


## Instance Methods
### (Object) **activate**(payload)


### (Object) **adjusted_credits_count**(promotable)
    

### (Object) **credits**


### (Object) **credits_count**


###  (Boolean) **eligible?**(promotable)
called anytime order.update! happens

### (Object) **eligible_rules**(promotable, options = {})
eligible_rules returns an array of promotion rules where eligible? is true for the promotable if
there are no such rules, an empty array is returned if the rules make this promotable ineligible,
then nil is returned (i.e. this promotable is not eligible)
  
###  (Boolean) **expired?**


###  (Boolean) **line_item_actionable?**(order, line_item)

  
### (Object) **products**


###  (Boolean) **usage_limit_exceeded?**(promotable)


###  (Boolean) **used_by?**(user, excluded_orders = [])

