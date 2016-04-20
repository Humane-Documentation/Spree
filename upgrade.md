# Upgrade

> Spree core files are encapsulated in away in gems so upgrading to newer files will not
touch any customized files (e.g. [sandbox application](installation#build-a-sample-application) project files).

* Ensure the installed spree gem is up-to-date by modifying `Gemfile` to match the new
spree version
* Run 
```bash
bundle update spree`
```
* Copy all DB migrations from Spree (and any other engine) and run them:
```bash
    rake railties:install:migrations
    rake db:migrate
```
* If you have extensions, you will need to manually verify that each works once an upgrade is
complete. Typically, compatible extensions will have a branch matching the upgrade version
* Manually test your store
