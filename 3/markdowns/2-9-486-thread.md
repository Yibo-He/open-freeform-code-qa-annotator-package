
# Post \#71265163 [Link](https://stackoverflow.com/questions/71265163/)

## Application.js not compiling after upgrading to Rails 7 on heroku with esbuild

**Vote**: 4 (532/702) **Views**: 4635 (531/702) 

**Internal ID** \#2-9-486

Created at 2022-02-25 11:24:43

Tags: `ruby-on-rails` `ruby` `heroku` `sprockets` `esbuild`

----------

#### Metadata:

Area: `Back-end`

Language: `ruby` (full parsed tag list: `ruby`)

----------

**Notepad**


----------

I updated my app on Heroku from Rails 6 with Webpacker to Rails 7 with esbuild.
The error I receive on production is as follows:
```
The asset "application.js" is not present in the asset pipeline
```

I went into my Heroku server and saw that the application.js file was inside  and in my manifest.js it is setup as follows:
```
//= link_tree ../images
//= link_tree ../builds
```

But when I check the * folder, all files are there except application.js and one css file.
As recommended by Heroku on their [site](https://devcenter.heroku.com/articles/rails-4-asset-pipeline#debugging) I also tried the below code locally:
```
RAILS_ENV=production bundle exec rake assets:precompile
```

This compiles all files including application.js into * and works normally on local. On Heroku production even if I try to manually compile, the application.js does not copy into *
My esbuild script is as follows and works with no problem:
```
"build": "esbuild app/javascript/*.* --bundle --outdir=app/assets/builds"
```

Does anyone have a clue or solution to load application.js into public/assets so that I do not get the below error?
```
The asset "application.js" is not present in the asset pipeline
```

Here is the app/javascript/application.js
```
// Entry point for the build script in your package.json
import "@hotwired/turbo-rails"
import "./controllers"
import * as bootstrap from "bootstrap"
import "lazysizes"
import "@fortawesome/fontawesome-free/js/all"

if ('scrollRestoration' in window.history) {
  window.history.scrollRestoration = 'manual';
}
```

Here is a css file that is also not compiling, maybe there is a connection, but I am not able to find out. (all other css files in this folder except for this file just compile to public/assets)
app/assets/stylesheets/shared/swiper.scss
```
@import "swiper/swiper.scss";
@import "swiper/modules/navigation/navigation.scss";
@import "swiper/modules/lazy/lazy.scss";

.swiper-button-next {
  color: #000000;
}

.swiper-button-prev {
  color: #000000;
}
```

and my script the script to place scss to css into app/assets/builds
```
"build:css": "sass ./app/assets/stylesheets/application.bootstrap.scss:./app/assets/builds/application.css ./app/assets/stylesheets/controllers:./app/assets/builds/controllers ./app/assets/stylesheets/shared:./app/assets/builds/shared ./app/assets/stylesheets/devise:./app/assets/builds/devise ./app/assets/stylesheets/errors.scss:./app/assets/builds/errors.css --no-source-map --load-path=node_modules"
```

Not sure if helpful, but here is my deploy log. (no errors)
```
git push heroku master                                           
Enumerating objects: 15, done.
Counting objects: 100% (15/15), done.
Delta compression using up to 12 threads
Compressing objects: 100% (8/8), done.
Writing objects: 100% (8/8), 633 bytes | 633.00 KiB/s, done.
Total 8 (delta 7), reused 0 (delta 0), pack-reused 0
remote: Compressing source files... done.
remote: Building source:
remote: 
remote: -----> Building on the Heroku-20 stack
remote: -----> Using buildpack: heroku/ruby
remote: -----> Ruby app detected
remote: -----> Installing bundler 2.2.33
remote: -----> Removing BUNDLED WITH version in the Gemfile.lock
remote: -----> Compiling Ruby/Rails
remote: -----> Using Ruby version: ruby-3.0.2
remote: -----> Installing dependencies using bundler 2.2.33
remote:        Running: BUNDLE_WITHOUT='development:test' BUNDLE_PATH=vendor/bundle BUNDLE_BIN=vendor/bundle/bin BUNDLE_DEPLOYMENT=1 bundle install -j4
remote:        Using rake 13.0.6
remote:        Using concurrent-ruby 1.1.9
remote:        Using i18n 1.8.11
remote:        Using minitest 5.15.0
remote:        Using tzinfo 2.0.4
remote:        Using activesupport 7.0.0
remote:        Using builder 3.2.4
remote:        Using erubi 1.10.0
remote:        Using racc 1.6.0
remote:        Using nokogiri 1.12.5 (x86_64-linux)
remote:        Using rails-dom-testing 2.0.3
remote:        Using crass 1.0.6
remote:        Using loofah 2.13.0
remote:        Using rails-html-sanitizer 1.4.2
remote:        Using actionview 7.0.0
remote:        Using rack 2.2.3
remote:        Using rack-test 1.1.0
remote:        Using actionpack 7.0.0
remote:        Using nio4r 2.5.8
remote:        Using websocket-extensions 0.1.5
remote:        Using websocket-driver 0.7.5
remote:        Using actioncable 7.0.0
remote:        Using globalid 1.0.0
remote:        Using activejob 7.0.0
remote:        Using activemodel 7.0.0
remote:        Using activerecord 7.0.0
remote:        Using marcel 1.0.2
remote:        Using mini_mime 1.1.2
remote:        Using activestorage 7.0.0
remote:        Using mail 2.7.1
remote:        Using actionmailbox 7.0.0
remote:        Using actionmailer 7.0.0
remote:        Using actiontext 7.0.0
remote:        Using public_suffix 4.0.6
remote:        Using addressable 2.8.0
remote:        Using aws-eventstream 1.2.0
remote:        Using aws-sigv4 1.4.0
remote:        Using bcrypt 3.1.16
remote:        Using msgpack 1.4.2
remote:        Using bootsnap 1.9.3
remote:        Using method_source 1.0.0
remote:        Using thor 1.1.0
remote:        Using zeitwerk 2.5.1
remote:        Using railties 7.0.0
remote:        Using breadcrumbs_on_rails 4.1.0
remote:        Using bundler 2.2.33
remote:        Using mini_magick 4.11.0
remote:        Using ffi 1.15.4
remote:        Using ruby-vips 2.1.4
remote:        Using image_processing 1.12.1
remote:        Using ssrf_filter 1.0.7
remote:        Using carrierwave 2.2.2
remote:        Using cssbundling-rails 1.0.0
remote:        Using orm_adapter 0.5.0
remote:        Using responders 3.0.1
remote:        Using warden 1.2.9
remote:        Using devise 4.8.1
remote:        Using unf_ext 0.0.8
remote:        Using unf 0.1.4
remote:        Using domain_name 0.5.20190701
remote:        Using excon 0.89.0
remote:        Using ffi-compiler 1.0.1
remote:        Using formatador 0.3.0
remote:        Using mime-types-data 3.2021.1115
remote:        Using mime-types 3.4.1
remote:        Using fog-core 2.2.4
remote:        Using multi_json 1.15.0
remote:        Using fog-json 1.2.0
remote:        Using fog-xml 0.1.4
remote:        Using ipaddress 0.8.3
remote:        Using fog-aws 3.12.0
remote:        Using friendly_id 5.4.2
remote:        Using heroku-deflater 0.6.3
remote:        Using http-cookie 1.0.4
remote:        Using http-form_data 2.3.0
remote:        Using llhttp-ffi 0.4.0
remote:        Using http 5.0.4
remote:        Using jbuilder 2.11.4
remote:        Using jsbundling-rails 1.0.0
remote:        Using json 2.6.1
remote:        Using kaminari-core 1.2.1
remote:        Using kaminari-actionview 1.2.1
remote:        Using kaminari-activerecord 1.2.1
remote:        Using kaminari 1.2.1
remote:        Using meta-tags 2.16.0
remote:        Using oauth 0.5.8
remote:        Using pg 1.2.3
remote:        Using puma 4.3.10
remote:        Using rails 7.0.0
remote:        Using rakuten_web_service 1.13.1
remote:        Using ransack 2.4.2 from https://github.com/activerecord-hackery/ransack (at 81910c2@81910c2)
remote:        Using sassc 2.4.0
remote:        Using sprockets 4.0.2
remote:        Using sprockets-rails 3.4.2
remote:        Using tilt 2.0.10
remote:        Using sassc-rails 2.1.2
remote:        Using sass-rails 6.0.0
remote:        Using settingslogic 2.0.9
remote:        Using sitemap_generator 6.1.2
remote:        Using slack-notifier 2.4.0
remote:        Using temple 0.8.2
remote:        Using slim 4.1.0
remote:        Using slim-rails 3.3.0
remote:        Using stimulus-rails 1.0.2
remote:        Using turbo-rails 1.0.0
remote:        Using twitter-ads 10.0.0
remote:        Using vacuum 4.0.0
remote:        Bundle complete! 49 Gemfile dependencies, 107 gems now installed.
remote:        Gems in the groups 'development' and 'test' were not installed.
remote:        Bundled gems are installed into `./vendor/bundle`
remote:        Bundle completed (0.93s)
remote:        Cleaning up the bundler cache.
remote: -----> Installing node-v16.13.1-linux-x64
remote: -----> Installing yarn-v1.22.17
remote: -----> Detecting rake tasks
remote: -----> Preparing app for Rails asset pipeline
remote:        Running: rake assets:precompile
remote:        DEPRECATION WARNING: `active_support/core_ext/uri` is deprecated and will be removed in Rails 7.1. (called from <main> at /tmp/build_07dca8b4/config/application.rb:7)
remote:        yarn install v1.22.17
remote:        [1/4] Resolving packages...
remote:        [2/4] Fetching packages...
remote:        [3/4] Linking dependencies...
remote:        [4/4] Building fresh packages...
remote:        Done in 5.32s.
remote:        yarn run v1.22.17
remote:        $ sass ./app/assets/stylesheets/application.bootstrap.scss:./app/assets/builds/application.css ./app/assets/stylesheets/controllers:./app/assets/builds/controllers ./app/assets/stylesheets/shared:./app/assets/builds/shared ./app/assets/stylesheets/devise:./app/assets/builds/devise ./app/assets/stylesheets/errors.scss:./app/assets/builds/errors.css --no-source-map --load-path=node_modules
remote:        Done in 2.32s.
remote:        yarn install v1.22.17
remote:        [1/4] Resolving packages...
remote:        success Already up-to-date.
remote:        Done in 0.10s.
remote:        yarn run v1.22.17
remote:        $ esbuild app/javascript/*.* --bundle --outdir=app/assets/builds
remote:        
remote:          app/assets/builds/application.js  2.1mb ⚠️
remote:        
remote:        Done in 0.22s.
remote:        Asset precompilation completed (10.98s)
remote:        Cleaning assets
remote:        Running: rake assets:clean
remote:        DEPRECATION WARNING: `active_support/core_ext/uri` is deprecated and will be removed in Rails 7.1. (called from <main> at /tmp/build_07dca8b4/config/application.rb:7)
remote: -----> Detecting rails configuration
remote: 
remote: ###### WARNING:
remote: 
remote:        There is a more recent Ruby version available for you to use:
remote:        
remote:        3.0.3
remote:        
remote:        The latest version will include security and bug fixes. We always recommend
remote:        running the latest version of your minor release.
remote:        
remote:        Please upgrade your Ruby version.
remote:        
remote:        For all available Ruby versions see:
remote:          https://devcenter.heroku.com/articles/ruby-support#supported-runtimes
remote: 
remote: ###### WARNING:
remote: 
remote:        No Procfile detected, using the default web server.
remote:        We recommend explicitly declaring how to boot your server process via a Procfile.
remote:        https://devcenter.heroku.com/articles/ruby-default-web-server
remote: 
remote: 
remote: -----> Discovering process types
remote:        Procfile declares types     -> (none)
remote:        Default types for buildpack -> console, rake, web
remote: 
remote: -----> Compressing...
remote:        Done: 101.3M
remote: -----> Launching...
remote:        Released vxxxx
remote:        https://xxxxxxxxx.herokuapp.com/ deployed to Heroku
remote: 
remote: Verifying deploy... done.
To https://git.heroku.com/xxxxxxxxx.git
   xxxxx..xxxxxx  master -> master
```


Seems like that when I deploy to Heroku, that the Heroku first runs assets compile and then the package json builds. Because of this, the builds folder is empty when compile runs and the application.js does not copy to public/assets.
For now to solve it, I removed builds folder from git ignore and add the files from builds to the repository. So now when compile runs, the build folder has the files and it compiles it to public/assets. I know that this is not the best way to solve, but for now it was the only way I knew to solve it.
If someone knows a way to edit the heroku deploy script to run assets compile after package json build script then it solves the problem.


----------
        
## Answer \#0

**Accepted** Vote: 7

Created at 2022-04-11 21:29:05

------------

Do you have `/app/assets/builds/.keep` pushed to the repository?
The problem might be that if the empty folder is not present during `rake assets:precompile`, then even though `jsbundling-rails` (for example; or similar) does something like `Rake::Task["assets:precompile"].enhance(["build"])` internally — the folder itself won't be considered by `rake assets:precompile` even if the `enhance`-ed rake task populates it.
While if it was initially present & empty — everything will work fine.
So in my case I didn't need to push the whole `/app/assets/builds` folder with all real contents, but I needed to push `.keep` there so that an empty folder is present before `assets:precompile` is run.
And then `.gitignore` only its contents, but make sure folder does not disappear after cloning the repo:
```
/app/assets/builds/*
!/app/assets/builds/.keep
```



------------
    
    
## Answer \#1

 Vote: 1

Created at 2022-03-08 23:27:10

------------

Add:  [https://github.com/rails/jsbundling-rails](https://github.com/rails/jsbundling-rails)
...When you deploy your application to production, the javascript:build task attaches to the assets:precompile task to ensure that all your package dependencies from package.json have been installed via yarn, and then runs yarn build to process all the entry points, as it would in development. The latter files are then picked up by the asset pipeline, digested, and copied into public/assets, as any other asset pipeline file...


------------
    
    
## Answer \#2

 Vote: 1

Created at 2022-08-28 00:29:04

------------

remove uglifier and install terser
```
gem 'terser'
```

```
// config/environments/production.rb

config.assets.js_compressor = :terser
```



------------
    
    
## Answer \#3

 Vote: 0

Created at 2022-05-13 15:08:06

------------

I was having a similar issue but with esbuild not installing during deploy, which lead me to this page during troubleshooting.
I had committed the `node_modules` folder with a `.yarn-integrity` file.
What fixed it for me was removing the `node_modules` folder, running `yarn install`, making sure the `node_modules` folder was ignored in my `.gitignore` file, and pushing the commit.
Once I deployed the application, the deploy was successful.


------------
    
    