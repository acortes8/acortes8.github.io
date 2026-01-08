---
title: Installing Ruby(MacOS)
date: 2026-01-07
categories: [Learning, Guides]
tags: [mac, ruby, guides, learning, installing]
---

MacOS usually ships with Ruby already, albeit older versions of Ruby. You'll need to download a newer version of Ruby. Easiest way to do this would be to use Homebrew. 

## Installing Homebrew
Refer to [Installing Homebrew (MacOS)](https://acortes8.github.io/posts/installing-homebrew/).

## Installing Ruby
> Homebrew is required to be installed for either path of installing Ruby.
{: .prompt-info }

Install Ruby, by either using homebrew (which will install the latest version of Ruby by default) or mise-en-place (which will let you pick which versions of Ruby to install and let's you switch between versions easily).

### With homebrew
1. Run the following command in your terminal:
~~~shell
$ brew install ruby
~~~
2. The terminal will prompt you to run some post-installation commands, which involve adding lines to you ~/.zshrc file (if the file doesn't exist, create it using `$ touch ~/.zshrc`).  Run what will most likely be the following commands:
~~~shell
$ export PATH="/opt/homebrew/lib/ruby/gems/3.4.0/bin:$PATH"
$ export PATH="/opt/homebrew/opt/ruby/bin:$PATH"
$ export LDFLAGS="-L/opt/homebrew/opt/ruby/lib"
$ export CPPFLAGS="-I/opt/homebrew/opt/ruby/include"
~~~
3. Done.

### With mise-en-place
1. Run the following commands in your terminal:
~~~shell
$ brew install mise
$ echo 'eval "$(mise activate zsh)"' >> ~/.zshrc
$ eval "$(mise activate zsh)"
~~~
2. After that, you can install Ruby through mise (this sets the global ruby default on your computer to version 3.4.3):
~~~shell
$ mise use -g ruby@3.4.3
~~~
3. If you're wanting to use different versions of Ruby for different projects, you can use the mise trust command in the root of each project:
~~~shell
# while inside the root directory of a project
$ mise trust
~~~
4. Done.

### Alternatives
Other routes for installing Ruby include the following:
* rbenv
* RVM
* asdf
* chruby

## Checking your Ruby version
Whatever path you take to install Ruby, run the following command to see which version of Ruby you're working with:
~~~shell
$ ruby -v
~~~