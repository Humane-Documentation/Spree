# Promotions

* Provide discounts to orders, as well as add potential additional items at no extra cost
* Can be activated, once checked for eligibility, through `PromotionHandler` when a user either:
  * adds a product to their cart
  * enters a coupon code during the checkout process
  * visits a page within the Spree store
* Promotions relate to two other components:
  * `actions` When a promotion is activated, its actions are performed, passing
 in the payload from `fire_event` call that triggered the activator becoming active
  * `rules` determine if a promotion is applicable
* When a promotion has a `code` or a `path` configured for it, it'll only be
activated if the payload's code or path match the promotion's
  * `code` attribute is used for promotion codes, where a user must enter a code to receive the
 promotion
  * `path` attribute is used to apply a promotion once a user has visited a specific path
* Path-based promotions will only work when `Spree::PromotionHandler::Page` class is used, as
in `Spree::ContentController` from `spree_frontend`
* A promotion may have a `usage_limit` attribute that restricts how many times it can be used

## Promotion Options (UI)
| Option      | Description                                                                 |
|-------------|-----------------------------------------------------------------------------|
| Name        | The name you assign the promotion                                           |
| Event Name  | what must happen before checking promotion eligibility. See options below   |
| Advertise   | Checking this will make the promotion visible to site visitors              |
| Description | Explanation of the promotion for users to see at checkout                   |
| Usage Limit | Maximum number a promotion can be used across all users. No value, no limit |
| Starts At   | Date the promotion becomes valid                                            |
| Expires At  | Date after which the promotion is invalid                                   |

These are the events possible:

| Event Option              | Description                                                          |
|---------------------------|----------------------------------------------------------------------|
| Add to Cart               | An item (any) is added to the cart                                   |
| Order Contents Changed    | Item is added or removed from an order or its quantity changes       |
| User Signup               | User creates an account                                              |
| Coupon Code Added         | User inputs a coupon code at checkout (code has to match)            |
| Visit Static Content Page | User visits a specific path (to read policies, important content...) |

## Actions
Determine what happens when a promotion apply to an order
### Default Actions:
#### Creating Order-Level Adjustment
* When `CreateAdjustment` action is taken, an adjustment is applied to the order unless the
promotion already applied an adjustment
* Once an adjustment is applied, `Promotion#eligible?` method re-checks eligibility every time
 the order is saved
* `Promotion#eligible?` uses `Promotion#eligible_rules` to check if the promotion is still eligible                                                                                              |

#### Creating Item-Level Adjustment
* When a `CreateItemAdjustments` action is taken, an adjustment is applied to each item within
the order unless the action has already been performed on that line item
* Eligibility of an item for the promotion is re-checked whenever it's updated against promo rules
* `CreateAdjustment` utilizes system calculators plus two other:

| Calculator Type  | Additional Data Required                                             |
|------------------|----------------------------------------------------------------------|
| Flat Percent     | Percentage                                                           |
| Flat Rate        | Amount of discount, currency                                         |
| Flexible Rate    | First item cost, additional item cost, max number of items, currency |
| Percent Per Item | Percentage                                                           |
| Free Shipping    | NA                                                                   |

#### Create Line Items
* When a `CreateLineItem` action is taken, a series of line items are added to the order, which
may alter the order's total
* This can be coupled with another action of an adjustment that nullifies the cost of adding the
product(s) to the order

#### Free Shipping
* When a `FreeShipping` action is taken, all shipments within an order have their prices
negated
* Like prior actions, eligibility of this promotion is re-checked whenever a shipment changes

### Customization: Adding a New Action
* Inherit from `Spree::PromotionAction`:
```
class MyPromotionAction < Spree::PromotionAction
  def perform(options={})
    ...
  end
end
```
> Promotion info are accessible using `promotion` method within any `Spree::PromotionAction`

* Register this action with Spree by adding the following to `config/initializers/spree.rb`:
```
Rails.application.config.spree.promotions.actions << MyPromotionAction
```
Action is now available within Spree's interface
* (Optional) To provide translations for the interface, define them within the locale file. For
instance, to define English translations add this to `config/locales/en.yml`:
```yaml
en:
  spree:
    promotion_action_types:
      my_promotion_action:
        name: My Promotion Action
        description: Performs my promotion action.
```

## Rules
* Factors that must be met for a promotion to be applicable to an order
* A promotion can have more than one rule and then `match_policy` attribute determines whether
eligibility requires that:
  * *all* rules must match
  * *any* one rule at least must match

### Default Rules
| Rule               | Description                                             |
|--------------------|---------------------------------------------------------|
| `FirstOrder`       | User's order is their first, Yay!                       |
| `ItemTotal`        | Order total is greater than (or equal to) a given value |
| `Product`          | Order contains a given product                          |
| `User`             | Restrict a promotion to given users                     |
| `UserLoggedIn`     | User ordering is logged in                              |
| `One Use Per User` | Valid only once per user                                |
| `Taxon(s)`         | Order includes product(s) of a given taxon(s)           |


### Customization: Adding a New Rule

* Inherit from `Spree::PromotionRule` as such (note code comments):
```
module Spree
  class Promotion
    module Rules
      class MyPromoRule < Spree::PromotionRule
        def applicable?(promotable)
          promotable.is_a?(Spree::Order)
        end
        def eligible?(order, options = {})
        # should return `true` or `false` to indicate if the promotion is eligible for an order
          ...
        end
        # If the promotion supports giving discounts on only specific line items, this
        # should return true if the specified line item meets the criteria for promotion
        def actionable?(line_item)
          ...
        end
      end
    end
  end
end
```
> Promotion info is retrievable by calling `promotion`

* Register the promotion by adding this to `config/initializers/spree.rb`:
```
Rails.application.config.spree.promotions.rules << Spree::Promotion::Rules::MyPromoRule
```
> Proper location and file name for the rule in this example would be:
`app/models/spree/promotion/rules/my_promo_rule.rb`

* Create a partial for the new rule `app/views/spree/admin/promotions/rules/_my_promo_rule.html.erb`
that's empty if it doesn't parameters or it hascomplex markup to enable setting values for the
new rule.

> Check out the default rule partials for examples

* Add new rule name and description for the locale you will be using. For instance, English edit
`config/locales/en.yml` and add:
```yml
en:
  spree:
    promotion_rule_types:
      my_promotion_rule:
        name: "My Promotion Rule"
        description: "Rule to define my new promotion"
```
* Restart your application and see admin interface

## Spree::Promo::CouponApplicator
???
