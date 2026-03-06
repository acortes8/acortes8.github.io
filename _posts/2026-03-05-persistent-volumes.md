---
title: Persistent Volumes, Records Not Loading Deployment
date: 2026-03-05
categories: [Learning, Guides]
tags: [rails, docker, kamal, volumes, databases, configuration]
---

My web application worked perfectly well for the month I've had it up so far on a Hetzner VPS using Kamal and Docker. But recently, after pushing a backlog of new changes I've made to my deployment, I noticed something was wrong. 

Seemingly randomly, my records for my Beverages table were changed. What used to be working, loadable images, and titles of real cocktails changed to be random strings. What this looked like can be seen below:

![Example Image](assets/img/posts/persistent-volumes/persistent_volumes_0.png)


Using the Rails console, I checked if these images were still in my database and they were from what I could tell, I covered how I checked this in [Rails Console in a VPS](https://acortes8.github.io/posts/rails-console-vps/). So I had to do some more digging to find out what was going on here what follows is what I believe to have been going wrong here. 

I'm using Kamal and Docker, and because of the way I had them configured I did not have persistent storage.

In `config/environments/production.rb` I had the line `config.active_storage.service = :local`.

And in my `storage.yml` I had `local` defined as such:
```yaml
local:
  service: Disk
  root: <%= Rails.root.join("storage") %>
```

So Active Storage was set to save to `/rails/storage`, and if I ssh'ed into my VPS, entered my web container, and ran `ls -a storage/` I could see that it is empty when it should've had some randomly named files in it.

Having it set up this way made my filesystem ephemeral. The files were fine for that first month until I redeployed using Kamal to push new unrelated changes. Doing this made Docker reinitialize the container making the original storage directory's contents disappear as it was replaced with an empty version of itself. 

But you might ask if that was the case, then why did the database say there were still images attached when I checked through the Rails console?

Well, it's because the database still contained the Active Storage metadata for them; the actual files, however, were gone. Which is why if I checked the elements in the browser using Inspect, I could see 404 errors. The attachment to the images still exists in the database, which would say that the records to have images attached to themselves, but the actual images that the attachments point to are missing on the disk.

Now that I knew what was wrong, I could fix it by making my data persist through deployments. 

There are three options I found I could consider.

The first option, that made the least sense to me, was doing a bind mount to a storage directory in the the Hetzner VPS environment, outside of the container. To do this, you would go to your Docker `deploy.yml` file and add a volume like so:
```yaml
volumes:
  - "/var/buzzysbar/storage:/rails/storage"
```

This option didn't seem ideal to me because I spent the effort of getting everything to run containerized using Docker, so having something set up outside of the container and in the top-level VPS environment, outside of the scope and management of Docker, seemed like a step in the wrong direction.

Instead, the second option was that I could mount the storage already used and set by Docker as a persistent volume so Docker keeps it around when we redeploy, like so:
```yaml
volumes:
  - "buzzysbar_storage:/rails/storage"
```

This keeps the volume and directories managed by Docker persistent, which for our situation and needs will work I believe, and if not, or if our needs increase, we can use object storage.