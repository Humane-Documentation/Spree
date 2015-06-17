[Index](../_index.md) » PromotionAction

# (Class) [Spree::PromotionAction](http://m.gymplayer.com/promotion_action.rb)
* Base class for all types of promotion action.
* PromotionActions perform the necessary tasks when a promotion is activated by an event and 
determined to be eligible.

#### Attributes
* `promotion_id`
* `position`
* `type`
* `deleted_at`

## Direct Subclasses
[Spree::Promotion::Actions::CreateAdjustment](Promotion/Actions/CreateAdjustment.md),
[Spree::Promotion::Actions::CreateItemAdjustments](Promotion/Actions/CreateItemAdjustments.md),
[Spree::Promotion::Actions::CreateLineItems](Promotion/Actions/CreateLineItems.md),[Spree::Promotion::Actions::FreeShipping](Promotion/Actions/FreeShipping.md)

## Methods inherited from
* [Base](Base.md)

### Methods included from
* [Spree::Preferences::Preferable](Preferences/Preferable.md)

## Instance Methods
### (Object) **perform**(options = {})
This method should be overriden in subclass Updates the state of the order or
performs some other action depending on the subclass options will contain the
payload from the event that activated the promotion. This will include the key
:user which allows user based actions to be performed in addition to actions
on the order
