## Preferences

* General application configuration and preferences per model instance like `logo` and `currency`
* To implement preferences for a model make sure your it inherits from `Spree::Base` then add
`preferences` column. This is an example migration:
```
class AddPreferencesColumnToSpreeProducts < ActiveRecord::Migration
  def up
    add_column :spree_products, :preferences, :text
  end
  def down
    remove_column :spree_products, :preferences
  end
end
```
This works because `Spree::Product` is a subclass of `Spree::Base`. If found, `preferences`
attribute gets serialized into a `Hash` and merged with the default values

> If you're using `spree_auth_devise`, then `Spree::User` doesn't inherit from `Spree::Base`

## General Settings
* Application-wide preferences are in `core/app/models/spree/app_configuration.rb`, available
through `Config`, e.g., `Spree::Config.site_name`
* Few general settings for admin interface are in (`/admin/general_settings`)
* You can add additional preferences under `spree/app_configuration` namespace or create a subclass
of `Preferences::Configuration`
```
# These will be saved with key: spree/app_configuration/hot_salsa
Spree::AppConfiguration.class_eval do
  preference :hot_salsa, :boolean
  preference :dark_chocolate, :boolean, :default => true
  preference :color, :string
  preference :favorite_number
  preference :language, :string, :default => 'English'
end
# Spree::Config is an instance of Spree::AppConfiguration
Spree::Config.hot_salsa = false
# Create your own class
# These will be saved with key: kona/store_configuration/hot_coffee
Kona::StoreConfiguration < Preferences::Configuration
  preference :hot_coffee, :boolean
  preference :color, :string, :default => 'black'
end
KONA::STORE_CONFIG = Kona::StoreConfiguration.new
puts KONA::STORE_CONFIG.hot_coffee
```

## Defining Preferences
* Done within the model itself
* For each preference, a data type is provided. The types available are:
    * `boolean`
    * `string`
    * `password`
    * `integer`
    * `text`
    * `array`
    * `hash`
* A default value may be defined which will be used unless a value was set for that instance

###### Example
```
class User < ActiveRecord::Base
  preference :hot_salsa, :boolean
  preference :dark_chocolate, :boolean, :default => true
  preference :color, :string
  preference :favorite_number, :integer
  preference :language, :string, :default => "English"
end
```

## Accessing Preferences
Accessed either using the shortcut methods generated for each preference or generic methods not
specific to any preference

### Shortcut Methods
**Query methods**
```
user.prefers_hot_salsa? # => false
user.prefers_dark_chocolate? # => false
```
**Reader methods**
```
user.preferred_color      # => nil
user.preferred_language   # => "English"
```
**Writer methods**
```
user.prefers_hot_salsa = false         # => false
user.preferred_language = "English"    # => "English"
```
**Preference availability?**
```
user.has_preference? :hot_salsa
```

### Generic Methods
Each shortcut method is essentially a wrapper for the generic methods below:

**Query method**
```
user.prefers?(:hot_salsa)       # => false
user.prefers?(:dark_chocolate)  # => false
```
**Reader methods**
```
user.preferred(:color)      # => nil
user.preferred(:language)   # => "English"
```
```
user.get_preference :color
user.get_preference :language
```
**Writer method**
```
user.set_preference(:hot_salsa, false)     # => false
user.set_preference(:language, "English")  # => "English"
```

### Accessing All Preferences
Access a hash of all stored preferences by accessing the `preferences` helper:
```
user.preferences # => {"language"=>"English", "color"=>nil}
```
This hash contains value for every preference defined for the model instance, whether the value is
default or previously stored

### Accessing Default Value
```
user.preferred_color_default # => 'blue'
```

### Types
* Used to generate forms or display the preference
* You can get the type defined for a preference:
```
user.preferred_color_type # => :string
```

## Configuring Spree Preferences
### Reading the Current Preferences
* `Config` constant provides general access to settings anywhere in the application whether from
initializers, models, controllers, views, etc.
* `Config` constant returns an instance of `AppConfiguration` which is where default values for all
general preferences are defined
* If you are using default preferences without modifications then nothing is stored in the database
* If you set a value for the preference it will save it to `spree_preferences` or in
`preferences` column. It will use a memory cached version to maintain performance
* You can access preferences from code. For example, Using a `rails console`:
```
>> Spree::Config.admin_interface_logo
=> "logo/spree_50.png"
>> Spree::Config.admin_products_per_page
=> 10
```

### Overriding Default Preferences
Default preferences in `AppConfiguration` can be changed using `set` method of `Config` module then
the preference system will persist the new value in the `spree_preferences` table

###### Example
```
>> Spree::Config.admin_products_per_page = 20
=> 20
>> Spree::Config.admin_products_per_page
=> 20
```

### Configuration Through Spree Initializer
During Spree installation, an initializer file is created under `config/initializers/spree.rb` and
its `Spree.config` block is a shortcut to setting `Config` multiple times. If you have
multiple default preferences you would like to override may do it here to keep your
preferences organized in a standard location.

> Preferences in `config/initializer.rb` will overwrite any changes that were made
through the admin user interface when you restart

