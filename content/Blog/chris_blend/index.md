+++
title = 'What is BlendOS?'
date = 2023-08-27T20:34:00-04:00
draft = false
description = "The blendOS team's response to Chris Titus Tech's recent video"
tags = ['BlendOS', 'linux']
type = 'post'
+++
{{< alert icon="clock-rotate-left" cardColor="#e63946" iconColor="#1d3557">}}
This article is over a year old.
{{< /alert >}}

The blendOS team's response to Chris Titus Tech's recent video.

<!-- If Chris changes that video's thumbnail, the cover image should change too :) -->

<!--more-->

# Intro

First some quick personal stuff. Now, I'm posting this on a Hugo blog, same framework Chris uses. This means comments are hosted on my repository (I use giscus, not utterances) Please do not flood the comments with angry replies, you're only hurting yourselves. Please don't flood the issues section, or anything like that. I'm sorry in advance if I offend anyone, that was not my intention.

I am writing this representing the blendOS team in response to a recent video by one Chris Titus Tech (to the Titus Tech Talk channel).

The [video in question](https://youtu.be/k1RP_TCWeNU) (skip to 4:44):


<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/k1RP_TCWeNU?amp;start=284" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>





Now, I shall begin.

**EDIT:** Chris made a pinned comment on the video correcting himself, which is good to see.

# Our Response:

## The Main Points

Let's start with a sort of play-by-play of his claims and our corrections.

### The beginning (4:44)

> I already hate this.

- You have a right to hate this distro, funnily enough I don't like immutable ones either.

> Now, let's not jump to conclusions (paraphrasing, hard to make out the last word he says).
- Chris basically says to not make unfair judgements, then proceeds to do so.

> I won't do a video on blendOS.
- You're not going to cover our distro, and that's fine, just try it privately at least.

### Midmark (5:20)

> God bless, I can only *imagine* the amount of problems they have.
- You're right on the money. I agree there's some issues around release status (stable for most, for others not) but yes we have issues, like any other distro, and we are working to fix them.

> I'm not going to cover blendOS, unless something *monumental* happens.
- That's your right, but stay tuned, we might have something up your alley 😉.

> If you like APKs, great, stick with Alpine.
- APK means Android (We ship Waydroid on the KDE and GNOME editions), and of course, you have a right to your opinion.

> Nothing good ever comes from using a shit ton of package managers.  
- You're right, which is why we use distro containers (not distrobox, more on that later).

> That's going in the trash bin.
- That hurts. But that's ok, you have a right to hate the distro.

### End (7:00)

> Having that many package managers with that many dependencies...
- Which is why we use containers.

> Just use Distrobox.  
- Ok, big explanation time. blendOS **is not** Distrobox. We used to use it, not anymore. We use a podman implementation called [blend](https://github.com/blend-os/blend), which is faster (Podman is faster and more secure than Docker) and allows for the calling of any container binary from the main shell (`binary_name.container_name`) or calling it normally using assosciatins (made by the `user` tool or `blend-settings`). We only take some code from Distrobox (which we properly credit) to support NVIDIA video cards within containers. Oh right, we also ship Waydroid 😁.

> I think it'd be fun to toy around with this stuff.  
- Please do.

## Our global response

### What they did wrong

Chris Titus Tech did screw up here. He made assumptions about a distro he did not try based on its [website](https://blendos.co). Yes, it was an informal stream clip, but people will get the wrong impression about the distro from this, I saw a few examples in Twitch chat. Everybody has the right to hate this distro, but if you want to hate it, at least try it. 

He could have given us the benefit of the doubt as he had not tried the distro, but he did not. Instead, false assumptions were made about the distro based on the website, which to you, the reader, may not explain enough. That's fine, we can fix that.

I think if you're going to hate on something, try it first. If you don't want to try it, at least give it the benefit of the doubt. This probably sums it up nicely:

> Titus it seems didn't bother to look at blendOS itself. It appears that he only took a quick glance at the [website](https://blendos.co). What he said was based on assumptions he had about blendOS, though if he actually took a look at blendOS he would've seen that a lot of his assumptions were wrong. He then recommended Distrobox, something that blendOS *used to* use for its containers.
>
> *- Joey Schaff (Jaoheah)*


> No research went into talking about the distro, he just assumed what the distro was and went on with his life.
>
> *- ethanrr ([Discord](https://discord.com/channels/1068192254365282405/1068192256235933760/1145157141771075594))*

**EDIT**

> I think, if anything, CTTs impressions of blendOS from the website can tell us that the website (as pretty as it is) doesn't quite do the distro justice, or at least doesn't communicate what makes it stand out from similar distros, why you'd want to use it over others.
> 
> *- Zephyr ([Discord](https://discord.com/channels/1068192254365282405/1068192256235933760/1145547796448026697))*

Now, I do agree with the point that all these new distros waste everybody's time, but this is different. It's not just another Ubuntu derivative, or another Arch spin. It may not seem like much now, but we are on the cusp of something game-changing, maybe even *revolutionary*, and it's not immutability.

I will also reiterate my stance that if you're going to comment on a distro, **try it first**. Everybody else who made a video about our distro, and commented on it, tried it first.

Quick judgments like this, especially when you have a larger community, can have ripple effects and damage a distro's reputation. They give people the wrong ideas about the distro.
 
### Reaction

Just to show the overall reaction, I would like to point out a few things from the video's comments now:

![comment](comment.png)

I agree.

Again, we also do not suffer from "dependency hell" because everything's containerized.

![comment2](comment2.png)

It is not using Distrobox, I already talked about this.

![comment3](comment3.png)

Which is sort of what we're doing. On a side note, nobody would do that and throw away their hard work.

![comment4](comment4.png)

Yup. Blend is a bit different however, with the containers and all.

### What I personally agree with

Reading through these did make me wonder if the distro is just wasting time. Our time, others' time. Even Rudra though about this a bit:

> Y'know, thinking about it, I do find myself pondering why we haven't poured our efforts into an actual half-decent Linux distribution akin to those of yesteryear, kinda like the first few releases of Ubuntu from ~2004-2007.
>
> *- Rudra Saraswat*

You might say he did this with [Ubuntu Unity](https://ubuntuunity.org) and the [Unity reboot](https://unityd.org). However that distro is still full of Ubuntu shitware, and Rudra can't make drastic changes as it's an official flavour now.

This made me realize that we haven't seen another Ubuntu, another Debian, in ages. It's all just rices of another distro.

I agree. If you like a packaging format, stick with it. However this will help consolidate everything into something that works (As I feel Flatpak sucks in its current state and could be better).



# Conclusion

Chris royally screwed up here, and I've corrected him. I have a feeling this isn't the first time he's made a mistake like this, but I hope it will be the last.

Now that I've said my piece, we can go back to making blendOS even better!