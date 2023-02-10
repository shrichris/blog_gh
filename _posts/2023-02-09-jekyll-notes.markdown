---
layout: post
title:  "Jekyll Notes"
date:   2023-02-09 
categories: notes
tags: jekyll
---

# Getting Started with Jekyll

Step by step instructions can be found [here][jekyll-step-by-step]

[Jekyll tutorial][jekyll-playlist] on Youtube

## Prerequisites

Jekyll is a Ruby gem and requires ruby and gem to be installed.

{% highlight console %}
gem install jekyll bundler
{% endhighlight %}

## Create and serve a new Jekyll site on your local machine

{% highlight console %}
jekyll new new-site
cd new-site
bundle exec jekyll serve
{% endhighlight %}

bundle exec is required when configuration changes need to be aplied. 

For changes to content the following is sufficient.
{% highlight console %}
jekyll serve
{% endhighlight %}

## Managing Draft posts

To serve draft posts in _drafts folder, use
{% highlight console %}
jekyll serve --draft
{% endhighlight %}

drafts are served using current date

Use the default naming convention when a draft post is ready to be published.

## Permalinks

Custom permalinks can be crafted to override the Jekyll defauly. For example to avoid using the categories in the post url

{% highlight console %}
permalink: /:year/:month/:day/:title
{% endhighlight %}

## Front matter defaults

are defined in the _config.yml file
## Jekyll themes

[Theme Search](https://rubygems.org/search?query=jekyl-theme)

install a theme by adding the theme to the gemfile e.g.

{% highlight console %}
gem "jekyll-theme-hacker"
{% endhighlight %}

To install the theme, run
{% highlight console %}
bundle install
{% endhighlight %}

Update the config file to use the theme.

To update the site to serve using the new theme, use

{% highlight console %}
budle exec
{% endhighlight %}

Be aware that if the new theme does not have layouts with the same names as the previous theme, pages will not render.

## Jekyll variables

List of Jekyll [variables](https://jekyllrb.com/docs/variables/)
## Deploy to github pages

[jekyll-playlist]: https://www.youtube.com/playlist?list=PLLAZ4kZ9dFpOPV5C5Ay0pHaa0RJFhcmcB
[jekyll-step-by-step]: https://jekyllrb.com/docs/step-by-step/01-setup/
## Odds and Ends

Jekyll uses categories to create url for posts.
