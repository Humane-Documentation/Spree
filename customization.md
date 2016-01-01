# Customization

> [Spree Roadmap](https://trello.com/b/PQsUfCL0/spree-roadmap) is worth checking before
customization

## Customization Approaches
### 1) Application Specific
* Tweaks behavior or appearance of Spree for a single host application
* Not intended to be shared or re-used

#### Storing Options
##### In a Spree Fork
* Forking Spree on Github directly customizing it and then running the site on this forked version
* Disadvantages:
    * Can be a headache to get right (Hint: Spree is huge)
    * A hassle to tracking changes to `spree/master` and pulling them into your project at the right time

> If you need extensive changes to core in a fork, you probably would want to look
seriously at splitting the custom code off into stand-alone extensions and then see whether
any of the remaining code should be contributed to the core fork

##### In The Host Application
* Certified Lazy Way
* Disadvantages:
    * Spree customization code and its logic could get mixed up with the original site code and customizations

##### In a Spree Extension
* Having an extra [Spree Extension](#Spree_Extension) (e.g. `spree-tweaks`) to contain the collection of modified
files, and loading first in the extensions order
* Advantages:
  * Basing your project on an official Spree release (with its own git branch)
  * Keeping clear what you are overriding to check against any core changes
  * Easier to modularize in the future

### 2) Modular
#### 2-a) Extension
* Discrete chunks of functionality organized and isolated to implement larger but specific and clear features
* Implemented as a Spree Extension
* Intended to be installed in multiple applications and distributed as ruby gems
* [Spree Extension Registry](http://spreecommerce.com/extensions) is a searchable collection of such extensions written and maintained by the Spree Community

#### 2-b) Theme
* Overhauls the look and feel of a Spree store or admin UIs
* Doesn't include logic customizations
* Mostly distributed as a gem and implemented as a Spree Extension

## Customization Guides
* [Logic](../how_to/logic_customization.md): Changing and or extending logic Spree's logic
* [Asset](../how_to/asset_customization.md): Changing static assets provided by Spree, including stylesheets, JavaScript, files
and images
* [View](../how_to/logic_customization.md): Changing and or extending look and feel of the store and its administration

## Tools & Tips
### Spree Extensions
* Provides a way to organize and isolate customizations needed
* Implemented as Rails engines so it's automatically a gem
* Primary mechanism for customizing Spree

> See the [Spree Extension Exercise](../how_to/extension_exercise.md) for a step-by-step tutorial

### Initializers
* Initializers, which are run during startup, are the recommended way to execute custom application-wide settings
* You can put initializers in extensions, thus have a way to execute extension-specific
configurations

> Avoid modifying `config/boot.rb` and `config/environment.rb`; use initializers instead
 
### Upgrade Considerations
* Core changes might impact what's overridden so you might need to patch your custom code or ensure
it interacts correctly with changed code (e.g. using appropriate ids in HTML to so new JS works)
* If possible, help us generalize the core code so your preferred effect is achieved by altering
fewer parameters. This is more practical than just duplicating files