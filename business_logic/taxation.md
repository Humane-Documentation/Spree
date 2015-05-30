## Taxation

* Taxes are represented using `tax_categories` and `tax_rates`
* Spree default is to treat everything as exempt from tax

## Components
### Tax Category (Model)
See [here](../models/TaxCategory.md)

### Tax Rate (Model)
See [here](../models/TaxRate.md)

## `DefaultTax` Calculator
* Suitable for both sales tax and price-inclusive tax
* Uses the item total (exclusive of shipping) when computing sales tax

##### *Example*
Zones: "Pennsylvania", "New York", "European Union"
Tax Categories: "clothing", "electronics"
Tax Rates: 6%, 10%, 5%
hypothetical 1:You need to charge 5% tax for all items that ship to New York and 6% on clothing that
ship to Pennsylvania. This will mean you need to construct two different zones: one zone containing
state of New York and another for state of Pennsylvania

hypothetical 2: You would like to charge 10% tax on all electronics and 5% tax on everything else.
This tax should apply to all countries in the European Union (EU). In this case you would construct
a single zone consisting of all countries in the EU. The fact that you want to charge two different
rates depending on the type of good does not mean you need two zones

## Shipping vs. Billing Address
* Most jurisdictions base tax on the shipping address so it's the Spree's default
* To calculate tax based on billing address instead, set `Config[:tax_using_ship_address]` to `false`

## Tax Types
### Sales Tax
* Used in the US
* Default tax type for any tax rate in Spree.
* Applied to the order as an adjustment

#### Example
Zone 1: North America
Tax Rate 1: 5% tax on "Tax category 1", Linked to "Zone 1"
Tax Category 1: "Clothing"
customer purchases 1 coffee mug and 2 of a clothing item priced at $17.99 and they live in US
Tax amount: ($17.99 x 2) x 0.05 is $1.799, which is rounded up to two decimal places, applying a tax
adjustment of $1.80 to the order. coffee mug is not taxed

### Tax Included
* Used in European Union (EU) and other countries
* Commonly referred to as a Value Added Tax (VAT.) or "tax inclusive" pricing
* Applied directly to the item price so prices for items displayed are "inclusive of tax" and no
additional tax needs to be applied during checkout
* Admin should enter all prices inclusive of tax
* Each order records the price paid (including tax) as part of the line item record. This means you
don't have to worry about changing prices or tax rates on older orders.
