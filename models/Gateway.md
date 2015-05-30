# Gateway (Model)
Service that authorizes credit card payments, processes them securely, and deposits the funds 
into retailer's bank account

### Attributes
* `type`
* `name`
* `description`
* `active` 
* `environment`: defaults to development
* `server`: defaults to "test"
* `test_mode`
* `preferences`

### Gateway Options
* `email` and `customer`: email address related to the order
* `ip`: Last IP address for the order
* `order_id`: Order's `number` attribute, plus the `identifier` for each payment
* `shipping`: total shipping cost for the order, in cents
* `tax`: total tax cost for the order, in cents
* `subtotal`: items total for the order, in cents
* `currency`: 3-character currency code for the order
* `discount`: promotional discount applied to the order
* `billing_address`: A hash containing billing address information
* `shipping_address`: A hash containing shipping address information

##### Billing & Shipping Addresses Fields:
* `name`: The combined `first_name` and `last_name` from the address
* `address1`: first line
* `address2`: second line
* `city`
* `state`: abbreviated state name, if not, complete name from related `State` object. If not,
`state_name` attribute from the address
* `country`: ISO name, e.g. "US", "AU"
* `phone`

## Supported Gateways
* Payment processing attempts to comply with `active_merchant` gem API where possible
* See [spree_gateway](https://github.com/spree/spree_gateway) extension

## Adding a gateway (Customization)
For a custom gateway to show up on the backend you need to add it to the config list of payment
methods by adding the following in spree.rb for example:
```
Rails.application.config.spree.payment_methods << YourCustomGateway
```

## Typical Fees (TMI)
* *Setup Fee* - A one-time charge to set up a payment gateway account
* *Recurring Fixed Monthly Fees* - fixed monthly fee gateway provider charges for access to 
their services and reports. Some gateways break this charge down further into a monthly
Gateway Fee and a Statement Fee
* *Transaction Fees* - A charge for each purchase made on your store. Pricing structure for 
these differ but a popular structure is to charge a percentage of the purchase price plus a flat fee
