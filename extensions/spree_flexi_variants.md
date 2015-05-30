# Extension: spree_flexi_variants
[Repo on Github](https://github.com/QuintinAdam/spree_flexi_variants)

### Screencasts
[Youtube playlist](http://www.youtube.com/my_playlists?p=1B8009EE2FF96FED)

### ERD Diagram
![ERD Diagram](https://dl.dropboxusercontent.com/u/87019235/images/erd.jpeg)

## Ad Hoc Options (Addons)
* Used when there are many options (possibly price-altering) and you don't want to create variants
for each combination
* Doesn't conflict with normal variants
* Can be required (forced) at product selection time or not
* Beneficial when the number of options types/values grows

### Ad Hoc Exclusions (Illegal Combinations)
* You can restrict combinations of options from coexisting if for example:
  * certain option combinations are unavailable
  * certain option combinations can't coexist
* Exclusions will not work if the addon uses `multi-select` scheme (e.g. pizza toppings)

### Customizing UI
Done by creating a partial with the same name as the addon in
`app/views/products/ad_hoc_options`, e.g. `app/views/products/ad_hoc_options/_toppings.html.erb`.
This is helpful when enabling **multiple option values** within an addon to be selected

##### *Example*
If a product needs to have two addons sizes and colors where all sizes alter the price,
but no colors does:
* Go to admin's product page
* Create option types `size` and `colors`, and add associated option values
* On a the same admin's product page, go to  *Ad Hoc Option Types* tab on the bottom right
* Add both option types
* Each option type's option values will appear along with price fields. Give each a price
(including 0.00 if you like)

On the store's product page you'll see drop downs where the price changes based on selection.
Adding the product to the cart will indicate the addon(s) in its description

* add a third option type, "gloss", with values "dull", "shiny", and "annoying"
* Go to *Ad Hoc Exclusions* admin product's page and add these illegal combinations
  * Color "blue" isn't allowed with finish "annoying" (size doesn't matter)
  * Another illegal combination is size=small, color=green, and gloss="dull"
* Go to store's product page and see the drop-down

## Product Customizations
* Provide highly customized products with full control over pricing using Spree calculators e.g.
- Cut to length 5 .82cm
- Engrave 'thanks for the memories'
- Upload my image
* Some calculators are provided but you can create your own
  * See `product_area` calculator for a customization that has more than one customizable option
  * You can add image customizations using the image customization calculator

### Customizing UI
adding appropriately named partial in the following manner: If customization is named
`cake_candles` with one customizable option named `amount`, options:

Done by creating a partial with its name either
* based on `customization_type` name, placed in `./customization_type`
* based on `calculator_type` name, placed in `./calculator_type` e.g. for calculator
`Calc::MyCalc` the partial would be `calculator_type/_my_calc.html.erb`

##### *Example*
* Inside admin app `Products` go to *Customization Types* sub-menu item
* Create a new type
  * called `length_customization`
  * presentation `Cut to length (inches)`
  * Leave the description blank
  * select AmountTimesConstant calculator
* fill in options for the calculator and the customization option row and update
* Create `rope` product then click *Customization Types* tab on the bottom right
* Click 'Add Product Customization Type' link and select `length_customization` to the product
* go to the store, select rope, enter a length, and add to cart

## Screenshot Examples
* `Cake` using **Ad Hoc Options** and **Product Customizations**
![Cake](https://raw.github.com/jsqu99/spree_flexi_variants/master/doc/cake_screenshot.png)
* `Necklace` using **Ad Hoc Options** and **Product Customizations**
![Necklace](https://raw.github.com/jsqu99/spree_flexi_variants/master/doc/necklace_screenshot.png)
* `Pizza` using **Ad Hoc Options**. (Note `multi` option checkboxes come from a partial named
after the option name `app/views/products/ad_hoc_options/_toppings.html.erb`)
![Picture Frame](https://raw.github.com/jsqu99/spree_flexi_variants/master/doc/pizza_screenshot.png)
