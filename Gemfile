source 'http://ruby.taobao.org'

gem 'rails', '3.2.12'

# Bundle edge Rails instead:
# gem 'rails', :git => 'git://github.com/rails/rails.git'
#将 rspec-rails 放在了开发组中，使用 RSpec 相关的生成器了
group :development, :test do 
  gem 'sqlite3'
  gem 'rspec-rails','2.11.0'
end 


# Gems used only for assets and not required
# in production environments by default.
group :assets do
  gem 'sass-rails',   '~> 3.2.3'
  gem 'coffee-rails', '~> 3.2.1'

  # See https://github.com/sstephenson/execjs#readme for more supported runtimes
  # gem 'therubyracer', :platforms => :ruby

  gem 'uglifier', '>= 1.0.3'
end

gem 'jquery-rails'

#capybara 允许我们使用类似英语中的句法编写与应用程序交互的代码
group :test do 
  gem 'capybara'
end 

#把PostgreSQL 所需的 gem 加入生产组，这样才能部署到 Heroku
group :production  do 
  gem 'pg', '>=0.12.2'
end 

# To use ActiveModel has_secure_password
# gem 'bcrypt-ruby', '~> 3.0.0'

# To use Jbuilder templates for JSON
# gem 'jbuilder'

# Use unicorn as the app server
# gem 'unicorn'

# Deploy with Capistrano
# gem 'capistrano'

# To use debugger
# gem 'debugger'
