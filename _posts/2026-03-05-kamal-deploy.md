---
title: Kamal Deploy
date: 2026-03-05
categories: [Learning, Guides]
tags: [kamal, deployment, export, passwords, credentials, guides, learning, postgres, docker]
---

To deploy updates to a VPS run `$ kamal deploy` on the local, development machine (not the VPS).

For this command to work you'll need to first set some environment variables for your Docker and Postgres passwords. Kamal reads these variables and sends them to the VPS when you run the deploy command to complete the set up. These environment variables only last for your current terminal session, so remember to set them again when needed. To set them you use the `export` command, and the two commands would look something like this:

`$ export KAMAL_REGISTRY_PASSWORD="yourpasswordhere"`

`$ export POSTGRES_PASSWORD="yourotherpasswordhere"`

If you find this tedious, you can instead use a password manager, read the Kamal secrets file in your project and there'll be a comment in it about how you can do this.