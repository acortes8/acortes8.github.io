---
title: Rails Console in a VPS
date: 2026-03-05
categories: [Learning, Guides]
tags: [rails, databases, postgres, hetzner, vps, docker]
---

Sometimes you need to query the database of your Rails application to query something from a table like an image address. Here's how you do that.

In this situation we're using a VPS, so we'll first want to ssh into that server with `$ ssh example.com`, and if you changed the ssh port on the VPS add that with a flag like so `$ ssh example.com -p 12345`.

Now, what you think would be next might be running `$ rails console`, but that won't work if we're using Docker to containerize our application.

What we need to do instead is to first list what containers we have running on our VPS with `$ docker ps`, this command will list them out for us. For our purposes we want to find the web server's container will might look something like `myapp-web`. You might see another container named something like `myapp-postgres` and think that one would be more apt for our purposes, but the web container has a connection to the Postgres container so for our convenience we can just use the web container for everything.

With this information you want to enter the web container with a command similar to this `docker exec -it myapp-web bash`.

This will open an interactive terminal to that container's environment, and in here is where we can run `bin/rails console` to query our database and retrieve information like so as an example:
```ruby
$ include Rails.application.routes.url_helpers

$ Beverage.with_attached_featured_image.each do |b|
    puts rails_blob_url(b.featured_image, host:
    "https://buzzysbar.com")
  end
```

