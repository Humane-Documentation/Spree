# Payments

## Components

### Payment (Model)
See [here](../models/Payment.md)

### Payment Method (Model)
See [here](../models/PaymentMethod.md)

### Gateway (Model)
See [here](../models/Gateway.md)

### Merchant Account (TMI)
* A bank account that allows accepting credit card payments
* An Internet merchant account allows accepting payments online without having the customer's
credit card physically in front of you

## Credit Card Data
* In production mode, credit card data is transmitted only once and via SSL
* Data is immediately submitted to your payment gateway and then discarded before saving the model
* Only name, type, expiration and last four digits are saved and only for verification
* Other data is never stored in the database, not even temporarily. It exists in memory on the
server for a fraction of a second before it's discarded

## Authorize vs Capture
* *Authorize*: Confirming availability of funds for a transaction with purchaser's card company
* Spree By default handles authorizing the payment for a transaction
* *Capturing*: Telling the card company you want to get paid for a transaction amount
* Spree gives choice of auto-capturing payments or manually capturing them via the Admin Interface
* Typically, this two step process of authorizing and then capturing a payment is used by online
retailers to delay charging the customer until the purchase is fulfilled (shipped)
* Not all gateways allow the two step process. Confirm with your payment gateway and doctor too

### CC Processing Options
#### Option 1: With Payment Profiles (Default)
##### Payment Profiles
* Service provided by some payment gateways
* Default checkout process in Spree assumes a gateway that allows for third party support for
payment profiles

##### Process
* Credit card gateway stores the credit card information
* Your application stores only a token that can be used to authorize future charges on that same
card without having to actually store it
* "token" is tied with your merchant account

##### Benefits
* Secure and PCI compliant means of storing the users credit card information
* Users can make subsequent purchases without having to reenter their card info
* Merchants can issue refunds to the credit card
* Merchants can make changes to an existing order without having to leave Spree and use the
gateway provider's website
* Ability to show a "confirmation" step after payment information is entered before an order is
processed since card number is now stored and can be used to perform standard authorization/capture
via the secure token provided by the gateway

#### Option 2: Without Payment Profiles
If you do not want to use Payment Profiles then you need to customize checkout since Spree
discards CC info after [Payment step](checkout.md#Payment) and so card info will be lost
before it's time to authorize it. In detail:
* Customize checkout so card info is entered and submitted on the final step
* Perform the authorization before the order is saved
* Remove any final "review and confirm" step

This is secure since CC information is transmitted to the gateway and then discarded

### Customization: Payment Profiles
* All `Gateway` classes have a `payment_profiles_supported?` method which indicates whether or
not payment profiles are supported
* If you are adding Spree support to a `Gateway` you should also implement the `create_profile`
method. The following is an example:
```
# Create a new CIM customer profile ready to accept a payment
def create_profile(payment)
  if payment.source.gateway_customer_profile_id.nil?
    profile_hash = create_customer_profile(payment)
    payment.source.update_attributes({
      :gateway_customer_profile_id => profile_hash[:customer_profile_id],
      :gateway_payment_profile_id => profile_hash[:customer_payment_profile_id])
    })
  end
end
```

### Processing Walk-through (UI)
* Receiving an order, an admin needs to process its payment (this guide focuses on processing
credit card payments). An order is ready for processing if
  * Order State is "Complete", meaning all information customer needs to provide is present
  * Payment State is "Balance Due", meaning there is an unpaid balance on the order
  * Shipment State is "Pending", because you can't ship an order before you collect payment on it
* Click "Balance Due" to open the order's payment info page. Clicking "Capture" starts payment
processing
* If payment is processed successfully the page will show you that payment state has progressed
from "Pending" to "Completed"

### Processing Walk-through (Code)
* When an order is complete, each associated `Payment` object will have `process!` method called
on it to fulfill the order's balance (unless `payment_required?` returned `false`)
* If the payment method requires a source and the payment has one then processing starts or
otherwise the payment needs manual processing
* How a payment is processed next depends on `PaymentMethod` sub-class' implementation of
`purchase` and `authorize` methods
* If `PaymentMethod` is configured to *auto-capture* then:
 * `Payment#purchase!` method is called which then calls `PaymentMethod#purchase`:
`payment_method.purchase(<amount>, <source>, <gateway options>)`
 * If it's successful, payment is marked `completed`. If not, it's is marked `failed`
* If `PaymentMethod` is NOT configured to *auto-capture* then:
  * `Payment#authorize!` method is called which then calls `PaymentMethod#authorize`:
`payment_method.authorize(<amount>, <source>, <gateway options>)`
  * If it's successful, payment transitions to `pending` so it's manually captured later by calling
  `capture!` method. If not, payment is marked `failed`
* Returned objects from `purchase` or `authorize` are `ActiveMerchant::Billing::Response`
objects to be stored in `spree_log_entries` table as a YAML log entry for the payment
* Once a payment is saved, it updates the order which may change `payment_state` to any of these:
  * `balance_due`: Payment is required for this order
  * `failed`: Last payment for this order failed
  * `credit_owed`: This order has been paid for in excess of its total
  * `paid`: Order has been paid for in full

> Increase in `payment_state` of `failed` could be a problem with the gateway. check `log_entries`

### Log Entries
Payment Log entries can be retrieved with a call to `log_entries` association on any `Payment` object.
To get `Active::Merchant::Billing::Response` out of `LogEntry` objects, call the `details` method.

## Voiding a Payment
Done from the Admin Interface
