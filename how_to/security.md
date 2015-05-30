# Security Configuration

## SSL
* By default Spree uses SSL only in production and staging
* Can be enabled/disabled under (Configuration -> General Settings -> Security Settings)

>- Production: referred to as "live" - real data, real users, real transactions
- Staging: similar to a final rehearsal - real data, possibly real users, fake transactions
- Testing: it is how the programmer tests functionality in an automated way before the
application meets any user

* Spree uses Rails built in
[ForceSSL](http://api.rubyonrails.org/classes/ActionController/ForceSSL/ClassMethods.html).
* It's recommended to `enable config.force_ssl = true` in production.rb to enforce SSL on every 
page. Otherwise use it on the controller level

## Alerts
* Spree periodically sends security and release announcements and you will see
them on the Admin Interface pages
* Can be disabled under (Configuration -> General Settings -> Security Settings) or setting
`Spree::Config[:check_for_alerts]` to `false`
* Some configuration information is included when checking so alerts can be customized. This is an
 example of the configuration information included in the alert request:

```json
{
  "name": "Spree Demo Site",
  "rails_version": "3.1.1",
  "version": "0.70.1",
  "rails_env": "production",
  "host": "www.spreecommerce.com"
}
```
