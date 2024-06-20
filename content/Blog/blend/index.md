+++
title = 'BlendOS V3'
description = "My thoughts on BlendOS v3"
date = 2023-08-23T07:28:27-04:00
draft = false
tags = ["blendOS", "Hashnode Archive", "Linux"]
type = 'post'
+++

<!--more-->

{{< alert icon="clock-rotate-left" cardColor="#e63946" iconColor="#1d3557">}}
This article is over a year old.
{{< /alert >}}

-- **This post is from my hashnode blog.** --

The true end to distro hopping gets an upgrade.

So blendOS v3 came out (I still have to update the docs oh god).

# v3

## What I like

So far, I'm excited about the full immutability (snapshots and easy backups), and this newfangled ISO update system (to confuse ['ol Baldy here](https://github.com/rayvermey)). The `akshara` utility is cool too.

## So what's new?

Rudra made a [trailer](https://www.youtube.com/watch?v=Ugv1mAdPN04) to push all this, I recommend you watch it for the iMovie stock music (although Apple only recently unveiled actual Apple stores in India):

[youtube embed removed]

Rudra also outlined everything in a [blog post](https://blendos.co/blend-os-v3/) (`iframe`'d badly below):

[iframe removed]

### TL;DR

It all boils down to the following:

* Installation ISOs are used for updates (never seen before, a new breakthrough!).

* `akshara`, some new management utility that Rudra forgot to write the README for. It's a mystery what it is to me anyway.

* `zsync` is being set up for the ISO repo to only download changed files, like what git does.

* Updates are in the background and instantaneous.

* Rudra made `assemble`, a tool based on the LineageOS `repo` build tool, which makes remixing and ISO building easy via XML manifests

* Akshara can be used to install extra drivers, though the ISO comes with many.

* It supports these distro containers:
  
  * Arch
  
  * AlmaLinux 9
  
  * Crystal Linux
  
  * Debian
  
  * Fedora 38
  
  * Kali Linux (rolling)
  
  * Neurodebian Bookworm
  
  * Rocky Linux
  
  * Ubuntu 22.04
  
  * Ubuntu 23.04

* Misc. bug fixes

* Same old binary naming scheme (`BINARY_NAME.CONTAINER_NAME`)

* I'm put under more pressure to finish the docs 🙂

Releases are named after Indian foods now, in alphabetical order (so what happens after v23...)

I also want v4 to be called blendOS Cheeseburger, although Leviathan and Avalon are valid options.

> blendOS is like a cheeseburger, in every single way except for all of them.
> 
> \- Asterisk

## What's next?

* We're planning on moving most of the repositories to our new [GitLab instance](https://git.blendos.co/blendos).

* We're also hoping to have a proper KB by v3 stable.

* `zsync` needs to be implemented for updates.

* We have to get v3 onto peoples' mirrors and we have to set up [`mirrorbits`](https://github.com/etix/mirrorbits) on the build server.

## Conclusion

This one was a bit shorter, but in general I'm happy with the project and hope it only gets better. These changes will help it be a better replacement for (or get it closer to, depending on your opinion) Bedrock Linux or VanillaOS, and give it a better user experience and more customizability overall.

Thanks for reading!
