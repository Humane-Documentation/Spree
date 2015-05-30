# Data Migration (to Spree)

This guide is a mix of tips and information about the relevant APIs, intended to help simplify the
process of getting a new site set up -whether you're developing a fresh site or moving from an
existing commerce platform.

The first section discusses various formats of data. Then we look in detail at import of the product
catalog. Sometimes you may want to import legacy order details, so there's a short discussion on
this.

Finally, there are some tips about how to ease the theme development process.

## Data Import Format

### Direct SQL import
Formatting data as SQL tables and importing it directly isn't recommended as you have to:
* Get the format right
* Deal with associations between tables
* Ensure new data meets system's validation rules

However there are cases where direct import is useful:
* When moving between hosting platforms
* When cloning project so collaborators can just import a database dump and save time of code import

### Rails Fixtures
* Spree uses fixtures to load sample data. It's a convenient for small data sets but tricky with
large ones especially if there are many interconnections and validations
* Rails can dump slices of the database in fixture format

### XML legacy data
* Some systems can export their data in standard spreadsheet formats
* Tools like REXML or Nokogiri can parse XML and either build a spreadsheet representation
or execute product-building actions directly

### SQL legacy data
* Try to build a Rails interface to the data (e.g. search for help with legacy
mappings) and dump a simplified format
* It might help to use views or complex queries to flatten multi-table data into a single table that
can then be treated like a spreadsheet

### Spreadsheet format
Most information about products can be flattened into spreadsheet form. For example, your
spreadsheet could have the following columns:

##### Fixed Details (columns)
-  product name
-  master price
-  master sku
-  taxon membership
-  shipping category
-  tax category
-  dimensions and weight
-  list of images
-  description

##### Properties
one column for each property type used in your catalog

##### Variant Specifications
- option types for the product
- one variant per column, each listing the option values and the price/sku

If you know how many fixed columns and properties to expect then it's easy to
determine which columns represent variants etc.

Some of these columns might have simple punctuation etc. to add structure to the field. We used:
* Html tags in the description
* *"WxHxD"* as a shorthand for dimensions
* *"green & small = small_green_shirt @ $10.00"* as a variant that's small and green, has
sku *small_green_shirt* and costs $10
* *"drinks\npizza"* in taxons column to encode membership of 2 taxons
* *"food > bakery > french"* in taxons column to encode membership and nesting

The taxon nesting notation is useful when:
* taxon name doesn't uniquely identify it (e.g. 'french'  from above) so you need ancestor taxons
* taxon structure isn't fixed in advance so taxons are created as products are entered

Another possibility for variants is to have each on a separate row, and leave the fixed fields
empty when a row is a variant of the last introduced product.

### Seed code
* Easiest way to load seed data is to put ruby files in *site/db/default/* so when `rake db:seed`
is called they're processed in the order of the migration timestamps
* Your ruby script can use one of the XLS or CSV format reading libraries to read an external
file, or if the data set is not too big, you could embed the CSV text in the script itself

> If order of loading is important, choose names so alphabetical order gives the correct load order

## Catalog Creation
Assume you're working from a CSV format, one product per row, and each row contains values for
fixed details, properties, and variants configuration.

### Products
* Products must have at least a name and a price to pass validation:
```
p = Spree::Product.create :name => 'some product',
                          :price => 10.0,
                          :description => 'some text here'
```
* The*permalink+ and timestamps are added automatically

* Set `available_on` field with a date in the past. Otherwise the product won't be listed:
```
p.available_on = Time.now
```

#### Master Variant (Probably out of date info)
* Accessible via `p.master` but many of its fields are accessible through `product` via delegation
so `p.price` is equivalent to `p.master.price`
* Delegation allows field modification so `p.price = 2 * p.price` doubles product's (master) price

If you don't have variants (other than master) then you must:
* Set `sku` field for the master variant
* Register stock for the master variant (Probably assigning `p.on_hand = 100` or a different
number suffices)

### Taxons
Adding a product to a particular taxon is easy: just add the taxon to the list of taxons for a
product.
```
p.taxons << some_taxon
```
Recall that taxons work like subclassing in OO languages, so a product in taxon T is also contained
in T's ancestors, so you should usually assign a product to the most specific applicable taxon - and
do not need to assign it to all of the taxon's ancestors.

However, you can assign products to as many taxons as you want, including ancestor taxons. This
feature is more useful with sibling taxons, e.g. assigning a red and green shirt to both 'red
clothes' and 'green clothes'.

***
Yes, this also means that child taxons don't have to be distinct, ie they can overlap.
***

When uploading from a spreadsheet, you might have one or more taxons listed for a product, and these
taxons will be identified by name. Individual taxon names don't have to be unique, e.g. you could
have 'shirts' under 'male clothing', and 'shirts' under 'female clothing'. In this case, you need
some context, eg 'male clothing > shirts' vs. 'female clothing > shirts'.

Do you need to create the taxon structure in advance? Not always: as the code below shows, it is
possible to create taxons as and when they are needed, but this can be cumbersome for deep
hierarchies. One compromise is to create the top levels (say the top 2 or 3 levels) in advance, then
use the taxon information column to do some product-specific fine tuning.

The following code uses a list of (newline-separated) taxon descriptions- possibly using 'A > B > C'
style of context to assign the taxons for a product. Notice the use of `where.first_or_create`.
```

# create outside of loop
  main_taxonomy = Spree::Taxonomy.where(:name => 'Products').first_or_create
# inside of main loop
the_taxons = []
taxon_col.split(/[\r\n]*/).each do |chain|
  taxon = nil
  names = chain.split
  names.each do |name|
    taxon = Spree::Taxon.where.first_or_create
  end
  the_taxons << taxon
