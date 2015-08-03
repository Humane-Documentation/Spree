## [Spree::User](https://github.com/spree/spree_auth_devise/tree/master/app/models/spree/user.rb)

> IMPORTANT: This model exists in Spree in two ways:
* Under Spree Core with class name `Spree.user_class.to_s`
* Under [spree_auth_devise](https://github.com/spree/spree_auth_devise) gem as `Spree::User`
Most of the time you'll use the one under core, e.g.
```
belongs_to :user, :class_name => Spree.user_class.to_s
```

### Attributes
* `encrypted_password`
* `password_salt`
* `email`
* `remember_token`
* `persistence_token`
* `reset_password_token`
* `perishable_token`
* `sign_in_count`
* `failed_attempts`
* `last_request_at`
* `current_sign_in_at`
* `last_sign_in_at`
* `current_sign_in_ip`
* `last_sign_in_ip`
* `login`
* `ship_address_id`
* `bill_address_id`
* `authentication_token`
* `unlock_token`
* `locked_at`
* `reset_password_sent_at`
* `spree_api_key`
* `remember_created_at`
* `deleted_at`
* `confirmation_token`
* `confirmed_at`
* `confirmation_sent_at`

### Related Attributes `tokenized_permissions`
* `permissable_id`
* `permissable_type`
* `token`
