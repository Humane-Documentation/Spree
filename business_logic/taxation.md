## Taxation
* Taxes are represented using `tax_categories` and `tax_rates`
* Spree default is to treat everything as exempt from tax
* Taxes are calculated based on best matching zone for the order
* When an order is placed, any product with a tax zone matching the order's zone will be taxed
* A zone might have multiple `tax_rates`

## Components
### Tax Category (Model)
See [here](../models/TaxCategory.md)

* Grouping products which are taxed the same way
* A product must belong to a tax category to be taxable
* A `tax_category` can have many `tax_rates`
* One Tax Category can be set as default so if a product doesn't have a related tax
 category, the default tax category would apply

### Tax Rate (Model)
See [here](../models/TaxRate.md)

* Under no circumstances should negative adjustments be applied for tax rates

Tax rates applicability to an order can't be determined until we 
attempt to apply these rates to the order's items. For instance, if a rate 
passes the criteria outlined in this method, but then has a tax category that doesn't match against any of the line items inside of the order, then that tax rate will not be applicable to anything


## `DefaultTax` Calculator
* Suitable for both sales tax and price-inclusive tax
* Uses the item total (exclusive of shipping) when computing sales tax

##### *Example*
You need to charge 5% tax for all items that ship to New York and 6% on clothing that
ship to Pennsylvania. This will mean you need to construct two different zones: one zone containing
state of New York and another for state of Pennsylvania

| Tax Rate | Category    | Zone         |
|----------|-------------|--------------|
| 6%       | Clothing    | Pennsylvania |
| 5%       | Food        | New York     |
| 5%       | electronics | New York     |

##### *Example*
You would like to charge 10% tax on all electronics and 5% tax on everything else.
This tax should apply to all countries in the European Union (EU). In this case you would construct
a single zone consisting of all countries in the EU. The fact that you want to charge two different
rates depending on the type of good does not mean you need two zones

| Tax Rate | Category    | Zone         |
|----------|-------------|--------------|
| 10%      | electronics | EU Countries |
| 5%       | Food        | EU Countries |
| 5%       | electronics | EU Countries |

## Shipping vs. Billing Address
* Most jurisdictions base tax on the shipping address so it's the Spree's default
* To calculate tax based on billing address instead, set `Config[:tax_using_ship_address]` to `false`

## Tax Types
### Sales Tax
* Used in the US
* Default tax type for any tax rate in Spree.
* Applied to the order as an adjustment

#### Example
| Tax Rate | Category | Zone          |
|----------|----------|---------------|
| 5%       | Clothing | North America |

If a customer purchases 1 coffee mug and 2 of a clothing item priced at $17.99 and they live in US
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


##### *Example*

* Spain (default tax zone)
* France


| Tax Rate | Type      | Category | Zone    |
|----------|-----------|----------|---------|
| 21%      | inclusive | Clothing | Spain   |
| 18%      | inclusive | Clothing | France  |
| 10%      | inclusive | Food     | Spain   |
| 8%       | inclusive | Food     | France  |
| 5%       | inclusive | Hotels   | Spain   |
| 2%       | inclusive | Hotels   | France  |

If an order had 2 line items, one from Clothing  category and the other from Food category, the tax rates that should be selected:

| Tax Rate | Type      | Category | Zone    |
|----------|-----------|----------|---------|
| 21%      | inclusive | Clothing | Spain   |
| 10%      | inclusive | Food     | Spain   |

If the order's address changes to one in France, then the tax will be recalculated:

| Tax Rate | Type      | Category | Zone    |
|----------|-----------|----------|---------|
| 18%      | inclusive | Clothing | France  |
| 8%       | inclusive | Food     | France  |