end
p.taxons = the_taxons
```
You can use similar code to set up other taxonomies, e.g. to have a taxonomy for brands and product
ranges, like 'Guitars' with child 'Acoustic'. You could use various property or option values to
drive the creation of such taxonomies.

### Product Properties
The first step is to create the property 'types'. These should beknown in advance so you can define
these at the start of the script. Youshould give the internal name and presentation name. For
simplicity, the codeexamples have these names as the same string.
```
size_prop = Spree::Property.where(name: 'size', presentation: 'Size').first_or_create
```
Then you just set the value for the property-product pair.
Assuming value*size_info+ which is derived from the relevant
column, this means:
```
Spree::ProductProperty.create :property => size_prop, :product => p, :value => size_info
```

#### Product Prototypes
The admin interface uses a system of 'prototypes' to speed up data entry, which seeds a product with
a given set of option types and (empty)property values. It probably isn't so useful when creating
products programmatically, since the code will need to do the hard work of creating variants and
setting properties anyway. However, we mention it here for completeness.

### Variants
Variants allow different versions of a product to be offered, e.g.allowing variations in size and
color for clothing. If a product comes in onlyone configuration, you don't need to use variants -
the master variant,already created, is sufficient.

Otherwise, you need to declare what the allowed option types are (e.g.
size, color, quality rating, etc) for your product, and then create variants
which (usually) have a single option value for each of the product's option
types (e.g. 'small' and 'red' etc).

> Spree's core generally assumes that each variant has exactly one option value for each of the
product's option types, but the current code is tolerant of missing values. Certain extensions may
be more strict, e.g. ones for providing advanced variant selection.

#### Creating Variants
New variants require only a product to be associated with, but it isuseful to set an identifying
`sku` code too. The price field is optional: if it is notexplicitly set, the new variant will use
the master variant's price (the same applies tocost_price` too). You can also set the `weight`,
`width`, `height`, and `depth` too.
```
v = Spree::Variant.create :product => p, :sku => "some_sku_code", :price => NNNN
```

> The price is only copied at creation, so any subsequent changes to a product's price will need to be
copied to all of its variants

Next, you may also want to register some stock for this variant.
The exact steps depend on how you have configured Spree's
[inventory system](inventory.html), but most sites
will just need to assign to `v.on_hand`, eg `v.on_hand = 100`.

You now need to set some option types and values, so customers can
choose between the variants.

#### Option Types
The option types to use will vary from product to product, so you willneed to give this information
for each product - or assume a defaultand only use different names when this column is empty.

You can probably declare most of the option types in advance, and so
just look up the names when required, though for fine control, you can
use the `where.first_or_create` technique, with something like this:
```
p.option_types = option_names_col.map do |name|
  Spree::OptionType.where(:name => name, :presentation => name).first_or_create
end
```

#### Option Values
Option values represent the choices possible for some option type.Again, you could declare them in
advance, or use `where.first_or_create`. You'llprobably find it easier to create/retrieve the option
values as you create each variant.

Suppose you are using a notation like `"Green & Small = small_green_shirt @ $10.00"`
to encode each variant in the spreadsheet, and this is stored in the variable
`opt_info`. The following extracts the three key pieces of information and sets
the option values for the new variant (see below for variant creation).
```
*,opts,sku,price = opt_info.match\s*=\s*\s*@.\*?)/).to_a
v = Spree::Variant.create :product => p, :sku => sku, :price => price
v.option_values = opts.split.map do |nm|
  Spree::OptionValue.where.first_or_create
end
```

> You don't have to stick with system-wide option types: you can create types specifically for  groups
of products such as a product range from a single manufacturer. In such cases, the range might have
a particular color scheme and there can be advantages to isolating the scheme's options in its own
type and set of values, rather than trying to work with a more general setup. It also avoids filling
up a type with lots of similar options - and so reduces the number of options when using faceted
search etc. You can also attach resources like color swatches to the more specific values.

#### Ordering of Option Values
You might want option values to appear in a certain order, such as by
increasing size or by alphabetical order. The `Spree::OptionValue` model uses
`acts_as_list` for setting the order, and option types will use the `position` field when retrieving
their associated values. The position is scoped to the relevant option type.

If you create option values in advance, just create them in the required
order and the plugin will set the `position` automatically.
```
color_type = Spree::OptionType.create :name => 'Color', :presentation => 'Color'
color_options = %w[Red Blue Green].split.map { |n|
  Spree::OptionValue.create :name => n, :presentation => n,
  :option_type => color_type }
```

Otherwise, you could enforce the ordering*after_ loading up all of the
variants, using something like this:
```
color_type.option_values.sort_by(&:name).each_with_index do |val,pos|
  val.update_attribute(:position, pos + 1)
end
```

#### Further reading
[Steph Skardal](https://github.com/stephskardal) has produced a usefulblog post on
[productoptioning](http://blog.endpoint.com/2010/01/rails-ecommerce-spree-hooks-comments.html).This
discusses how the variant option representation works and how sheused it to build an extension for
enhanced product option selection.

### Product and Variant Images
Spree uses [paperclip](https://github.com/thoughtbot/paperclip) to manage image attachments and
their various size formats. (See the [Customization Guide](customization.md#product-images) for 
info on
altering the image formats.) You can attach images to products and to variants - the mechanism is
polymorphic. Given some local image file, the following will associate the image and create all of
the size formats.

```

#for image for product (all variants) represented by master variant
img = Spree::Image.create(:attachment => File.open(path), :viewable => product.master)
#for image for single variant
img = Spree::Image.create(:attachment => File.open(path), :viewable => variant)
```

Paperclip also supports external [storage of images in
S3](https://github.com/thoughtbot/paperclip/blob/master/lib/paperclip/storage.rb)
