
# Post \#70800753 [Link](https://stackoverflow.com/questions/70800753/)

## RAILS Calling `DidYouMean::SPELL_CHECKERS.merge!(error_name => spell_checker)' has been deprecated

**Vote**: 16 (306/702) **Views**: 11158 (404/702) 

**Internal ID** \#2-9-474

Created at 2022-01-21 11:46:30

Tags: `ruby-on-rails` `ruby` `rubygems`

----------

#### Metadata:

Area: `Back-end`

Language: `ruby` (full parsed tag list: `ruby`)

----------

**Notepad**


----------

Good morning people.
I'm trying to understand the error below but as I'm new to rails, I didn't quite understand. Does anyone have a light on what it could be?
I searched the internet but didn't find anything specific.
I searched on the internet but didn't identify anything, if anyone has seen it or has the link, you can send me and I'll see.
If you need any more information to help, let me know and I'll edit the post and add it, I don't know if there's anything else I could have already posted.
thank you for your help !!
```
➜ make up  
docker-compose up
Starting XXXXXX_postgres    ... done
Starting XXXXXX_mailcatcher ... done
Starting XXXXXX_rails       ... done
Attaching to XXXXXX_mailcatcher, XXXXXX_postgres, XXXXXX_rails
XXXXXX_mailcatcher    | Starting MailCatcher
XXXXXX_mailcatcher    | ==> smtp://0.0.0.0:1025
XXXXXX_postgres       | 
XXXXXX_postgres       | PostgreSQL Database directory appears to contain a database; Skipping initialization
XXXXXX_postgres       | 
XXXXXX_mailcatcher    | /usr/local/bundle/gems/thin-1.5.1/lib/thin/server.rb:104: warning: constant ::Fixnum is deprecated
XXXXXX_postgres       | 2022-01-21 11:02:46.949 UTC [1] LOG:  starting PostgreSQL 12.8 (Debian 12.8-1.pgdg110+1) on x86_64-pc-linux-gnu, compiled by gcc (Debian 10.2.1-6) 10.2.1 20210110, 64-bit
XXXXXX_mailcatcher    | ==> http://0.0.0.0:1080
XXXXXX_postgres       | 2022-01-21 11:02:46.949 UTC [1] LOG:  listening on IPv4 address "0.0.0.0", port 5432
XXXXXX_postgres       | 2022-01-21 11:02:46.949 UTC [1] LOG:  listening on IPv6 address "::", port 5432
XXXXXX_postgres       | 2022-01-21 11:02:46.954 UTC [1] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
XXXXXX_postgres       | 2022-01-21 11:02:46.967 UTC [26] LOG:  database system was shut down at 2022-01-21 11:02:42 UTC
XXXXXX_postgres       | 2022-01-21 11:02:46.973 UTC [1] LOG:  database system is ready to accept connections
XXXXXX_rails          | /usr/local/bundle/gems/bundler-2.1.4/lib/bundler/vendor/thor/lib/thor/error.rb:105: warning: constant DidYouMean::SPELL_CHECKERS is deprecated
XXXXXX_rails          | Calling `DidYouMean::SPELL_CHECKERS.merge!(error_name => spell_checker)' has been deprecated. Please call `DidYouMean.correct_error(error_name, spell_checker)' instead.
XXXXXX_rails          | Traceback (most recent call last):
XXXXXX_rails          |  52: from bin/rails:2:in `<main>'
XXXXXX_rails          |  51: from bin/rails:2:in `load'
XXXXXX_rails          |  50: from /app/bin/spring:7:in `<top (required)>'
XXXXXX_rails          |  49: from /app/bin/spring:7:in `tap'
XXXXXX_rails          |  48: from /app/bin/spring:10:in `block in <top (required)>'
XXXXXX_rails          |  47: from /usr/local/lib/ruby/site_ruby/2.7.0/rubygems/core_ext/kernel_require.rb:85:in `require'
XXXXXX_rails          |  46: from /usr/local/lib/ruby/site_ruby/2.7.0/rubygems/core_ext/kernel_require.rb:85:in `require'
XXXXXX_rails          |  45: from /usr/local/bundle/gems/spring-3.0.0/lib/spring/binstub.rb:11:in `<top (required)>'
XXXXXX_rails          |  44: from /usr/local/bundle/gems/spring-3.0.0/lib/spring/binstub.rb:11:in `load'
XXXXXX_rails          |  43: from /usr/local/bundle/gems/spring-3.0.0/bin/spring:49:in `<top (required)>'
XXXXXX_rails          |  42: from /usr/local/bundle/gems/spring-3.0.0/lib/spring/client.rb:30:in `run'
XXXXXX_rails          |  41: from /usr/local/bundle/gems/spring-3.0.0/lib/spring/client/command.rb:7:in `call'
XXXXXX_rails          |  40: from /usr/local/bundle/gems/spring-3.0.0/lib/spring/client/rails.rb:28:in `call'
XXXXXX_rails          |  39: from /usr/local/bundle/gems/spring-3.0.0/lib/spring/client/rails.rb:28:in `load'
XXXXXX_rails          |  38: from /app/bin/rails:4:in `<top (required)>'
XXXXXX_rails          |  37: from /app/bin/rails:4:in `require_relative'
XXXXXX_rails          |  36: from /app/config/boot.rb:4:in `<top (required)>'
XXXXXX_rails          |  35: from /app/config/boot.rb:4:in `require'
XXXXXX_rails          |  34: from /usr/local/bundle/gems/bootsnap-1.9.1/lib/bootsnap/setup.rb:4:in `<top (required)>'
XXXXXX_rails          |  33: from /usr/local/bundle/gems/bootsnap-1.9.1/lib/bootsnap.rb:112:in `default_setup'
XXXXXX_rails          |  32: from /usr/local/bundle/gems/bootsnap-1.9.1/lib/bootsnap.rb:70:in `setup'
XXXXXX_rails          |  31: from /usr/local/bundle/gems/bootsnap-1.9.1/lib/bootsnap/compile_cache.rb:20:in `setup'
XXXXXX_rails          |  30: from /usr/local/bundle/gems/bootsnap-1.9.1/lib/bootsnap/compile_cache/yaml.rb:50:in `install!'
XXXXXX_rails          |  29: from /usr/local/bundle/gems/bootsnap-1.9.1/lib/bootsnap/compile_cache/yaml.rb:55:in `init!'
XXXXXX_rails          |  28: from /usr/local/bundle/gems/bootsnap-1.9.1/lib/bootsnap/load_path_cache/core_ext/kernel_require.rb:31:in `require'
XXXXXX_rails          |  27: from /usr/local/bundle/gems/bootsnap-1.9.1/lib/bootsnap/load_path_cache/core_ext/kernel_require.rb:22:in `require_with_bootsnap_lfi'
XXXXXX_rails          |  26: from /usr/local/bundle/gems/bootsnap-1.9.1/lib/bootsnap/load_path_cache/loaded_features_index.rb:92:in `register'
XXXXXX_rails          |  25: from /usr/local/bundle/gems/bootsnap-1.9.1/lib/bootsnap/load_path_cache/core_ext/kernel_require.rb:23:in `block in require_with_bootsnap_lfi'
XXXXXX_rails          |  24: from /usr/local/bundle/gems/bootsnap-1.9.1/lib/bootsnap/load_path_cache/core_ext/kernel_require.rb:23:in `require'
XXXXXX_rails          |  23: from /usr/local/lib/ruby/2.7.0/yaml.rb:4:in `<main>'
XXXXXX_rails          |  22: from /usr/local/bundle/gems/bootsnap-1.9.1/lib/bootsnap/load_path_cache/core_ext/kernel_require.rb:31:in `require'
XXXXXX_rails          |  21: from /usr/local/bundle/gems/bootsnap-1.9.1/lib/bootsnap/load_path_cache/core_ext/kernel_require.rb:22:in `require_with_bootsnap_lfi'
XXXXXX_rails          |  20: from /usr/local/bundle/gems/bootsnap-1.9.1/lib/bootsnap/load_path_cache/loaded_features_index.rb:92:in `register'
XXXXXX_rails          |  19: from /usr/local/bundle/gems/bootsnap-1.9.1/lib/bootsnap/load_path_cache/core_ext/kernel_require.rb:23:in `block in require_with_bootsnap_lfi'
XXXXXX_rails          |  18: from /usr/local/bundle/gems/bootsnap-1.9.1/lib/bootsnap/load_path_cache/core_ext/kernel_require.rb:23:in `require'
XXXXXX_rails          |  17: from /usr/local/lib/ruby/2.7.0/psych.rb:15:in `<main>'
XXXXXX_rails          |  16: from /usr/local/bundle/gems/bootsnap-1.9.1/lib/bootsnap/load_path_cache/core_ext/kernel_require.rb:31:in `require'
XXXXXX_rails          |  15: from /usr/local/bundle/gems/bootsnap-1.9.1/lib/bootsnap/load_path_cache/core_ext/kernel_require.rb:22:in `require_with_bootsnap_lfi'
XXXXXX_rails          |  14: from /usr/local/bundle/gems/bootsnap-1.9.1/lib/bootsnap/load_path_cache/loaded_features_index.rb:92:in `register'
XXXXXX_rails          |  13: from /usr/local/bundle/gems/bootsnap-1.9.1/lib/bootsnap/load_path_cache/core_ext/kernel_require.rb:23:in `block in require_with_bootsnap_lfi'
XXXXXX_rails          |  12: from /usr/local/bundle/gems/bootsnap-1.9.1/lib/bootsnap/load_path_cache/core_ext/kernel_require.rb:23:in `require'
XXXXXX_rails          |  11: from /usr/local/lib/ruby/2.7.0/psych/nodes.rb:2:in `<main>'
XXXXXX_rails          |  10: from /usr/local/bundle/gems/bootsnap-1.9.1/lib/bootsnap/load_path_cache/core_ext/kernel_require.rb:31:in `require'
XXXXXX_rails          |   9: from /usr/local/bundle/gems/bootsnap-1.9.1/lib/bootsnap/load_path_cache/core_ext/kernel_require.rb:22:in `require_with_bootsnap_lfi'
XXXXXX_rails          |   8: from /usr/local/bundle/gems/bootsnap-1.9.1/lib/bootsnap/load_path_cache/loaded_features_index.rb:92:in `register'
XXXXXX_rails          |   7: from /usr/local/bundle/gems/bootsnap-1.9.1/lib/bootsnap/load_path_cache/core_ext/kernel_require.rb:23:in `block in require_with_bootsnap_lfi'
XXXXXX_rails          |   6: from /usr/local/bundle/gems/bootsnap-1.9.1/lib/bootsnap/load_path_cache/core_ext/kernel_require.rb:23:in `require'
XXXXXX_rails          |   5: from /usr/local/lib/ruby/2.7.0/psych/nodes/node.rb:2:in `<main>'
XXXXXX_rails          |   4: from /usr/local/bundle/gems/bootsnap-1.9.1/lib/bootsnap/load_path_cache/core_ext/kernel_require.rb:31:in `require'
XXXXXX_rails          |   3: from /usr/local/bundle/gems/bootsnap-1.9.1/lib/bootsnap/load_path_cache/core_ext/kernel_require.rb:22:in `require_with_bootsnap_lfi'
XXXXXX_rails          |   2: from /usr/local/bundle/gems/bootsnap-1.9.1/lib/bootsnap/load_path_cache/loaded_features_index.rb:92:in `register'
XXXXXX_rails          |   1: from /usr/local/bundle/gems/bootsnap-1.9.1/lib/bootsnap/load_path_cache/core_ext/kernel_require.rb:23:in `block in require_with_bootsnap_lfi'
XXXXXX_rails          | /usr/local/bundle/gems/bootsnap-1.9.1/lib/bootsnap/load_path_cache/core_ext/kernel_require.rb:23:in `require': superclass mismatch for class StringIO (TypeError)
XXXXXX_rails exited with code 1
```

