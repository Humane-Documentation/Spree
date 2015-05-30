# Customization

> This is a general, read-it-first guide to customizing Spree. For tips on customizing a specific
module functionality see its documentation

> Spree roadmap at [https://trello.com/b/PQsUfCL0/spree-roadmap]
(https://trello.com/b/PQsUfCL0/spree-roadmap) is worth checking before customization

## Customization Management
Spree supports three methods for organizing customizations. While they all provide similar
options for customization they differ in re-usability.

### 1) Application Specific
* Tweaks behaviour or appearance to match a business's processes, branding, or add a unique feature
* Customizations are stored within the host application where Spree is installed
* Generally not shared or re-used

### 2) Extension
* Discrete pieces of functionality implemented as Rails engines so they provide a natural way to
bundle all changes needed to implement larger features
* Mostly intended to be installed in multiple Spree
* Mostly distributed as ruby gems

> See [Extension Guide](extensions.md) for more

### 3) Theme
* Designed to overhaul the entire look and feel of a Spree store (or its administration system)
* Don't generally include logic customizations
* Distributed in similar manner to extensions

### To fork or not to fork�
Suppose there's a few details you want to override but aren't the usual things that you'd
override (like views) - so something like tweaks to the models or controllers. You could hide
these in an site extension, but they could get mixed up with your real site
customizations. You could also fork Spree and run your site on this forked version, but this can
also be a headache to get right. There's also the hassle of tracking changes to `spree/master` and
pulling them into your project at the right time.

So here's a compromise: have an extra extension, say `spree-tweaks`, to contain your small
collection of modified files, which is loaded first in the extension order. The benefits are:

- it's clear what you are overriding, and easier to check against core changes
- you can base your project on an official gem release or a `spree/master` commit stage
- such tweaks can become part of your client site project and be managed with SCM etc.

If you find yourself wanting extensive changes to core, this technique probably won't work well.
But then again, if this is the case, then you probably want to look seriously at splitting some code
off into stand-alone extensions and then see whether any of the other code should be contributed to
the core.

## Upgrade Considerations
### Tracking changes for overridden code
* Core changes might impact what's overridden so you might need to patch your custom code or ensure
it interacts correctly with changed code (e.g. using appropriate ids in HTML to so new JS works)
* If you can, help us generalize the core code so your preferred effect is achieved by altering
fewer parameters, this will be more useful than duplicating several files

### Initializers
* Initializers are run during startup and so are the recommended way to execute most settings.
* You can put initializers in extensions, thus have a way to execute extension-specific
configurations

> Avoid modifying `config/boot.rb` and `config/environment.rb`; use [initializers](#initializers)
 instead

## Customization Options
1. **Logic**: Changing and or extension of the logic of Spree to meet specific business requirements
2. **Asset**: Changing static assets provided by Spree, including stylesheets, JavaScript, files
and images
3. **View**: Changing and or extending look and feel of the store and its administration

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -

## 1. Logic Customization

### Extending Classes
* All Spree's business logic (models, controllers, helpers, etc) can easily be extended /
overridden to meet your requirements using standard Ruby.
* Standard practice for including such changes in your application or extension is to create a
file within the relevant **app/models/spree** or  **app/controllers/spree** directory with the
original class name with **_decorator** appended

##### *Examples*

###### Adding a Method to `Product` Model
app/models/spree/product_decorator.rb

```
Spree::Product.class_eval do
  def some_method
    ...
  end
end
```

###### Adding an Action to `ProductsController`
app/controllers/spree/products_controller_decorator.rb

```
Spree::ProductsController.class_eval do
  def some_action
    ...
  end
end
```

> The exact same format can be used to redefine an existing method

###### Accessing Data in Custom Method
You can access product data in the new method using `:load_data before_filter`

```
Spree::ProductsController.class_eval do
  before_filter :load_data, :only => :some_action
  def some_action
    ...
  end
end
```

`:load_data` uses params[:id] to lookup the product by its permalink

### Overriding Controller Action Responses
Spree `respond_override` method supports overriding or changing the output of an existing
controller's action without completely overriding the method (avoiding double render exceptions).
The method is used to customize the response from any action, and is built on top of
Rails's `respond_with` method (which Spree controllers use). It accepts a hash of options:

```
respond_override :action_name => { :format =>  { :result => lambda { ... response ... } } }
```

* `:action_name` Can be any existing action within a controller (:update, :create, :new..)
provided the action is using `respond_with` to define its response
* `:format` Of the request, (:html, :json, :js..). All Spree controllers have a class level
`respond_to` method call that defines which format the controller's actions will respond to
* `:result` Either `:success` or `:failure`. `:success` is default for most but
actions that change or create models get `:failure` response if validation fails for the
model being updated
* `lambda` Contains the actual code to create the desired custom response (i.e. render or
redirect_to). A lambda must be passed to ensure code is evaluated at the correct time

##### *Examples*
To render a custom partial for `index` action of ProductsController, include the following in
**app/controllers/spree/products_controller_decorator.rb**:

```
Spree::ProductsController.class_eval do
  respond_override :index => { :html =>
    { :success => lambda { render 'shared/some_file' } } }
end
```

Or if you wanted to redirect on failure to `create` in `Admin::ProductsController`:

```
Spree::Admin::ProductsController.class_eval do
  respond_override :create => { :html => { :failure => lambda {
    redirect_to some_url } } }
end
```

#### Caveats
* If an action does not use `respond_with` to define its response then `respond_override` will
 **not** work
* Some actions contain several `respond_with` calls so any `respond_override` defined on it
will be executed for any of the `respond_with` instances. It's important therefore to check the
model state/logic within the lambda passed to prevent overriding all possible responses

### Product Images
* Spree uses [paperclip](https://github.com/thoughtbot/paperclip) gem to manage images for products
* All paperclip options are available on Image class
* You may add additional image sizes for use in your templates (e.g. :micro for shopping cart)
* If you want to modify Spree default product and thumbnail image sizes, create
`image_decorator`.rb in your model directory, and override attachment sizes:

```
Spree::Image.class_eval do
  attachment_definitions[:attachment][:styles] = {
    :mini => '48x48>', # thumbs under image
    :small => '100x100>', # images on category view
    :product => '240x240>', # full product image
    :large => '600x600>' # light box image
  }
end
```


#### Image Resizing option syntax
Default behavior is to resize the image and maintain aspect ratio. Commonly used options are:

* trailing #, image will be centrally cropped, ensuring the requested dimensions
* trailing >, image will only be modified if it is currently larger than the requested dimensions
. (i.e. :small thumb for a 100x100 original image will be unchanged)


- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -

## 2. Asset Customization

### Spree's Asset Pipeline
With the release of 3.1 Rails now supports powerful asset management features and Spree fully
leverages these features to further extend and simplify its customization potential. Using asset
customization techniques outlined below you be able to adapt all the JavaScript, stylesheets and
images contained in Spree to easily provide a fully custom experience.

All Spree generated (or upgraded) applications include an `app/assets` directory (as is standard
for all Rails 3.1 apps). We've taken this one step further by subdividing each top level asset
directory (images, JavaScript files, stylesheets) into frontend and backend directories. This is
designed to keep assets from the frontend and backend from conflicting with each other.

A typical assets directory for a Spree application will look like:

    app
    |-- assets
        |-- images
        |   |-- spree
        |       |-- frontend
        |       |-- backend
        |-- javascripts
        |   |-- spree
        |       |-- frontend
        |       |   |-- all.js
        |       |-- backend
        |           |-- all.js
        |-- stylesheets
        |   |-- spree
        |       |-- frontend
        |       |   |-- all.css
        |       |-- backend
        |           |-- all.css

Spree also generates four top level manifests (all.css & all.js, see above) that require all the
core extension's and site specific stylesheets / JavaScript files.

#### How core extensions (engines) manage assets
All core engines have been updated to provide four asset manifests that are responsible for
bundling up all the JavaScript files and stylesheets required for that engine.

For example, Spree provides the following manifests:

    vendor
    |-- assets
        |-- javascripts
        |   |-- spree
        |       |-- frontend
        |       |   |-- all.js
        |       |-- backend
        |           |-- all.js
        |-- stylesheets
        |   |-- spree
        |       |-- frontend
        |       |   |-- all.css
        |       |-- backend
        |           |-- all.css

These manifests are included by default by the relevant all.css or all.js in the host Spree
application. For example, `vendor/assets/javascripts/spree/backend/all.js` includes:

```
//= require jquery
//= require jquery_ujs
//= require spree/backend
//= require_tree .
```

External JavaScript libraries, stylesheets and images have also be relocated into vendor/assets
(again Rails 3.1 standard approach), and all core extensions no longer have public directories.

### Managing your application's assets
Assets that customize your Spree store should go inside the appropriate directories inside
`vendor/assets/images/spree`, `vendor/assets/javascripts/spree`, or `vendor/assets/stylesheets/spree`
This is done so that these assets do not interfere with other parts of your application.

### Managing your extension's assets
We're suggesting that all third party extensions should adopt the same approach as Spree and
provide the same four (or less depending on what the extension requires) manifest files, using
the same directory structure as outlined above.

Third party extension manifest files will not be automatically included in the relevant all.(js|css) files so it's important to document the
manual inclusion in your extensions installation instructions or provide a Rails generator to do so.

For an example of an extension using a generator to install assets and migrations take a look at
the [install_generator for spree_fancy]
(https://github.com/spree/spree_fancy/blob/master/lib/generators/spree_fancy/install/install_generator.rb).

### Overriding Spree's core assets
Overriding or replacing any of Spree's internal assets is even easier than before. It's
recommended to attempt to replace as little as possible in a given JavaScript or stylesheet file
to help ease future upgrade work required.

The methods listed below will work for both applications, extensions and themes with one
noticeable difference: Extension & theme asset files will not be automatically included (see
above for instructions on how to include asset files from your extensions / themes).

#### Overriding individual CSS styles
Say for example you want to replace the following CSS snippet:

```css
/* spree/app/assets/stylesheets/spree/frontend/screen.css */
div#footer {
 clear: both;
}
```

You can now just create a new stylesheet inside
`your_app/vendor/assets/stylesheets/spree/frontend/` and include the following CSS:

```css
/* vendor/assets/stylesheets/spree/frontend/foo.css */
div#footer {
 clear: none;
 border: 1px solid red;
}
```

The `frontend/all.css` manifest will automatically include `foo.css` and it will actually include
 both definitions with the one from `foo.css` being included last, hence it will be the rule
 applied.

#### Overriding entire CSS files
To replace an entire stylesheet as provided by Spree you simply need to create a file with the
same name and save it to the corresponding path within your application's or extension's
`vendor/assets/stylesheets` directory.

For example, to replace `spree/frontend/all.css` you would save the replacement to
`your_app/vendor/assets/stylesheets/spree/frontend/all.css`.

> This same method can also be used to override stylesheets provided by
third-party extensions

#### Overriding individual JavaScript functions
A similar approach can be used for JavaScript functions. For example, if you wanted to override
the `show_variant_images` method:

```javascript
 // spree/app/assets/javascripts/spree/frontend/product.js
var show_variant_images = function(variant_id) {
  $('li.vtmb').hide();
  $('li.vtmb-' + variant_id).show();
  var currentThumb = $('#' +
    $("#main-image").data('selectedThumbId'));
  // if currently selected thumb does not belong to current variant,
  // nor to common images,
  // hide it and select the first available thumb instead.
  if(!currentThumb.hasClass('vtmb-' + variant_id) &&
    !currentThumb.hasClass('tmb-all')) {
   var thumb = $($('ul.thumbnails li:visible').eq(0));
   var newImg = thumb.find('a').attr('href');
   $('ul.thumbnails li').removeClass('selected');
   thumb.addClass('selected');
   $('#main-image img').attr('src', newImg);
   $("#main-image").data('selectedThumb', newImg);
   $("#main-image").data('selectedThumbId', thumb.attr('id'));
 }
}
```

Again, just create a new JavaScript file inside `your_app/vendor/assets/javascripts/spree/frontend`
and include the new method definition:

```javascript
 // your_app/vendor/assets/javascripts/spree/frontend/foo.js
var show_variant_images = function(variant_id) {
 alert('hello world');
}
```

The resulting `frontend/all.js` would include both methods, with the latter being the one
executed on request.

#### Overriding entire JavaScript files
To replace an entire JavaScript file as provided by Spree you simply need to create a file with
the same name and save it to the corresponding path within your application's or extension's
`app/assets/javascripts` directory.

For example, to replace `spree/frontend/all.js` you would save the replacement to
`your_app/vendor/assets/javascripts/spree/frontend/all.js`.

> This same method can be used to override JavaScript files provided
by third-party extensions.

#### Overriding images
Finally, images can be replaced by substituting the required file into the same path within your
application or extension as the file you would like to replace.

For example, to replace the Spree logo you would simply copy your logo to:
`your_app/vendor/assets/images/logo/spree_50.png`.


- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -

## 3. View Customization
### Using Deface
Deface is a standalone Rails library that enables you to customize Erb templates without needing
to directly edit the underlying view file. Deface allows you to use standard CSS3 style selectors
to target any element (including Ruby blocks), and perform an action against all the matching
elements.

For example, take the Checkout Registration template, which looks like this:

```erb
<%%= render 'spree/shared/error_messages', :target => user %>
<h2><%%= Spree.t(:registration) %></h2>
<div id="registration" data-hook>
  <div id="account" class="columns alpha eight">
    <!-- TODO: add partial with registration form -->
  </div>
  <%% if Spree::Config[:allow_guest_checkout] %>
    <div id="guest_checkout" data-hook class="columns omega eight">
      <%%= render 'spree/shared/error_messages', :target => order %>
#
      <h2><%%= Spree.t(:guest_user_account) %></h2>
#
      <%%= form_for order, :url => update_checkout_registration_path,
                           :method => :put,
                           :html => { :id => 'checkout_form_registration' } do |f| %>
        <p>
          <%%= f.label :email, Spree.t(:email) %><br />
          <%%= f.email_field :email, :class => 'title' %>
        </p>
        <p><%%= f.submit Spree.t(:continue), :class => 'button primary' %></p>
      <%% end %>
    </div>
  <%% end %>
</div>
```

If you wanted to insert some code just before the +#registration+ div on the page you would define
an override as follows:

```
Deface::Override.new(:virtual_path  => "spree/checkout/registration",
                     :insert_before => "div#registration",
                     :text          => "<p>Registration is the future!</p>",
                     :name          => "registration_future")
```

This override **inserts** <code><p>Registration is the future!</p></code> **before** the div with
the id of "registration".

#### Available actions
Deface applies an __action__ to element(s) matching the supplied CSS selector. These actions are
passed when defining a new override are supplied as the key while the CSS selector for the target
element(s) is the value, for example:

```
:remove => "p.junk"
:insert_after => "div#wow p.header"
:insert_bottom => "ul#giant-list"
```

Deface currently supports the following actions:

* <tt>:remove</tt> - Removes all elements that match the supplied selector
* <tt>:replace</tt> - Replaces all elements that match the supplied selector, with the content
supplied
* <tt>:replace_contents</tt> - Replaces the contents of all elements that match the supplied selector
* <tt>:surround</tt> - Surrounds all elements that match the supplied selector, expects
replacement markup to contain <%%= render_original %> placeholder
* <tt>:surround_contents</tt> - Surrounds the contents of all elements that match the supplied
selector, expects replacement markup to contain <%%= render_original %> placeholder
* <tt>:insert_after</tt> - Inserts after all elements that match the supplied selector
* <tt>:insert_before</tt> - Inserts before all elements that match the supplied selector
* <tt>:insert_top</tt> - Inserts inside all elements that match the supplied selector, as the first child
* <tt>:insert_bottom</tt> - Inserts inside all elements that match the supplied selector, as the last child
* <tt>:set_attributes</tt> - Sets attributes on all elements that match the supplied selector,
replacing existing attribute value if present or adding if not. Expects :attributes option to be passed.
* <tt>:add_to_attributes</tt> - Appends value to attributes on all elements that match the
supplied selector, adds attribute if not present. Expects :attributes option to be passed.
* <tt>:remove_from_attributes</tt> - Removes value from attributes on all elements that match
the supplied selector. Expects :attributes option to be passed.

> Not all actions are applicable to all elements. For example, <tt>:insert_top</tt> and
 <tt>:insert_bottom</tt> expects a parent element with children.

#### Supplying content

Deface supports three options for supplying content to be used by an override:

* <tt>:text</tt> - String containing markup
* <tt>:partial</tt> - Relative path to a partial
* <tt>:template</tt> - Relative path to a template

> As Deface operates on the Erb source the content supplied to an override can include Erb, it is
not limited to just HTML. You also have access to all variables accessible in the original Erb context.

#### Targeting elements
While Deface allows you to use a large subset of CSS3 style selectors (as provided by Nokogiri),
the majority of Spree's views have been updated to include a custom HTML attribute
(<tt>data-hook</tt>), which is designed to provide consistent targets for your overrides to use.

As Spree views are changed over coming versions, the original HTML elements maybe edited or be
removed. We will endeavour to ensure that data-hook / id combination will remain consistent
within any single view file (where possible), thus making your overrides more robust and upgrade proof.

For example, spree/products/show.html.erb looks as follows:

```erb
<div data-hook="product_show" itemscope itemtype="http://schema.org/Product">
  <%% body_id = 'product-details' %>
  <div class="columns six alpha" data-hook="product_left_part">
    <div class="row" data-hook="product_left_part_wrap">
      <div id="product-images" data-hook="product_images">
        <div id="main-image" data-hook>
          <%%= render 'image' %>
        </div>
        <div id="thumbnails" data-hook>
          <%%= render 'thumbnails', :product => product %>
        </div>
      </div>
      <div data-hook="product_properties">
        <%%= render 'properties' %>
      </div>
    </div>
  </div>
  <div class="columns ten omega" data-hook="product_right_part">
    <div class="row" data-hook="product_right_part_wrap"
      <div id="product-description" data-hook="product_description">
        <h1 class="product-title" itemprop="name"><%%= accurate_title %></h1>
        <div itemprop="description" data-hook="description">
          <%%= product_description(product) rescue Spree.t(:product_has_no_description) %>
        </div>
        <div id="cart-form" data-hook="cart_form">
          <%%= render 'cart_form' %>
        </div>
      </div>
      <%%= render 'taxons' %>
    </div>
  </div>
</div>
```

As you can see from the example above the `data-hook` can be present in
a number of ways:

-   On elements with **no** `id` attribute the `data-hook` attribute
    contains a value similar to what would be included in the `id`
    attribute.
-   On elements with an `id` attribute the `data-hook` attribute does
    **not** normally contain a value.
-   Occasionally on elements with an `id` attribute the `data-hook` will
    contain a value different from the elements id. This is generally to
    support migration from the old 0.60.x style of hooks, where the old
    hook names were converted into `data-hook` versions.

The suggested way to target an element is to use the `data-hook`
attribute wherever possible. Here are a few examples based on
**products/show.html.erb** above:

```
:replace => "[data-hook='product_show']"
:insert_top => "#thumbnails[data-hook]"
:remove => "[data-hook='cart_form']"
```

You can also use a combination of both styles of selectors in a single
override to ensure maximum protection against changes:

```
 :insert_top => "[data-hook='thumbnails'], #thumbnails[data-hook]"
 ```

#### Targeting ruby blocks
Deface evaluates all the selectors passed against the original erb view
contents (and importantly not against the finished / generated HTML). In
order for Deface to make ruby blocks contained in a view parseable they
are converted into a pseudo markup as follows.

> Version 1.0 of Deface, used in Spree 2.1, changed the code tag syntax. Formerly code tags were
parsed as `<code erb-loud>` and `<code erb-silent>`.  They are now parsed as `<erb loud>` and
`<erb silent>`. Deface overrides which used selectors like `code[erb-loud]` should now
use `erb[loud]`.

Given the following Erb file:
```erb
<%% if products.empty? %>
 <%%= Spree.t(:no_products_found) %>
<%% elsif params.key?(:keywords) %>
  <h3><%%= Spree.t(:products) %></h3>
<%% end %>
```
Would be seen by Deface as:
```html
<html>
  <erb[silent]> if products.empty? </erb>
  <erb[loud]> Spree.t(:no_products_found) </erb>
  <erb[silent]> elsif params.key?(:keywords) </erb>
  <h3><erb[loud]> Spree.t(:products) </erb></h3>
  <erb[silent]> end </erb>
</html>
```
So you can target ruby code blocks with the same standard CSS3 style
selectors, for example:
```
:replace => "erb[loud]:contains('t(:products)')"
:insert_before => "erb[silent]:contains('elsif')"
```

#### View upgrade protection
To ensure upgrading between versions of Spree is as painless as
possible, Deface supports an `:original` option that can contain a
string of the original content that's being replaced. When Deface is
applying the override it will ensure that the current source matches the
value supplied and will output to the Rails application log if they are
different.

These warnings are a good indicator that you need to review the source
and ensure your replacement is adequately replacing all the
functionality provided by Spree. This will help reduce unexpected issues
after upgrades.

Once you've reviewed the new source you can update the `:original` value
to new source to clear the warning.

> Deface removes all whitespace from both the actual and `:original`
source values before comparing, to reduce false warnings caused by basic
whitespace differences.

#### Organizing Overrides
The suggested method for organizing your overrides is to create a
separate file for each override inside the **app/overrides** directory,
naming each file the same as the **:name** specified within.

> Using this method will ensure your overrides are compatible with
future theming developments (editor).

#### More information on Deface
For more information and sample overrides please refer to its
[README](https://github.com/railsdog/deface) file on GitHub.

You can also see how Deface internals work, and test selectors using the
[Deface Test Harness](http://deface.heroku.com) application.

### Template Replacements
Sometimes the customization required to a view are so substantial that
using a Deface override seems impractical. Spree also supports the
duplication of views within an application or extension that will
completely replace the file of the same name in Spree.

To override any of Spree's default views including those for the admin
interface, simply create a file with the same filename in your app/views
directory.

For example, to override the main layout, create the file
YOUR_SITE_OR_EXTENSION/app/views/spree/layouts/spree_application.html.erb

> It's important to ensure you copy the correct version of a view
into your application or extension, as copying a mismatched version
could lead to hard to debug issues. We suggest using `bundle show spree`
to get the location of the Spree code you're actually running and then
copying the relevant file from there.

#### Drawbacks of template replacements
Whenever you copy an entire view into your extension or application you
are adding a significant maintenance overhead to your application when
it comes to upgrading to newer versions of Spree. When upgrading between
versions you need to compare each template that's been replaced to
ensure to replicate any changes from the newer Spree version in your
locally copied version.

To this end we strongly suggest you use Deface to achieve the desired
customizations wherever possible.
