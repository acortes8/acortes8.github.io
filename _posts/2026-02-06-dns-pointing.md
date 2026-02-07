---
title: DNS Pointing
date: 2026-02-06
categories: [Learning, Guides]
tags: [dns, domains, hetzner, vps, server, security, guides, learning]
---

# What is DNS?
DNS stands for Domain Name System. It points domain names to IP addresses (e.g., example.com resolving to 203.0.113.1).

## How to point an external domain to a Hetzner server
In the examples below `example.com` is to be substituted with whatever root domain you own.

1. Log in to your Domain registrar (e.g., Squarespace).
2. Navigate to DNS settings on the registrar's dashboard.
3. Add/Update an `A` record.
    1. Type: `A`
    2. Host/Name: `@` (This represents the root domain)
    3. Value/Target: Your Hetzner Server IPv4 Address
4. Add `WWW` record (optional).
    1. Type: `CNAME`
    2. Host/Name: `www`
    3. Value: `@` or `example.com`
5. Configure Reverse DNS
    1. Log into Hetzner
    2. Select your project and specific server
    3. Navigate to the `Networking` tab in the menu
    4. Find your IP address and then click the three dots
    5. Edit the Reverse DNS and enter your full domain name then click save
6. Wait for DNS changes to propagate, can take a few minutes, up to 48 hours.

The optional `www` record is so visiting both `example.com` and `www.example.com` will work. The root domain is `example.com` while `www` is a subdomain that can be prefixed to the root domain. The two addresses are not considered to be the same unless you add a `CNAME` record pointing the `www` subdomain back to the root domain.

The Reverse DNS configuration is not critical nor universally adopted by the internet, but it's good practice to set up and is suggested by the Standards from the Internet Engineering Task Force. Setting it up helps with proving legitimacy and other security purposes.