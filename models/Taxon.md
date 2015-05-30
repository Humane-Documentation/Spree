## Taxon (Model)

#### Attributes
* `parent_id`
* `position`
* `name`: A required field for all taxons. The name determines what the user will see when they 
look at this product in your store
* `permalink`: The end of the URL a user goes to, in order to see all products associated with this 
taxon. This field is also required, and a value is automatically generated for you when you 
create the taxon. Be careful with arbitrarily changing the permalink - if you have two taxons 
with the same permalink you will run into issues
* `taxonomy_id`
* `lft`
* `rgt`
* `icon_file_name`: Icons are currently not functional
* `icon_content_type`
* `icon_file_size`
* `icon_updated_at`
* `description`: currently not functional
* `meta_title`: Overrides the store's setting for page title when a user visits the taxon's  page
 on the front end of the website
* `meta_description`: Overrides the store's setting for meta description when a user visits the 
taxon's page on the front end of the website
* `meta_keywords`: Overrides the store's setting for meta keywords when a user visits the taxon's
 page on the front end of the website
* `depth`: depth of the taxon within the hierarchy, e.g. the most *parent* depth is 0




### Attributes `products_taxons`
* `product_id`
* `taxon_id`
* `position`
