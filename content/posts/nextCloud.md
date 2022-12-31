+++
title = "Nextcloud"
date = "2022-11-19T11:18:22-07:00"
author = "Aamon"
#cover = ""
tags = ["Server", "Self-host"]
#keywords = ["", ""]
description = "Here's how I set up my `Nextcloud` instance locally."
showFullContent = false
readingTime = true
hideComments = false
#color = "" #color from the theme settings
+++

As should already be known, I'm hosting this site off of my Raspberry Pi 4.
Since my goal with is it to make it the best server **for myself** that I can, it is now running my own `Nextcloud` instance.

`Nextcloud` is an open open-source alternative to Google Drive, OneDrive, or Dropbox.
As with the other services, you can pay for cloud hosted access, which makes it feel like all the other cloud shares.
(While being open-source, which is still cool)
What makes `Nextcloud` special is that you can also self host your own instance.

They have a few options for hosting:

* `Docker`
* `Snap`
* VM image

I initially tried to get the all-in-one `Docker` image working, as I've had a little experience with `Docker` from building a `CTF` in work.
For what ever reason copy pasting the command from the Github didn't work, even though it was the "Command for arm64 CPUs like the Raspberry Pi 4".
I found that fairly strange, as `Docker` and other container systems are meant to make running programs work on whatever system.
Whatever, I just decided to run the `Snap` which seems like the preferred method by Linux users.

In the past I've not been a fan of `Snap`, but when I think about it as a `Docker` replacement I'm more of a fan already.

To get an instance running with `Snap` you only need to run one command:

```bash
sudo snap install nextcloud
```

Which is really cool!!!

...

However, I have some more specific needs.

* I can't have it running on port 80, as that's where the `apache2` server is running.
* I want to have all the data running on an external drive, so that it does not impact the system storage.

While these sound specific, they are not difficult to setup.

First I had to set an environment variable.
`$SNAP_COMMON` is the variable that controls where the data goes.
To set it for all users creating a file in `/etc/profile.d` with the export will do it.
I created a file called `nextCloud.sh` and wrote the following:

```bash
export SNAP_COMMON=/media/aamonm/Small\ Drive
```

And for the other requirements I ran the following commands:

```bash
sudo snap connect nextcloud:removable-media
sudo snap connect nextcloud:network-observe
sudo snap set nextcloud ports.http=81 ports.https=444
```

Other than that, I opened my browser to [aamonserver:81](http://aamonserver:81) and completed the setup.

I now have my own *cloud* share, so that's pretty cool, and useful.

**Notes**

* It is only accessible from inside my home network at the moment (Same as the site itself)
* I have not set up certificates, since I can't do that on port 81 or 444, which is where I want it.
