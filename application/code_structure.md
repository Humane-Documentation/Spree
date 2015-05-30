# Structure

## Source
To clone the git repository:
```shell
git clone git://github.com/spree/spree.git
```

## Collection of Gems
Spree gem consists of a collection of gems maintained together in a single GitHub
repository. The gems are organized into subdirectories:

| Gem            | Directory | Description                                                       |
| :--------------| :---------| :-----------------------------------------------------------------|
| spree_api      | api       | REST JSON API API for several components below                    |
| spree_backend  | backend   | Admin area for product management, order management, etc.         |
| spree_cmd      | cmd       | Command line utility for installing Spree and creating extensions |
| spree_core     | core      | Core functionality - all other gems depend on this gem            |
| spree_dash     | dash      | Simple overview dashboard [Jirafe](http://jirafe.org)             |
| spree_frontend | frontend  | Customer-facing functionality for product viewing, checkout, etc. |
| spree_sample   | sample    | Data and images for setting up a sample Spree store               |

By requiring the Spree gem you automatically require all of necessary gems and their dependencies.

## Rails Engines
Spree gems are Rails Engines. This provides several advantages:

### Intuitive Customization
Engines behave like fully-functional applications in several aspects such as:
* Models, views and controllers
* Routes
* Helpers
* Rake tasks
* Generators
* Locales

These elements can be overridden in the main Rails application so it's simple to add
Spree to your application and then customize it by supplying your own elements in that same
application.

### Consistency With Rails
Spree receives all of the massive testing and attention to detail that comes for free when using
the Rails core engine functionality rather than a custom solution.

### Modularity
Developers are free to use only the parts of Spree they find useful. For instance, this would
allow you to omit promotions functionality or to replace the authentication mechanism.

It is possible to use only some pieces. For example, you could use just the barebones spree\_core
gem and perhaps combine it with your own custom backend admin instead of using spree_api.

> For more on Rails Engines see [Rails Guides](http://edgeguides.rubyonrails.org/engines.html)
