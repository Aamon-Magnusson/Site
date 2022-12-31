+++
title = "Server Update"
date = "2022-12-30T14:49:01-07:00"
author = "Aamon"
tags = ["Server", "Self-host"]
description = "An update to my self hosted server."
showFullContent = false
readingTime = true
hideComments = false
+++

As can be read from my [Hugo Setup]({{< ref "/posts/hugoSetup.md" >}}) and [Nextcloud]({{< ref "/posts/nextCloud.md" >}}) posts, currently my site is running off of a Raspberry Pi 4.
It is still proving to be a great low power server, with fairly good performance.
It's not like it should replace dedicated servers, but I like it for what I need.

I am now running a couple new services, which I will go through in the post.
In total I am running the following (in order of installation):

- `Apache`
- `Nextcloud`
- `Pi-hole`
- `PiVPN` (`Wireguard`)

I also have some future plans of other things to host, and run.

# `Apache`

Not much has changed about the `Apache` running.
I did try to setup certificates, but that ended up breaking the installation, which caused me to re-image the Pi entirely.

I have the port open to make the site accessible from the internet, and that's about all for fancy configuration.

# `Nextcloud`

The installation instructions from [my Nextcloud post]({{< ref "/posts/nextCloud.md" >}}) worked great again when I had to reinstall `Nextcloud`.

Past that not much has changed.

# `Pi-hole`

`Pi-hole` is a `DNS` ad-blocker.
I use it on my entire home network, as the default `DNS` server.
(That is set in my router)

It's not perfect, and I don't think I would recommend it.
It doesn't work on YouTube ads, and messes with the sponsored links from google.

But I'm running it now, so I might as well keep it.

## Installation

The installation is super simple.
Run the "One-Step automated install" from their GitHub:

```bash
curl -sSL https://install.pi-hole.net | bash
```

Follow the instructions, and make the needed changes to your router.
(If you want it to be the default `DNS` server)

## Fixes

There are a couple things that might need fixing.

When I first set it up ads were still showing up on my Windows machine, that can be fixed by disabling IPv6 on the machine.
Instead of doing that I disabled it for the entire network, in my router.

Through a few weeks of use I noticed my YouTube watched history was not working.
Turns out there are several domains that will get blocked that are needed for some small function in several sites and services.
The list of known domains that may be needed can be found [here](https://discourse.pi-hole.net/t/commonly-whitelisted-domains/212).
To fix my particular issue run I ran the following commands:

```bash
pihole -w s.youtube.com
pihole -w video-stats.l.google.com
```

# `PiVPN`

`PiVPN` is simply an installer for either `Wireguard` or `OpenVPN`.
Either of which will allow you to `VPN` into the network from which the device is hosting the service is from.

I am using it as a method to access some things that are within my network, but not accessible from the internet.
Like my `Nextcloud` instance, and to access my Raspberry Pi and Kali machines through `ssh`.

This also means I can work from home, from anywhere.
Some things I do with work are linked to my IP, which I am able to use through the VPN.

## Installation

Similar to `Pi-hole`, the install is done through one command, and some guided questions:

```bash
curl -L https://install.pivpn.io | bash
```

From there you will also have to open a port on your router, which will depend on the service you use, and if you change the port during install.

The `Wireguard` apps are super easy to use, and seem really quick.

# Plans

I have several services I would like to add, and some clean up I need to do.

* First on my list, I would like to get a reverse proxy/tunnel set up with CloudFlare.
I'm hoping this will be an easy way to secure any services I want open to the internet.
* Next I would like to set up an app like Memo, for taking quick notes.
I currently use Google Keep, but self-hosting would be good.
Plus it would be Markdown.
* Not that I think I will self-host it, but I would like an email server.
I'm thinking I will use AWS SES, due to the complexity of self-hosting.
This will be used for the next service.
* I'm thinking I would like my own password manager.
I'm leaning towards Bitwarden, but that is not final.
* Past this are just potentially cool things that I might do someday, but not soon, like a Matrix server, so that I can have my own chat room, and an RSS feed collector.
Oh, and I could also run a Minecraft server, for the *lols*.
These will be a fair bit further out though.
