source 'https://rubygems.org'
git_source(:github) { |repo| "https://github.com/#{repo}.git" }

ruby '2.6.5'

# Bundle edge Rails instead: gem 'rails', github: 'rails/rails'
gem 'rails', '~> 6.0.2', '>= 6.0.2.1'
# Use postgresql as the database for Active Record
gem 'pg', '>= 0.18', '< 2.0'
# Use Puma as the app server
gem 'puma', '~> 4.3'
# Use SCSS for stylesheets
gem 'sass-rails', '>= 6'
# Transpile app-like JavaScript. Read more: https://github.com/rails/webpacker
gem 'webpacker', '~> 4.0'
# Turbolinks makes navigating your web application faster. Read more: https://github.com/turbolinks/turbolinks
gem 'turbolinks', '~> 5'
# Build JSON APIs with ease. Read more: https://github.com/rails/jbuilder
gem 'jbuilder', '~> 2.7'
# Use Redis adapter to run Action Cable in production
# gem 'redis', '~> 4.0'
# Use Active Model has_secure_password
# gem 'bcrypt', '~> 3.1.7'

# Use Active Storage variant
# gem 'image_processing', '~> 1.2'

# Reduces boot times through caching; required in config/boot.rb
gem 'bootsnap', '>= 1.4.2', require: false

group :development, :test do
  # Call 'byebug' anywhere in the code to stop execution and get a debugger console
  gem 'byebug', platforms: [:mri, :mingw, :x64_mingw]
end

group :development do
  # Access an interactive console on exception pages or by calling 'console' anywhere in the code.
  gem 'web-console', '>= 3.3.0'
  gem 'listen', '>= 3.0.5', '< 3.2'
  # Spring speeds up development by keeping your application running in the background. Read more: https://github.com/rails/spring
  gem 'spring'
  gem 'spring-watcher-listen', '~> 2.0.0'
end

# Windows does not include zoneinfo files, so bundle the tzinfo-data gem
gem 'tzinfo-data', platforms: [:mingw, :mswin, :x64_mingw, :jruby]


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
