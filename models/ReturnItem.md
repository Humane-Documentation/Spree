[Index](../_index.md) » ReturnItem

# (Class) [Spree::ReturnItem](http://m.gymplayer.com/return_item.rb)

### Attributes
* `return_authorization_id`
* `inventory_unit_id`
* `exchange_variant_id`
* `pre_tax_amount`
* `included_tax_total`
* `additional_tax_total`
* `reception_status`
* `acceptance_status`
* `customer_return_id`
* `reimbursement_id`
* `exchange_inventory_unit_id`
* `acceptance_status_errors`
* `preferred_reimbursement_type_id`
* `override_reimbursement_type_id`
* `resellable`

## Modules
* [ExchangeVariantEligibility](ReturnItem/ExchangeVariantEligibility.md)

## Constants
COMPLETED_RECEPTION_STATUSES =%w(received given_to_customer)

## Methods included from
* [DisplayMoney](DisplayMoney.md)

## Class Methods
### (Object) **from_inventory_unit**(inventory_unit)
    

## Instance Methods
### (Object) **build_exchange_inventory_unit**
    

### (Object) **eligible_exchange_variants**


###  (Boolean) **exchange_processed?**


###  (Boolean) **exchange_requested?**


###  (Boolean) **exchange_required?**


### (Object) **exchange_shipment**


###  (Boolean) **reception_completed?**


### (Object) **set_default_pre_tax_amount**


### (Object) **total**

