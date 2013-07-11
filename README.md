# Gutentag

A good, simple, solid tagging extension for ActiveRecord.

This was built partly as a proof-of-concept, and partly to see how a tagging gem could work when it's not all stuffed within models, and partly just because I wanted a simpler tagging library.

## Installation

Get it into your Gemfile - and don't forget the version constraint!

    gem 'gutentag', '~> 0.1.0'

Next: your tags get persisted to your database, so let's import and run the migrations to get the tables set up:

    rake gutentag:install:migrations
    rake db:migrate

## Usage

The first step is easy: add the tag associations to whichever models should have tags (in these examples, the Article model):

    class Article < ActiveRecord::Base
      # ...
      has_many_tags
      # ...
    end

That's all it takes to get a tags association on each article. Of course, populating tags can be a little frustrating, unless you want to manage Gutentag::Tag instances yourself? As an alternative, just use the tag_names accessor to get/set tags via string representations.

    article.tag_names #=> ['pancakes', 'melbourne', 'ruby']
    article.tag_names << 'portland'
    article.tag_names #=> ['pancakes', 'melbourne', 'ruby', 'portland']
    article.tag_names -= ['ruby']
    article.tag_names #=> ['pancakes', 'melbourne', 'portland']

## Licence

Copyright (c) 2013, Gutentag is developed and maintained by Pat Allan, and is released under the open MIT Licence.