###### Example
```
Spree.config do |config|
  config.admin_interface_logo = 'logo/my_store.png'
  config.tax_using_ship_address = true
end
```

### Configuration Through Admin Interface
The admin interface has several different screens where various settings can be configured

## Site-Wide Preferences
* Done by creating a configuration file that inherits from `Preferences::Configuration`:
```
class Spree::MyApplicationConfiguration < Spree::Preferences::Configuration
  preference :theme, :string, :default => "Default"
  preference :show_splash_page, :boolean
  preference :number_of_articles, :integer
end
```
* It is recommended to create the configuration file in `lib/` directory

### Configuring Site-Wide Preferences
Recommended way is through an initializer:
```
module Spree
# must first instantiate the configuration object
  MyApp::Config = Spree::MyApplicationConfiguration.new
end
MyApp::Config[:theme] = "blue_theme"
MyApp::Config[:show_spash_page] = true
MyApp::Config[:number_of_articles] = 5
```

## Spree Configuration Options
* `address_requires_state` determines if state field appears on the checkout page. Default: `true`
* `admin_interface_logo` Path to the logo to display on the admin interface. Can be different
 from `Spree::Config[:logo]`. Default: `logo/spree_50.png`
* `admin_products_per_page` number of products per page in the admin interface . Default: `10`
* `allow_backorder_shipping` Determines if an `InventoryUnit` can ship or not. Default: `false`
* `allow_checkout_on_gateway_error` Continues checkout even if gateway error failed. Default: `false`
* `alternative_shipping_phone` Determines if an alternative phone number should be present for
the shipping address on the checkout page. Default: `false`
* `always_put_site_name_in_title` Determines if the site name (`current_store.site_name`) should be
in the title. Default: `true`
* `attachment_default_url` Tells `Paperclip` the form of URL to use for missing attachments
* `attachment_path` Tells `Paperclip` path where to store images
* `attachment_styles` A JSON hash of different styles supported by attachments. Default:
```
{
  "mini":"48x48>",
  "small":"100x100>",
  "product":"240x240>",
  "large":"600x600>"
}
```
* `attachment_default_style` Key from list of styles from `Config[:attachment_styles]` which is
default style for images. Default: `product` style
* `auto_capture` whether a purchase or an authorize operation will be performed on the card via
current gateway. Default: `false`
* `checkout_zone` Limits checkout to countries from a specific zone by name. Default: `nil`
* `company` whether or not a "Company" field appears on checkout pages for addresses. Default: `false`
* `currency` three-letter currency code in which prices will be displayed in. Default: "USD"
* `default_country_id` default country's id. Default: 214 (United States within the seed data)
* `dismissed_spree_alerts` List of alert IDs that you have dismissed
* `last_check_for_spree_alerts` Stores last time alerts were checked for which occur every 12 hours
* `layout` path to layout folder relative to `app/views` directory. Default:
`spree/layouts/spree_application`. To make Spree use another use this:
```
Spree.config do |config|
  config.layout = "application"
end
```
* `logo` logo displayed on frontend. Default: `logo/spree_50.png`
* `max_level_in_taxons_menu` number of levels to descend when viewing a taxon menu. Default: `1`
* `orders_per_page` number of orders per page in admin backend. Default: `15`
* `prices_inc_tax` Determines if prices are labelled as including tax or not. Default: `false`
* `shipment_inc_vat` Determines if shipments should include VAT calculations. Default: `false`
* `shipping_instructions` if shipping instructions are requested or not at checkout. Default: `false`
* `show_descendents` Determines if taxon descendants are shown when showing taxons. Default: `true`
* `show_only_complete_orders_by_default` Determines if on admin screen only completed  orders are
shown. Default: `true`
* `show_variant_full_price` Determines if variant's full price or price difference from a
product should be displayed on product's show page. Default: `false`
* `tax_using_ship_address` Determines if tax information should be based on shipping address
rather than the billing address. Default: `true`
* `track_inventory_levels` Determines if inventory levels are tracked when products are purchased at
checkout causing new `InventoryUnit` objects to be created when a product is bought. Default: `true`

### Important system-wide settings
Settings that your app need to function correctly should be set using initializers

## S3 Support
To configure Spree to upload images to S3, add this to `config/initializers/spree.rb`:
```
Spree.config do |config|
  config.use_s3 = true
  config.s3_bucket = '<bucket>'
  config.s3_access_key = "<key>"
  config.s3_secret = "<secret>"
end
```
It's better to not include `rails_root` path inside `attachment_path` configuration option,
which by default is:
```
:rails_root/public/spree/products/:id/:style/:basename.:extension
```

To change this, add this below `s3_secret` configuration setting:
```
config.attachment_path = '/spree/products/:id/:style/:basename.:extension'
```

Additionally, you need to tell `paperclip` how to construct URLs for your images by placing this
code outside `config` block inside `config/initializers/spree.rb`:
```
Paperclip.interpolates(:s3_eu_url) do |attachment, style|
  "#{attachment.s3_protocol}://#{Spree::Config[:s3_host_alias]}/#{attachment
   .bucket_name}/#{attachment.path(style).gsub(%r{^/}, "")}"
end
```
