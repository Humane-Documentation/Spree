# Email Configuration

> Spree mail settings has been extracted out into a gem in favor of generic action mailer settings.
Please add [spree_mail_settings](https://github.com/spree-contrib/spree_mail_settings)
to your Gemfile before proceeding if you desire this

The configurable components of your Spree site are managed in the Mail Method Settings panel. You
can reach this by going to the Admin Interface (Configuration -> Mail Method Settings)

### Enable Mail Delivery
* Causes all confirmation and notification emails Spree shopping cart system generates to be sent
* Disable this if you want to develop/test without sending bogus emails

### Send Mails As
Set this to the email to be used as the "From" line on the store auto-generated emails

### Send Copy of All Mails To
Help track all emails your store sends

### Intercept Email Address
Causes any notification emails to be re-routed to the email address you declare

### SMTP Settings
GUI to store's server SMTP settings

### HTML Email Templates
The HTML email templates use [Zurb Ink](http://zurb.com/ink/templates.php)
and [Premailer-Rails](https://github.com/fphilipe/premailer-rails) for responsive styling
