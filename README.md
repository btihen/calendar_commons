# README

This README would normally document whatever steps are necessary to get the
application up and running.

Rails 6 Plus Devise and Rspec
```bash
rails new -T calendar_commons
cd calendar_commons/
# add mit license
touch LICENSE
cat <<"EOF" >LICENSE
MIT License

Copyright (c) 2020 Bill Tihen

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
EOF
# udpate gems
cat <<"EOF" >> Gemfile
#################
# MY ADDED GEMS #
#################

# BACK END
##########
# gem 'devise', '~> 4.6'
gem 'devise' # , '~> 4.7'  # rails 6.0 requires 4.7.0 or greater
# gem 'devise', git: 'https://github.com/plataformatec/devise'
# gem 'devise', git: 'https://github.com/plataformatec/devise/master'
# rails generate devise:install
# https://github.com/plataformatec/devise
# in config/environments/development.rb:
# config.action_mailer.default_url_options = { host: 'localhost', port: 3000 }
# rails generate devise MODEL
# rails generate devise:views

# for time expiring passwords (prevent repeat passwords - etc)
# gem 'devise-secure_password', '~> 1.0.5'
# rails generate devise:secure_password:install
# edit: config/initializers/secure_password.rb

# https://github.com/hexorx/countries
# also provides lat & long info
# c    = ISO3166::Country.find_country_by_alpha2('ch')
# c    = ISO3166::Country.find_country_by_alpha3('can')
# list = ISO3166::Country.find_all_countries_by_region('Americas')
# require: 'countries/global' - obviates the need to call ISO3166::Country,
#           simply call Country
# gem 'countries'  # , require: 'countries/global'

# # easy pg fulltext searches - easier than building indexed views - but slower - ok for now
# gem 'pg_search'

# # initiative state machine
# gem 'aasm'

# model dashboard
# gem 'administrate'
# bundle install
# rails generate administrate:install

# validates date and time
# gem 'validates_timeliness', '~> 4.0'
# rails generate validates_timeliness:install

# declarative interfaces in controllers
# gem 'decent_exposure', '3.0.0'

# FRONT END
###########
# simple country dropdowns
# gem 'country_select' #, '~> 3.1'

# # Serialize object - for js
# gem 'active_model_serializers'

# # Transpile app-like JavaScript. Read more: https://github.com/rails/webpacker
# # waiting on react-rails to support webpacker 4
# gem 'webpacker', '~> 4.0'

# #React component support
# # gem 'react_on_rails', '11.1.4'
# gem 'react_on_rails'

# # See https://github.com/rails/execjs
# # readme for more supported runtimes
# gem 'mini_racer', platforms: :ruby

# # PRODUCTION
# gem 'rollbar'

# DEV / TESTS
#############
group :development, :test do
  # debugging
  gem 'pry-rails'
  gem 'pry-byebug'
  gem 'pry-stack_explorer'

  gem 'factory_bot_rails'
  gem 'faker'

  gem 'rspec-rails'
  # rails generate rspec:install

  # use requests instead
  # gem 'rails-controller-testing'
end

group :test do
  # FEATURE TESTS
  # gem 'cucumber-rails', require: false
  # # rails generate cucumber:install
  # # https://github.com/cucumber/cucumber/wiki/RSpec-Expectations
  # # use rspec - expectations in cucumber
  # gem 'rspec-expectations'
  # # database_cleaner is not required, but highly recommended
  # gem 'database_cleaner'
  # allow cucumber to do JavaScript testing too
  gem 'selenium-webdriver'
  # https://mikecoutermarsh.com/rails-capybara-selenium-chrome-driver-setup/
  # download chromedriver from: http://chromedriver.chromium.org/
  # or use brew cask install chromedriver
  # finally in features/env.rb - switch the browser to :chrome
  # gem 'chromedriver-helper'
  gem 'webdrivers' # , '~> 3.0'

  # easier tests (inside rspec)
  gem 'shoulda-matchers' # , '~> 3.1'

  # cucumber can test emails (rspec too?)
  gem 'email_spec'

  # code coverage
  gem 'simplecov'
  gem 'simplecov-console'
end

group :development do
  # security check gems
  # https://www.occamslabs.com/blog/securing-your-ruby-and-rails-codebase
  # http://fretless.com/blog/static-security-analysis-of-your-ruby-and-rails-applications/
  gem 'brakeman', require: false
  # brakeman
  # or the opensource version
  # gem 'railroader', :require => false
  # railroader

  # code smells & churn
  gem 'rubycritic', require: false
  # rubycritic app

  gem 'bundler-audit', require: false
  # bundle audit check --update

  # also useful for sinatra, etc. (checks CVE-2013-6421 records)
  gem 'dawnscanner', :require=>false
  # bundle install
  # dawn --console .

  # rubocop (security checks with: )
  gem 'rubocop', require: false
  # security only and excludes junk folders too!
  # rubocop -c .rubocop_security.yml
  # quick and simple security checks
  # rubocop --only Security
  # cat <<EOF >.rubocop_security.yml
  # AllCops:
  #   DisabledByDefault: true
  #   Exclude:
  #     - 'db/**/*'
  #     - 'specs/**/*'
  #     - 'config/**/*'
  #     - 'features/**/*'
  #     - 'lib/tasks/**/*'
  #     - 'app/views/**/*'
  #     - 'bin/{rails,rake}'
  #     - 'node_modules/**/*'
  #     - !ruby/regexp /old_and_unused\.rb$/
  # Bundler/InsecureProtocolSource:
  #   Enabled: true
  # Security/Eval:
  #   Enabled: true
  # Security/JSONLoad:
  #   Enabled: true
  # Security/MarshalLoad:
  #   Enabled: true
  # Security/Open:
  #   Enabled: true
  # Security/YAMLLoad:
  #   Enabled: true
  # EOF

  # # starUML for uml diagram and RailsERD for Entity Diagram
  # # https://voormedia.github.io/rails-erd/install.html
  # # brew install graphviz
  # gem 'rails-erd'
  # # rake erd
  #
  # # capture emails in the web browser
  # gem 'letter_opener'
end
EOF
code . -n
bundle update
rails generate rspec:install
rails g controller Landing index
rails generate devise:install
rails generate devise User
rails generate devise:views
rails g migration AddUserInfoToUsers first_name last_name user_title user_role
rails db:create
rails db:migrate
rails generate devise:views
# test that landing page shows up
rails s
# if all is ok commit
git add .
git commit -am "initial commit with Devise and rspec other gems - no CSS / JS Framework yet"
git remote add origin git@github.com:btihen/calendar_commons.git
git push -u origin master
git pull
```

