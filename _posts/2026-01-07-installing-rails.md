---
title: Installing Rails (MacOS)
date: 2026-01-07
categories: [Learning, Guides]
tags: [mac, rails, guides, learning, installing]
---

## Prerequisites for running Rails
- A Ruby interpreter (Rails 8 will run on Ruby versions 3.2, 3.3, and 3.4. Won't work with older versions).
- Ruby on Rails (the book I'm reading uses Rails version 8.0.2).
- Some libraries (depending on operating system being used).
- A database (SQLite 3 is used by default, PostgreSQL is more scalable but requires additional set up)
-  Docker (optional, but good practice to for isolating your development environment from your actual computer for easier deployments).

## Installing Ruby
Refer to [Installing Ruby (MacOS)](https://acortes8.github.io/posts/installing-ruby/).

## Installing Rails
1. Run the following command in your terminal:
~~~shell
$ gem install rails -v 8.0.2 --no-document
~~~
2. Done.

## Choosing a Rails version
Occasionally, you might want to run another version of Rails. What follows are some things to know.

You can use the gem command to find all the versions of Rails you have installed:
~~~shell
$ gem list --local rails
~~~

You can verify which version of Rails you're running as the global default by running:
~~~shell
$ rails --version
~~~

If the command doesn't return the expected version, you can run the follow:
~~~shell
$ rails _8.0.2_ --version
~~~

What this will do is generate a file named Gemfile in the current directory with the following contents:
> The strange syntax is called a *twiddle-wakka*, or (more formally) the pessimistic version operator. It means that you're asking for the latest version of Rails that's compatible with 8.0.2.
{: .prompt-info }
~~~Gemfile
gem "rails", "~> 8.0.2"
~~~

To upgrade rails, simply update the version number in the Gemfile that's in the root directory of your application and run:
~~~shell
$ bundle install
~~~

If needed, you can also pin to a specific version of Rails by replacing the twiddle-wakka with an equals sign.

## Databases
Rails supports many different databases. All of them, minus SQLite 3, will require a database driver to be installed for Rails to connect with it.