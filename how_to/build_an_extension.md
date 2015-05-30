# Extensions

Extensions are the primary mechanism for customizing Spree, sharing reusable code and organizing
and isolating discrete chunks of functionality

## Extension Registry
[Spree Extension Registry](http://spreecommerce.com/extensions) is a searchable collection of
Extensions written and maintained by members of the [Spree Community]
(http://spreecommerce.com/community)

If you need to extend Spree application's functionality, look in the Extension Registry first;
you may find an extension that either implements what you need or provides a good starting point

## Creating an Extension
Suppose we want the ability to mark certain products as being on sale. We'd like to be able to:
* set a sale price on a product
* show products that are on sale on a separate page

Start by generating the extension outside of the Spree application:
```shell
spree extension simple_sales
cd spree_simple_sales
```
This creates a `spree_simple_sales` directory with several files and directories

### Adding a Sale Price to Variants

We next create a migration that adds `sale_price` column to variants:
```shell
bundle exec rails g migration add_sale_price_to_spree_variants sale_price:decimal
```
Because we are dealing with prices, we edit the generated migration to ensure the correct precision
and scale. Edit the file `db/migrate/XXXXXXXXXXX_add_sale_price_to_spree_variants.rb` so it contains
```
class AddSalePriceToSpreeVariants < ActiveRecord::Migration
  def change
    add_column :spree_variants, :sale_price, :decimal, :precision => 8, :scale => 2
  end
end
```

### Adding Our Extension to the Spree Application
This will allow us to see how the extension works with an actual store as we develop it.

Within the `mystore` application directory, add to `Gemfile`:
```
gem 'spree_simple_sales', :path => '../spree_simple_sales'
```
Adjust the path depending on where you created the extension relative to `mystore` directory.
After this bundle:
```shell
bundle install
```
Next run `spree_simple_sales` install generator to copy over the migration we created
```shell
rails g spree_simple_sales:install
```

### Adding a Controller Action to HomeController
Now we need to extend `Spree::HomeController` to add an action that selects "on sale" products

> Note for the sake of this example `Spree::HomeController` is only included in
spree_frontend so you need to make it a dependency in your extensions *.gemspec file

Go to `spree_simple_sales` root to create the directory structure for our controller decorator:
```shell
mkdir -p app/controllers/spree
```
Next, create `home_controller_decorator.rb` in the new directory and add the following to it:
```
module Spree
  HomeController.class_eval do
    def sale
    # This selects only the products that have a variant with a `sale_price` set
      @products = Product.joins(:variants_including_master)
                         .where('spree_variants.sale_price is not null').uniq
    end
  end
end
```
Now we create a route to this action in `config/routes.rb` file:
```
Spree::Core::Engine.routes.draw do
  get "/sale" => "home#sale"
end
```

### Viewing On Sale Products
#### Setting Sale Price for a Variant
Let's update the sample data so we have at least one product that is on sale. We will use the
rails console as we have no admin interface to set sale prices for variants:
```shell
rails console
```
Now, follow the steps I take in selecting a product and updating its master variant to have a sale
price. Note, you may not be editing the exact same product as I am, but this is not important. We
just need one "on sale" product to display on the sales page.
```irb
> product = Spree::Product.first
=> #<Spree::Product id: 107377505, name: "Spree Bag", description: "Lorem ipsum dolor sit amet, consectetuer adipiscing...", available_on: "2013-02-13 18:30:16", deleted_at: nil, permalink: "spree-bag", meta_description: nil, meta_keywords: nil, tax_category_id: 25484906, shipping_category_id: nil, count_on_hand: 10, created_at: "2013-02-13 18:30:16", updated_at: "2013-02-13 18:30:16", on_demand: false>
> variant = product.master
=> #<Spree::Variant id: 833839126, sku: "SPR-00012", weight: nil, height: nil, width: nil, depth: nil, deleted_at: nil, is_master: true, product_id: 107377505, count_on_hand: 10, cost_price: #<BigDecimal:7f8dda5eebf0,'0.21E2',9(36)>, position: nil, lock_version: 0, on_demand: false, cost_currency: nil, sale_price: nil>
> variant.sale_price = 8.00
=> 8.0
> variant.save
=> true
```

### Creating a View
To create a view to display on sale products we first create the required views directory:
```shell
mkdir -p app/views/spree/home
```
Next, create `app/views/spree/home/sale.html.erb` and add this to it:
```erb
<div data-hook="homepage_products">
  <%%= render 'spree/shared/products', :products => @products %>
</div>
```
If you navigate to `http://localhost:3000/sale` you should see the product(s) listed that we set
a `sale_price` on. However their prices aren't correct.

### Decorating Variants
To fix our extension so it uses `sale_price` when present, we first create the required
directory structure for our new decorator:
```shell
mkdir -p app/models/spree
```
Next, create `app/models/spree/variant_decorator.rb` and add this to it:
```
module Spree
  Variant.class_eval do
  # We alias `price_in` method to `orig_price_in` and override it
    alias_method :orig_price_in, :price_in
    def price_in(currency)
    # If there is a `sale_price` on the product's master variant we return it otherwise we
    # call the original implementation of `price_in`
      return orig_price_in(currency) unless sale_price.present?
      Spree::Price.new(:variant_id => self.id, :amount => self.sale_price, :currency => currency)
    end
  end
end
```

### Testing Our Decorator
We should be careful with our Variant decorator since we are modifying core Spree functionality.

#### Generating the Test App
From our extension root, we run Spree `test_app` rake task to generate a barebones Spree
application within our `spec` directory to run our tests against:
```shell
bundle exec rake test_app
```
After this running `rspec` should show that it there are no tests in it (yet):
```shell
No examples found.
Finished in 0.00005 seconds
0 examples, 0 failures
```
Let's replicate the extension's directory structure in our spec directory:
```shell
mkdir -p spec/models/spree
```
In the new directory, let's create `variant_decorator_spec.rb` and add the following tests to it:
```
require 'spec_helper'
describe Spree::Variant do
  describe "#price_in" do
    it "returns the sale price if it is present" do
      variant = create(:variant, :sale_price => 8.00)
      expected = Spree::Price.new(:variant_id => variant.id,
                                  :currency => "USD",
                                  :amount => variant.sale_price)
      result = variant.price_in("USD")
      result.variant_id.should == expected.variant_id
      result.amount.to_f.should == expected.amount.to_f
      result.currency.should == expected.currency
    end
    it "returns the normal price if it is not on sale" do
      variant = create(:variant, :price => 15.00)
      expected = Spree::Price.new(:variant_id => variant.id,
                                  :currency => "USD",
                                  :amount => variant.price)
      result = variant.price_in("USD")
      result.variant_id.should == expected.variant_id
      result.amount.to_f.should == expected.amount.to_f
      result.currency.should == expected.currency
    end
  end
end
```
These test that the `price_in` method we overrode in our `VariantDecorator` returns the
correct price both when the sale price is present and when it is not.

### Deface Override
To add a field to product edit admin page that allows `sale_price` to be added
or updated we could override the view Spree provides but there are potential problems.
If Spree updates the view in a new release we won't get the updated view as we are already
overriding it. We would need to update our view with the new content from Spree and then
add our customizations back in to stay fully up to date.

Let's do this instead using Deface to keep our view customizations in one spot, `app/overrides`,
and make sure we are always using the latest implementation of the view provided by Spree.

#### Implementation
We want to override the product edit admin page, so the view we want to modify in this case is the
product form partial. This file's path will be `spree/admin/products/_form.html.erb`.

First, let's create the overrides directory with the following command:
```shell
mkdir app/overrides
```
So we want to override `spree/admin/products/_form.html.erb`. Here is the part of the file we are
going to add content to (you can also view the [full file]
(https://github.com/spree/spree/blob/master/backend/app/views/spree/admin/products/_form.html.erb)):
```erb
<div class="right four columns omega" data-hook="admin_product_form_right">
<%%= f.field_container :price do %>
    <%%= f.label :price, raw(Spree.t(:master_price) + content_tag(:span, ' *',
     :class => 'required')) %>
    <%%= f.text_field :price, :value => number_to_currency(@product.price,
      :unit => '') %>
    <%%= f.error_message_on :price %>
<%% end %>
```
We want our override to insert another field container after the price field container. We can do
this by creating a new file `app/overrides/add_sale_price_to_product_edit.rb` and adding the
following content:
```
Deface::Override.new(:virtual_path => 'spree/admin/products/_form',
  :name => 'add_sale_price_to_product_edit',
  :insert_after => "erb[loud]:contains('text_field :price')",
  :text => "
    <%%= f.field_container :sale_price do %>
      <%%= f.label :sale_price, raw(Spree.t(:sale_price) + content_tag(:span, ' *')) %>
      <%%= f.text_field :sale_price, :value =>
        number_to_currency(@product.sale_price, :unit => '') %>
      <%%= f.error_message_on :sale_price %>
    <%% end %>
  ")
```
We also need to delegate `sale_price` to the master variant in order to get the updated product edit
form working.

We can do this by creating a new file `app/models/spree/product_decorator.rb` and adding the
following content to it:
```
module Spree
  Product.class_eval do
    delegate_belongs_to :master, :sale_price
  end
end
```
Now, when we head to `http://localhost:3000/admin/products` and edit a product, we should be  able
to set a sale price for the product and be able to view it on our sale page,
`http://localhost:3000/sale`.

## Versioning the Extension
Different versions of Spree may act differently with your extension so it's advisable to keep
different branches of your extension maintained for the different branches of Spree.

It's advisable that your extension follows the same versioning pattern as Spree itself. Having a
consistent branching naming scheme across Spree and its extensions will reduce confusion in
the long run.
