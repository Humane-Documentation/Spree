# Installation
## Alternatives
### Build a Sample Application
Spree includes a helpful Rake task for setting up a *sandbox* application:
* Clone the Git repo
```bash
git clone git://github.com/spree/spree.git
cd spree
```
> It's a good idea to use a new "*gem environment*" so Spree gems wouldn't fight with your existing dependencies. This can be done with [RVM Gemsets](https://rvm.io/gemsets/creating)
* Install the gem dependencies
```bash
bundle install
```
* Create a sandbox application for testing purposes (and automatically perform all necessary database setup)
```bash
bundle exec rake sandbox
```
* Start the server
```bash
cd sandbox && rails server
```

This creates a bare-bones application configured with Spree gem. It runs the DB migrations  and sets
up the sample data. Resulting `sandbox` folder is ignored by `.gitignore` and is  deleted and
rebuilt from scratch each time the Rake task runs.

### Use in an Existing Application
* To use a stable branch of Spree, add this line to your Gemfile
```ruby
gem 'spree', github: 'spree/spree', branch: '3-0-stable'
```
* To use the bleeding edge version of Spree:
```ruby
gem 'spree', github: 'spree/spree'
```
* Install these gems using this command:
```bash
bundle install --auto-accept
```
* Use the install generator to set up Spree:
```bash
rails g spree:install --sample=false --seed=false
```
* You can avoid running DB migrations and or generating seed and sample data by passing these flags:
```bash
rails g spree:install --migrate=false --sample=false --seed=false
```
* To perform those on your own:
```bash
bundle exec rake railties:install:migrations
bundle exec rake db:migrate
bundle exec rake db:seed
bundle exec rake spree_sample:load
```

#### To Browse Store
[http://localhost:3000](http://localhost:3000)

#### To Browse Admin Interface
[http://localhost:3000/admin](http://localhost:3000/admin)

Username `spree@example.com`   
Password `spree123`

> If you elected not to use the `--auto-accept` option when you added Spree to your Rails app, and
did not install the seed data, the admin user will not yet exist in your database. To create a new admin user run this rake task:
```bash
rake spree_auth:admin:create
```

## Performance in Development Mode
In development mode, Rails continuously reloads objects on each request. Its asset pipeline made
things even slower. To speed up performance in development mode **when NOT working on front end issues**:
* In your `config/environments/development.rb`, add:
```ruby
config.assets.debug = false
```
* Precompile your assets:
```ruby
RAILS_ENV=development bundle exec rake assets:precompile
```

> To remove precompiled assets at anytime (**especially** before committing to Git etc.):
```ruby
RAILS_ENV=development bundle exec rake assets:clean
```