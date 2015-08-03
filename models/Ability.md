[Index](../_index.md) » Ability

# (Class) [Spree::Ability](http://m.gymplayer.com/ability.rb)
> Ability is document under [Authorization](../../authorization)

## Constructor
###  `[Ability]()`) **initialize**(user)
Returns a new instance of Ability

## Class Method
### (Object) **register_ability**(ability)
Allows us to go beyond the standard cancan initialize method which makes it
difficult for engines to modify the default `Ability` of an application. The
`ability` argument must be a class that includes the `CanCan::Ability` module.
The registered ability should behave properly as a stand-alone class and
therefore should be easy to test in isolation.

### (Object) **remove_ability**(ability)