Add Bulma from: http://blog.blackninjadojo.com/css/bulma/2019/02/27/how-to-create-a-layout-for-your-rails-application-using-bulma.html
Add Bulma Template from: https://jenil.github.io/bulmaswatch/
```bash
yarn add bulma
# fix: gyp: No Xcode or CLT version detected!
# https://cleody.com/fix-no-xcode-or-clt-version-detected-when-running-npm-install/
sudo rm -r -f /Library/Developer/CommandLineTools
xcode-select --install
# now retry
yarn add bulma
rm app/assets/stylesheets/application.css
touch app/assets/stylesheets/application.scss
cat <<"EOF">> app/assets/stylesheets/application.scss
@charset "utf-8";

// import fonts
@import url('https://fonts.googleapis.com/css?family=Source+Code+Pro|Roboto+Slab|Open+Sans');
@import url('https://fonts.googleapis.com/css?family=Ubuntu');

// add bulma variables to compile
$family-sans-serif: 'Open Sans', Helvetica, Arial, sans-serif;
$family-monospace: 'Source Code Pro', monospace;
$family-primary:'Ubuntu', sans-serif;

$subtitle-line-height: 1.5;

// import bulma and optionally the extensions
@import 'bulma/bulma';

// Import css layouts
@import '_layout';
EOF

touch app/assets/stylesheets/_layout.scss
cat <<"EOF">> app/assets/stylesheets/_layout.scss
body {
  display:flex;
  flex-direction:column;
  justify-content:space-between;
  height:100vh;
}
.header {
  padding:2rem 1.5rem;
}
.section {
  display:flex;
  flex:1 0 auto;
}
.weekday {
  text-align: center;
  background-color: #f5f5f5;
}
.calendar-day{
  border-style: solid;
  border-width: 1px;
  border-color: #cccccc;
}
EOF

# narbar:
# https://bulma.io/documentation/components/navbar/
cat <<"EOF" > app/views/layouts/application.html.erb
<!DOCTYPE html>
<html>
  <head>
    <title>CalendarCommons</title>
    <%= csrf_meta_tags %>
    <%= csp_meta_tag %>

    <%= stylesheet_link_tag 'application', media: 'all', 'data-turbolinks-track': 'reload' %>
    <%= javascript_pack_tag 'application', 'data-turbolinks-track': 'reload' %>

    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link rel="stylesheet" href="https://unpkg.com/bulmaswatch/litera/bulmaswatch.min.css">
    <link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.6.3/css/all.css" integrity="sha384-UHRtZLI+pbxtHCWp1t77Bi1L4ZtiqrqD80Kn4Z8NTSRyMA2Fd33n5dQ8lWUE00s/" crossorigin="anonymous">
  </head>

  <body>
    <p class="notice"><%= notice %></p>
    <p class="alert"><%= alert %></p>

    <nav class="navbar is-light" role="navigation" aria-label="main navigation">
      <div class="navbar-brand">
        <a class="navbar-item" href="/">
          <h1 id="title" class="navbar-item">
            CalComs
          </h1>
        </a>

        <a role="button" class="navbar-burger burger" aria-label="menu" aria-expanded="false" data-target="navbarBasicExample">
          <span aria-hidden="true"></span>
          <span aria-hidden="true"></span>
          <span aria-hidden="true"></span>
        </a>
      </div>

      <div id="navbarBasicExample" class="navbar-menu">
        <div class="navbar-start">
          <a class="navbar-item">
            Home
          </a>

          <a class="navbar-item">
            Documentation
          </a>

          <div class="navbar-item has-dropdown is-hoverable">
            <a class="navbar-link">
              More
            </a>

            <div class="navbar-dropdown">
              <a class="navbar-item">
                About
              </a>
              <a class="navbar-item">
                Jobs
              </a>
              <a class="navbar-item">
                Contact
              </a>
              <hr class="navbar-divider">
              <a class="navbar-item">
                Report an issue
              </a>
            </div>
          </div>
        </div>

        <div class="navbar-end">
          <div class="navbar-item">
            <div class="buttons">
              <a class="button is-primary">
                <strong>Sign up</strong>
              </a>
              <a class="button is-light">
                Log in
              </a>
            </div>
          </div>
        </div>
      </div>
    </nav>

    <section class="section">
      <div class="container is-fluid">
        <p class="notice"><%= notice %></p>
        <p class="alert"><%= alert %></p>
        <%= yield %>
      </div>
    </section>

    <footer class="footer is-light">
      <div class="container">
        Copyright © 2019 CalendarCommons. All rights reserved.
      </div>
    </footer>

    <script type="text/javascript">
      document.addEventListener('DOMContentLoaded', () => {

        // Get all "navbar-burger" elements
        const $navbarBurgers = Array.prototype.slice.call(document.querySelectorAll('.navbar-burger'), 0);

        // Check if there are any navbar burgers
        if ($navbarBurgers.length > 0) {

          // Add a click event on each of them
          $navbarBurgers.forEach( el => {
            el.addEventListener('click', () => {

              // Get the target from the "data-target" attribute
              const target = el.dataset.target;
              const $target = document.getElementById(target);

              // Toggle the "is-active" class on both the "navbar-burger" and the "navbar-menu"
              el.classList.toggle('is-active');
              $target.classList.toggle('is-active');

            });
          });
        }

      });
    </script>
  </body>
</html>
EOF
```


Add Bulma Extensions
```bash
yarn add bulma-extensions
```
