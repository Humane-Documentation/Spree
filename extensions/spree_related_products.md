# Extension: spree_related_products
[Repo on Github](https://github.com/spree-contrib/spree_related_products)

Provides a way to define different types of relationships between products such as:
* Accessories
* Cross Sells
* Up Sells
* Compatible Products
* Replacement Products
* Warranty & Support Products

## Relation Types
* `RelationType` defines each type of products relationship
* Access related products of a `RelationType` by referencing the `relation_type` name:
```
rt = Spree::RelationType.create(name: 'Accessories', applies_to: 'Spree::Product')
 => #<Spree::RelationType id: 4, name: "Accessories" ...>
product = Spree::Product.last
 => #<Spree::Product id: 1060500592 ...>
product.accessories
 => []
```
* `respond_to?` wouldn't work to test if a `relation_type` method exists or not. Instead, use
`has_related_products?` method:
```
product.has_related_products?('accessories')
# => true
if product.has_related_products?('accessories')
  # Display an accessories box..
end
```
* To access all related products regardless of RelationType:
```
product.relations
 => []
```

### UI
* RelationTypes are defined and managed via admin's interface (Products->Relation Types)
* Manage specific relationships via *Related Products* tab on the admin's product page for each Product

## Discounts
* You can specify a discount amount to be applied if a customer purchases related products
* For a coupon to apply, you must create a promotion and leave *Code* value empty and adding an
Action of type *RelatedProductDiscount*
