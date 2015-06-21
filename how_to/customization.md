# Customization

> [Spree Roadmap](https://trello.com/b/PQsUfCL0/spree-roadmap) is worth checking before
customization

## Customization Approaches
### 1) Application Specific
* Tweaks behaviour or appearance to match a business's processes, branding, or add a unique feature
* Stored within the host application where Spree is installed
* Generally not shared or re-used

### 2) Extension
* Discrete chunks of functionality implemented as Rails engines
* Provide a modular way to organize and isolate changes needed to implement larger features
* Primary mechanism for customizing Spree
* Usually intended to be installed in multiple applications and distributed as ruby gems
* [Spree Extension Registry](http://spreecommerce.com/extensions) is a searchable collection of
Extensions written and maintained by the Spree Community

> See the [Extension Exercise](../how_to/extensions.md) for a step-by-step guide

### 3) Theme
* Overhauls the look and feel of a Spree store or admin UIs
* Doesn't include logic customizations
* Distributed like gems

### To fork or not to fork
Suppose there's a few details you want to override that aren't views like tweaks to models
or controllers. You could:
* Hide these in the application, but they could get mixed up with your real site code and
customizations
* Fork Spree and run your site on this forked version, but this can be a headache to
get right and also a hassle in tracking changes to `spree/master` and pulling them into your
 project at the right time
* Have an extra extension, say `spree-tweaks`, to contain your small collection of modified
files, which is loaded first in the extensions order. The benefits:
  * Basing your project on an official Spree release (with its own git branch)
  * Keeping clear what you are overriding to check against any core changes
  * Modularize

If you find yourself wanting extensive changes to core, you probably would want to look
seriously at splitting the custom code off into stand-alone extensions and then see whether
any of the other code should be contributed to the core

## Upgrade Considerations
* Core changes might impact what's overridden so you might need to patch your custom code or ensure
it interacts correctly with changed code (e.g. using appropriate ids in HTML to so new JS works)
* If you can, help us generalize the core code so your preferred effect is achieved by altering
fewer parameters, this will be more useful than duplicating several files

## Customization Categories
1. **Logic**: Changing and or extension of the logic of Spree to meet specific business requirements
2. **Asset**: Changing static assets provided by Spree, including stylesheets, JavaScript, files
and images
3. **View**: Changing and or extending look and feel of the store and its administration
