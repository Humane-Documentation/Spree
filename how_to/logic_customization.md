# Logic Customization

## Extending Classes
* All Spree's logic (models, controllers, helpers, etc) can easily be extended/overridden
using standard Ruby
* Standard practice for including customizations in your application or extension is to
create a file within the relevant **(app/models/spree)** or  **(app/controllers/spree)**
directory with the original class name appended with `_decorator`

### Adding/Redefining a Method
For an action in `Product` Model, create `app/models/spree/product_decorator.rb` with:
```
Spree::Product.class_eval do
  def some_method
    ...
  end
end
```
The exact same format can be used to redefine an existing method

### Adding/Redefining an Action
For an action in `ProductsController`, create
`app/controllers/spree/products_controller_decorator.rb` with:
```
Spree::ProductsController.class_eval do
  def some_action
    ...
  end
end
```

### Accessing Data in a Custom Method
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

## `respond_override`
* A method that overrides or changes the output of a controller's action without completely overriding the method (avoiding double render exceptions)
* Can customize the response from any action, and is built on top of
Rails's `respond_with` method (which Spree controllers use).
* Accepts a hash of options:
  * `:action_name` Can be any existing action within a controller (:update, :create, :new..)
  provided the action is using `respond_with` to define its response
  * `:format` Of the request, (:html, :json, :js..). All Spree controllers have a class level
  `respond_to` method call that defines which format the controller's actions will respond to
  * `:result` Either `:success` or `:failure`. `:success` is default for most but
  actions that change or create models get `:failure` response if validation fails for the
  model being updated
  * `lambda` Contains the actual code to create the desired custom response (i.e. render or
  redirect_to). A lambda must be passed to ensure code is evaluated at the correct time

```
respond_override :action_name => { :format =>  { :result => lambda { ... response ... } } }
```

### *Examples*
To render a custom partial for `index` action of `ProductsController`, create
`app/controllers/spree/products_controller_decorator.rb` with:
```
Spree::ProductsController.class_eval do
  respond_override :index => { :html =>
    { :success => lambda { render 'shared/some_file' } } }
end
```

To redirect on failure to `create` in `Admin::ProductsController`:
```
Spree::Admin::ProductsController.class_eval do
  respond_override :create => { :html => { :failure => lambda {
    redirect_to some_url } } }
end
```

### Caveats
* If an action does not use `respond_with` to define its responses then `respond_override` will
 **not** work
* Some actions contain several `respond_with` calls so a `respond_override` defined on it
will be executed for any or all of its `respond_with` instances. It's important then to check the
model state/logic within the lambda passed to prevent overriding all possible responses

## Product Images
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

### Image Resizing option syntax
Default behavior is to resize the image and maintain aspect ratio. Commonly used options are:
* trailing #, image will be centrally cropped, ensuring the requested dimensions
* trailing >, image will only be modified if it is currently larger than the requested dimensions
. (i.e. :small thumb for a 100x100 original image will be unchanged)
