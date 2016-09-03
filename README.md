# Book Review: A Ruby on Rails application!

The overal goal of this application is to create book reviews.

The function goal of my developing the app was to create a collection 
for books and manipulate them [RESTfully](https://en.wikipedia.org/wiki/Representational_state_transfer) using Rails; just like [MeteorJS](https://en.wikipedia.org/wiki/Meteor_(web_framework)), amazing design and functionalities can be achieved using Ruby on Rails.

I didn't dwell a lot on the super-responsiveness of the app as I was concerned with the [Backend](https://www.upwork.com/hiring/development/back-end-web-developer/) development. When chanced 
I'll refine the nitty gritty and create some amazing feel. Programming 
late at night can have it's downsides, but no sooner do I get some spare time, than I will enhance lots of it's [Frontend](https://www.upwork.com/hiring/development/front-end-developer/) functionalities. 

## Functional Requirements

### 1. Browser duh!

```ruby
# Chrome works well and would reccomend it for wanna be Rubyists or Rails
# developers due to it's rich developer tools. 


#=> Other browsers should do the charm as well, wouldn't reccomend IE 
#   though </:-)
```

### 2. CMD Prompt / Terminal / Bash

```ruby
# I didn't deploy my app to Heroku because all my accounts are fully
# loaded with apps and thus have to pay for a deployment.


# If on a UNIX machine (Linux or Mac), chances are that you have Ruby 
# installed. Clone the folder or download it on your machine.
# CD to the folder and run the server. (I developed with Puma but 
# Webrick will still do.) Open localhost port 3000 et voila!

# If Running Winblows NT, you'll need to install Ruby cos Microsoft thinks 
# you should stick to Visual Studio Tools.
```

## Technical Requirements

### 1. Ruby and Rails. 

```ruby
# My Ruby version; 
ruby 2.3.1p112 (2016-04-26 revision 54768) [x86_64-darwin15]
# My Rails version;
Rails 5.0.0.1
# I use Version Control. Prefer Git than Subversion. 
git version 2.6.4
# Stuff you'll get out of the box are SQLite, most gems and their 
# dependencies for a basic system functionality. 
$ mkdir <your Dir>
$ CD <your Dir>
$ rails new <name of app>
$ rails s 
# Development platform created. :-)
```

### 2. Simple form

Saved me a lot of time. 
Used Gemfile

```ruby
$ gem 'simple_form'
```

Installed and ran the generator.

```ruby
$ bundle install
$ rails generate simple_form:install
```

Then got to normal Rails coding. Thats as easy as it gets. 

```erb
<%= simple_form_for @book, :html => { :multipart => true } do |josembi| %>
    <%= select_tag(:category_id, options_for_select(@categories), :prompt => "Select a category") %>
    
    <%= josembi.file_field :book_img %> <!--Add img upload function.-->
    <%= josembi.input :title, label: "Book Title" %>
    <%= josembi.input :description %>
    <%= josembi.input :author %>
    <%= josembi.button :submit, :class => "btn-custom2" %>
<% end %>
```

### 3. Bootsrap-sass

[![Gem Version](https://badge.fury.io/rb/bootstrap-sass.svg)](http://badge.fury.io/rb/bootstrap-sass)
[![npm version](https://img.shields.io/npm/v/bootstrap-sass.svg?style=flat)](https://www.npmjs.com/package/bootstrap-sass)
[![Bower Version](https://badge.fury.io/bo/bootstrap-sass.svg)](http://badge.fury.io/bo/bootstrap-sass)
[![Build Status](https://img.shields.io/travis/twbs/bootstrap-sass.svg)](https://travis-ci.org/twbs/bootstrap-sass)

Dropped it in rails using asset pipeline.
```ruby
gem 'bootstrap-sass', '~> 3.3.6'
gem 'sass-rails', '>= 3.2'

# Imported Bootstrap and it's sprockets in the application.scss
@import "bootstrap-sprockets";
@import "bootstrap";
```

### 4. Devise

[![Build Status](https://api.travis-ci.org/plataformatec/devise.svg?branch=master)](http://travis-ci.org/plataformatec/devise)
[![Code Climate](https://codeclimate.com/github/plataformatec/devise.svg)](https://codeclimate.com/github/plataformatec/devise)

A very cool authentication solution for rails. I love to write less code and use the DRY principle to avoid bugs in my applications. This one came in handy.

Devise is a flexible authentication solution for Rails based on Warden. It:

* Is Rack based;
* Is a complete MVC solution based on Rails engines;
* Allows you to have multiple models signed in at the same time;
* Is based on a modularity concept: use only what you really need.

```ruby
# I installed the gem file.
gem 'devise'
```

```console
$ rails generate devise:install
```

Devise interacts well with rails and creates nested routes automatically. No need to update them. 

### 5. Paperclip

[![Build Status](https://secure.travis-ci.org/thoughtbot/paperclip.svg?branch=master)](http://travis-ci.org/thoughtbot/paperclip)
[![Dependency Status](https://gemnasium.com/thoughtbot/paperclip.svg?travis)](https://gemnasium.com/thoughtbot/paperclip)
[![Code Climate](https://codeclimate.com/github/thoughtbot/paperclip.svg)](https://codeclimate.com/github/thoughtbot/paperclip)
[![Inline docs](http://inch-ci.org/github/thoughtbot/paperclip.svg)](http://inch-ci.org/github/thoughtbot/paperclip)
[![Security](https://hakiri.io/github/thoughtbot/paperclip/master.svg)](https://hakiri.io/github/thoughtbot/paperclip/master)

Installed this to enhance file attachment for ActiveRecord.

```ruby
gem "paperclip", "~> 5.0.0"
gem "paperclip", git: "git://github.com/thoughtbot/paperclip.git"

# It's class inherits from ActiveRecord Base. Included it this way;
class YourNameChoice < ActiveRecord::Base
  include Paperclip::Attach
  ...
end
```

After generating a model I ran a migration to create methods/functions for attachments.

```ruby
class AddAttachmentBookImgToBooks < ActiveRecord::Migration
  def self.up
    change_table :books do |t|
      t.attachment :book_img
    end
  end

  def self.down
    remove_attachment :books, :book_img
  end
end
```


### 6. jQuery Raty

[![Build Status](https://img.shields.io/travis/wbotelhos/raty/master.svg)](https://travis-ci.org/wbotelhos/raty "Travis CI")
[![Dependency Status](https://david-dm.org/wbotelhos/raty.svg)](https://david-dm.org/wbotelhos/raty "Dependency Status")
[![Dev Dependency Status](https://david-dm.org/wbotelhos/raty/dev-status.svg)](https://david-dm.org/wbotelhos/raty#info=devDependencies "Dev Dependency Status")
[![Code Climate](https://codeclimate.com/github/wbotelhos/raty.png)](https://codeclimate.com/github/wbotelhos/raty "Code Climate")

```
@version  2.7.0
@since    2010.06.11
@author   Washington Botelho
@doc      wbotelhos.com/raty
```

I integrated the jQuery.js framework file in my application and added the necessary image files (I used Imagemagick for enhancement).

Script at show page seems to have a compatibility issue with Rails 5 or some other reason that I couldn't figure out; after two hours of trying different scripts, I gave up but will revisit soon. The star ratings work pretty well in the forms though. 

```js
    $(".average-review-rating").raty({
        readOnly: true,
        score: function() {
            return $(this).attr('data-score');
        },
        path: '/assets/'
    });
    
```

### 7. Database creation

I used SQLite for development. Will use PostgreSQL when I decide to deploy to Heroku.

### 8. Deployment instructions

Deployment is straight forward in Ubuntu & Capistrano), Passenger, Git & Capistrano, Heroku, etc.
```ruby
# HEROKU: You'll need to use PostgreSQL and NOT SQLite for deployment. The 
# latter is slow in their servers.

# GIT & Capistrano: Version Control and Push to a remote repository.
# git remote add origin git@github.com:username/your-repo-name.git  {Using SSH}
# git remote add origin https://github.com/username/your-repo-name.git 
# {Using HTTP}
# Capistrano;
group :development do
    gem 'capistrano'
end

$ bundle install 

# After the install, you'll need to capify the app.
```

## Developer

Development done by;

Joseph M Mwania. 

## Contacts


http://www.theappwebtech.com/

https://twitter.com/appwebtech

https://www.facebook.com/theappwebtech/

## License

MIT License. Copyright 2016 Appwebtech. http://theappwebtech.com


