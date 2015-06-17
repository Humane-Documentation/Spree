[Index](../_index.md) » AppConfiguration

# (Model) [Spree::AppConfiguration](http://m.gymplayer.com/app_configuration.rb)
* Primary location for defining spree preferences
* Created once and stored in the spree environment

## setters:
a.color = :blue
a[:color] = :blue
a.set :color = :blue
a.preferred_color = :blue

## getters:
a.color
a[:color]
a.get :color
a.preferred_color

## Dynamic Method Handling
This class handles dynamic methods through the `method_missing` method in the class 
[Spree::Preferences::Configuration](Preferences/Configuration.md#method_missing-instance_method)

## Instance Methods
### (Object) **searcher_class**
searcher_class allows spree extension writers to provide their own Search class

### (Object) **searcher_class=** (sclass)