this is my gemfile
```
source 'https://rubygems.org'
git_source(:github) { |repo| "https://github.com/#{repo}.git" }

ruby '2.7.1'

gem 'rails', '~> 6.1.4'
gem 'pg', '~> 1.1'
gem 'puma', '~> 5.0'
gem 'bcrypt', '~> 3.1.7'
gem 'jwt'
gem 'simple_command'
gem "rqrcode", "~> 2.0"
gem "pundit"
gem 'rack-cors'
gem 'active_model_serializers', "~> 0.10.2"
gem 'kaminari'
gem 'carrierwave'
gem 'fog', require: 'fog/aws'
gem "aws-sdk-s3", require: false
gem 'mini_magick'
# Reduces boot times through caching; required in config/boot.rb
gem 'bootsnap', '>= 1.4.4', require: false
gem 'paranoia', '~> 2.1'

group :development, :test do
  # Call 'byebug' anywhere in the code to stop execution and get a debugger console
  gem 'byebug', platforms: [:mri, :mingw, :x64_mingw]
  gem 'faker'
  gem 'cpf_faker'
  gem "awesome_print", require:"ap"
  gem 'factory_bot_rails'
  gem 'faker'
  gem 'rspec-rails'
end

group :test do
  gem "database_cleaner-active_record", "~> 2.0"
  gem "shoulda-matchers"
  gem "simplecov", "~> 0.21.2", require: false
end

group :development do
  gem 'faker'
  gem 'listen', '~> 3.3'
  # Spring speeds up development by keeping your application running in the background. Read more: https://github.com/rails/spring
  gem 'spring'
end

# Windows does not include zoneinfo files, so bundle the tzinfo-data gem
gem 'tzinfo-data', platforms: [:mingw, :mswin, :x64_mingw, :jruby]
```

```
root@1:/app# bundler -v
/usr/local/bundle/gems/bundler-2.1.4/lib/bundler/vendor/thor/lib/thor/error.rb:105: warning: constant DidYouMean::SPELL_CHECKERS is deprecated
Calling `DidYouMean::SPELL_CHECKERS.merge!(error_name => spell_checker)' has been deprecated. Please call `DidYouMean.correct_error(error_name, spell_checker)' instead.
Bundler version 2.1.4
root@1:/app# gem list | grep bundl
bundle (0.0.1)
bundler (2.3.5, 2.1.4)
root@1:/app#
```



----------
        
## Answer \#0

**Accepted** Vote: 15

Created at 2022-01-21 13:27:45

------------

First of all, the message about `DidYouMean` is a deprecation warning not an error, it doesn't break your app. It means that usage of `DidYouMean::SPELL_CHECKERS` is deprecated and will be removed in a future version of ruby. In this case in [Ruby 3.3](https://github.com/ruby/ruby/blob/master/lib/did_you_mean.rb#L116). You shouldn't worry about it until you use versions that are lower than 3.3.
It's not your code that triggers the warning. It comes from a gem named [Thor](https://github.com/rails/thor/blob/v1.1.0/lib/thor/error.rb#L105). The issue was solved in thor version 1.2.0. You can update the gem by calling `bundle update thor`.
The actual error comes from the `bootsnap` gem:
```
/usr/local/bundle/gems/bootsnap-1.9.1/lib/bootsnap/load_path_cache/core_ext/kernel_require.rb:23:in `require': superclass mismatch for class StringIO (TypeError)
```

As far as I can understand it loads the `psych` gem and fails.
Try to update it `bundle update bootsnap` or remove or check suggested [solutions here](https://stackoverflow.com/questions/70026904/ruby-on-rails-error-superclass-mismatch-for-class-stringio-typeerror?noredirect=1&lq=1).
If it doesn't help it might be helpful if you provide versions of `bootsnap`, `psych`, and `stringio` gems
```
gem list psych
gem list stringio
gem list bootsnap
```

or your `Gemfile.lock`


------------
    
    
## Answer \#1

 Vote: 31

Created at 2022-08-07 23:09:20

------------

This happened to me when updating Ruby in a Rails project from 3.0.4 to 3.1.2.
This fixed it for me:
```
bundle update --bundler
```

Hope it helps.


------------
    
    
## Answer \#2

 Vote: 1

Created at 2023-01-30 09:00:19

------------

Try `bundle _2.3.3_ update --bundler`.
It works for me!
Thx


------------
    
    