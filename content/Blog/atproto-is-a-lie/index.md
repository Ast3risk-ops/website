+++
title = 'ATProto (Bluesky) is a Lie'
description = 'Why Bluesky and ATProto at large will fall just like Twitter.'
date = 2026-02-01T16:34:18-04:00
draft = false
tags = ['Bluesky', 'Fediverse']
type = 'post'
series = ["Bluesky"]
series_order = 1
+++

<!--more-->

Background image by Unknown Author (found on [PeakPx](https://www.peakpx.com/en/hd-wallpaper-desktop-kyjnp))

>[!TIP]
>This blog post uses [Nutshells](https://ncase.me/nutshell)! Click any link starting with a colon (:) to {{< nutshell title="expand it" href="https://ncase.me/nutshell/#WhatIsNutshell" >}} (requires JavaScript). You can also Nutshell any heading (hidden in a Nutshell or not) from this page and use it in your own writing!

*If JavaScript is unavailable, you will see all local Nutshells listed below. External Nutshells will become standard links.*

>[!note] Corrections
>Corrected AppView definition and implications, The AppView is a central API that handles ingesting, webapps then pull from that. It's actually worse than what I originally thought.

# :x Nutshells

<noscript>
These are all the Nutshells that were used in the post.
</noscript>
<br><br>

###### :x Blitzscaling

{{< nutwarn >}}

Blitzscaling, based on the German warfare strategy of *blitzkrieg*, consists of raising a ton of venture capital funding, then using that funding to survive while undercutting your competitors. Once all competition is dead, you jack prices back up and strangle your newfound userbase, who will still stay with your service due to how familiar it is.

The most notable example of this strategy is DoorDash, who ended up being the top food delivery app despite entering the market very late. They paid their drivers well and sold food cheaply up until they had enough of a monopoly, where they became the scumbag company they're known as today.

----

## Preface

>[!note]
>This post is directed towards anyone who uses Bluesky because they think it's "open", "decentralized," "billionaire-proof," or "the future of social media." I wrote this because I'm tired of people talking about ATProto like it's the future when it really changes nothing.

There are two kinds of ways people interact with others on the Internet. Communication networks and social networks. The latter have all fallen into disarray and become giant dumpster fires their inhabitants are blissfully unaware of or choose to ignore.

![A guy with a "cool" cap standing across from an X (Twitter) logo saying "I LOVE CHILD PORN" and a person next to them saying "Look man, this is where all my friends are and I get more likes and views here. Yeah it's all bots and all but this is the only place that gives me attention and-"](posts/bluesky/twitter1.png "Priorities.")

However, in the wake of Musk taking over Twitter[^1], a (relatively) small group of users left. Spurred on by this, a bunch of new companies sprung up to fight for their attention. Most were forgotten and architecturally the same as the site they were trying to replace.

![A page showing various screenshots of the Hive mobile app with text in the center saying "Socialize on Hive Social"](posts/bluesky/hive.png "Anyone remember Hive?")

However, Twitter would not be defeated so easily. All the way back in 2019, Jack Dorsey had a brilliant idea.

> Twitter is funding a small independent team of up to five open source architects, engineers, and designers to develop an open and decentralized standard for social media. The goal is for Twitter to ultimately be a client of this standard. 🧵
>
>\- [Jack Dorsey, Twitter](https://xcancel.com/jack/status/1204766078468911106)

Eventually, Jay Graber would split the project off from Twitter, becoming the founder and CEO of the project's new identity, the <abbr title="Public Benefit Limited Liability Corporation">PBLLC</abbr> known simply as Bluesky.

From there the company began operating on an invite system and wasn't actually decentralized in any respect. Everyone who had been attacked by Twitter users both before and after Musk felt welcome. However, the first red flags presented themselves during this time. Bluesky took the same path as other {{< nutshell title="blitzscaled" href="#blitzscaling" >}} corporations, raising a ton of [venture capital money](https://bsky.social/about/blog/7-05-2023-business-plan) from a firm called [Neo](https://neo.com). Then, the public launch hit, ATProto exploded in popularity as "Twitter without Elon" and we arrive at the present.

## "The Interface Problem"

>[!tip]- Terminology
>Shortened from the official [gloassary](https://atproto.com/guides/glossary).
><dt>PDS</dt>
><dd>A <b>P</b>ersonal <b>D</b>ata <b>S</b>erver, holds user data and activity like posts. The majority are hosted by Bluesky PBC.</dd>
><dt>Relay</dt>
><dd>Indexes all the PDSes to create the <b>Firehose</b>, an aggregation of all data passing through the network. Not required, but useful at scale or to quickly join an AppView to the whole network.
><dt>AppView</dt>
><dd>The API that ingests data from the PDS. It fetches your user data from your PDS, and other activity from the Firehose. Apps can then fetch data from these AppViews. The most popular is `api.bsky.app`.</dd>
{icon="book-open"}

Here's how ATProto is typically pictured:

![OAuth2 diagram](posts/bluesky/diagram-oauth.webp "[Source](https://atproto.com/guides/applications#step-2-signing-in-with-o-auth)")

Or, for a more general setup:

{{< mermaid >}}
flowchart LR
A[(User PDS)] <--> B[(Relay)]
B <-- Firehose --> C(AppView)
{{< /mermaid >}}

<noscript>
<img src="/mermaid/1.png" alt="User PDS <--> Relay <--> AppView">
</noscript>

However, in practice the network really operates like this:

{{< mermaid >}}
flowchart TD
A[(User PDS)]
B[(Relay)]
C(AppView)
C -- Firehose --> B
subgraph 1 [Hidden]
B <--> A
B <--> D[(User PDS)]
B <--> E[(User PDS)]
end
{{< /mermaid >}}

<noscript>
<img src="/mermaid/2.png" alt="User PDS <--> Relay <-- AppView, the non-AppView layers are hidden">
</noscript>

Everything propagates from the AppView downwards, because that's all users ever interact with. You could swap out the lower layers completely and nobody would notice, nobody who uses the network cares about or even uses the lower layers. According to [Are We Decentralized Yet?](https://arewedecentralizedyet.online), at the time of writing, Bluesky's PDSes hold 99.37% of ATProto's userbase. You are automatically put on a Bluesky PDS when signing up through the main AppView, [bsky.app](https://bsky.app).

<video controls muted playsinline alt="Bluesky signup flow, you have to click a small pencil icon next to small text, then switch to the Custom option, where you're expected to just know a URL to a PDS">
<source src="/vid/bluesky/bskysignup.webm" type="video/webm">
Alt: Bluesky signup flow, you have to click a small pencil icon next to small text, then switch to the Custom option, where you're expected to just know a URL to a PDS
Your browser either does not support the video tag or the VP9 codec.
</video>
<figcaption>Not only is that text small, I have no idea what other servers there are and this tells me nothing.</figcaption>

The typical defence is that other PDS hosts run their own webapps where people can sign up to that PDS host, but most people are still exposed to ATProto through Bluesky's landing page and branding, which takes them to [bsky.app](https://bsky.app). The fact that they don't advertise alternative options there doesn't inspire confidence in the company or its shareholders.

Large webapps are very familiar to people (like Twitter or Reddit are to their userbase), and it'd be very difficult to convince people to leave if Bluesky decided to make unfavorable changes simply because that webapp is familiar.

Most apps also ingest data from the main AppView, `api.bsky.app`, which most PDSes proxy data to.

This "interface problem" is a layer of centralization present in ATProto (and crypto-powered stuff too) that nobody really thinks about. The AppView is what brings everything together, putting enormous power in the hands of AppView and webapp operators. Operators can hide, edit, or promote things at their leisure, and if they're the main AppView that PDSes connect to, they're screwed.

AppViews also serve far more users than a simple federated instance, meaning any changes or downtime have far wider ramifications than just affecting one group of users.

### Decentralized Network, Centralized Terms

An example of this kind of control is how decisions made by Bluesky Trust & Safety affect the network. According to Bluesky's [moderation blog post](https://bsky.social/about/blog/03-12-2024-stackable-moderation):

> **What do I need to do to moderate my own community on Bluesky?**
>
>All users of Bluesky’s client app are subscribed by default to Bluesky’s moderation. If you would like to run a moderation service that layers on top of these defaults, you can create a new account for that new service and get it up and running with Ozone.
>
>However, if you want to opt out of our defaults, this is still possible — we believe it’s important to give users the right to leave and not lock you in. You would need to use or develop a separate client app that connects to the AT Protocol, but this option gives you full flexibility to implement your own moderation system from the ground up.

One can make a safe assumption that most users interact with the network through the official web and mobile clients due to their marketing and longevity (they're the first AppViews), which cannot opt out of Bluesky's moderation.

>Our Right to Terminate. We may suspend, restrict, or terminate your Account—or specific features of Bluesky—at any time, without prior notice, if:
>
>    You violate these Terms, the Privacy Policy, Community Guidelines, or Copyright Policy;
>    We are legally required to do so, such as by court order or regulatory demand; or
>    We believe that your continued access poses a risk to Bluesky, to other users, or to third parties, including in cases involving safety, legal exposure, reputational risk, or platform integrity.
>
>\- [TOS](https://bsky.social/about/support/tos)

These clients also have to agree to the brilliant Bluesky TOS and Privacy Policy. Since legalese makes everyone go to sleep, the TOS;DR contributors have made [a summary](https://edit.tosdr.org/services/10752), here are the fun points:

![Visit https://edit.tosdr.org/services/10752](posts/bluesky/tosdr2.png "The quotes do exist, just in different wording.")

![Visit https://edit.tosdr.org/services/10752](posts/bluesky/tosdr.png "Pending additions can't be viewed by unauthenticated users :(")

>[!quote]- Full quotes for the claims
>>11. Indemnification
>>
>>Summary: If you break the rules or cause problems on Bluesky, you might have to pay for and help us solve any complaints or legal issues that come up.
>>
>>You agree to indemnify, defend, and hold harmless Bluesky, its affiliates, and their respective officers, directors, employees, and agents (collectively, the “Bluesky Parties”) from and against any and all claims, disputes, demands, liabilities, damages, losses, and expenses—including reasonable legal and accounting fees—arising out of or in any way related to:
>>
>>    Your access to or use of Bluesky Social;
>>
>>    Your User Content;
>>
>>    Your violation of these Terms or any other applicable Bluesky policies;
>>
>>    Any actions you take through or in connection with our services; or
>>
>>    Your violation of any law or the rights of a third party.
>>
>>Bluesky reserves the right to assume the exclusive defense and control of any matter subject to indemnification by you. If we do, you agree to fully cooperate with our defense of the claim.
>>
>> [...]
>>
>>iv. Waiver of Class Actions. TO THE EXTENT PERMITTED BY APPLICABLE LAW, YOU AND BLUESKY AGREE THAT EACH MAY BRING CLAIMS AGAINST THE OTHER ONLY IN YOUR OR ITS INDIVIDUAL CAPACITY, AND NOT AS A PLAINTIFF, CLASS MEMBER, OR REPRESENTATIVE IN ANY PURPORTED CLASS, COLLECTIVE, OR REPRESENTATIVE PROCEEDING.
>>
>>\- [TOS](https://bsky.social/about/support/tos)
>
>>ii. Cookies (and Other Technologies). We and third parties that provide content or other functionality on Bluesky may use cookies, pixel tags, and other technologies ("Tracking Technologies") to automatically collect information. See Section 9, Cookies, for more information.
>>
>>
>>[...]
>>
>>B. For Administrative Purposes. We use personal information for various administrative purposes, such as:
>>
>> i. Pursuing our legitimate interests like direct marketing, research and development (including marketing research), network and information security, and fraud prevention;
>>
>>[...]
>>
>>Sharing to Protect Us or Others. We may access, preserve, and disclose any information we store if we, in good faith, believe doing so is required or appropriate to: (i) comply with law enforcement, regulatory, or national security requests and legal process, like a court order or subpoena; (ii) protect your, our, or others' rights, property, or safety; (iii) enforce our policies or contracts; (iv) collect amounts owed to us; or (v) assist with an investigation or prosecution of suspected or actual illegal activity.
>>
>>
>>[...]
>>
>>Disclosure of Personal Data. As detailed in Section 11, How We Share your Personal Data, we may disclose the categories of Personal Data identified above to the following categories of third parties for various business purposes: other Bluesky companies, service providers, our professional advisers, business partners, other businesses as needed to provide our Services, and certain third parties where you have provided consent, where it is in connection with a corporate transaction, or where we are required by law or in connection with other legal process.
>>
>>[...]
>>
>>iv. Service Providers. We may share Personal Data with our third-party service providers and vendors. This includes service providers and vendors that provide us with IT support, hosting, payment processing, customer service, and related services.
>>
>>v. Business Partners. We may share Personal Data with our business partners to provide you with a product or service you have requested. We may also share your personal information with business partners with whom we jointly offer products or services.
>>
>>[...]
>>
>>D. Sharing to obtain Professional Services. We may share Personal Data with our legal advisors, bankers, auditors, accountants, consultants, and insurers. Our professional advisors will process Personal Data as necessary to provide their services to us.
>>
>>
>>[...]
>>
>>We may transfer, process, and store all personal information we collect anywhere in the world. Different countries have different data protection laws.
>>
>>If we transfer personal information from the European Economic Area, Switzerland, Brazil and/or the United Kingdom to a country that does not provide an adequate level of protection under applicable data protection laws, we will do so (i) using appropriate safeguards; (ii) based on safeguards like the European Commission-approved, UK Government-approved, or Brazil’s Data Protection Authority Standard Contractual Clauses or Addenda; or (iii) otherwise in accordance with applicable data protection laws.
>>
>>For more information about the safeguards we use for international transfers of your personal information, please contact us as set forth below.
>>
>>\- [Privacy Policy](https://bsky.social/about/support/privacy-policy)

These policies aren't very open or user-friendly, and are much closer to those of social media sites like Twitter. Bluesky has exercised their unfair power to nuke certain posts into orbit. 

### Centralized "Moderation"

Bluesky does not enforce its community guidelines equally and has completely failed [Black](https://techcrunch.com/2023/06/08/blueskys-growing-pains-strain-relationship-with-its-black-community-moderation/) and [trans](https://www.nbcnews.com/tech/social-media/bluesky-growing-pains-rcna181029) users. Bluesky's moderation list can silence any user it deems unfit to post, even those using other PDSes. Considering the CEO's erratic behavior and the habits of the head of Bluesky T&S, this is not good:

![A pair of two posts from Jay Graber, the CEO of Bluesky. In first, she says "You could try a poster’s strike. I hear that works." In the second, she replied "Are you paying us? Where?" to someone saying "Yeah but a customer threatening to cancel their service usually gets a couple things accomplished. C'mon, Jay. Shame on you."](posts/bluesky/jay.png "[Source](https://stefanbohacek.online/@stefan/115311658328349605)")

In response to Bluesky not banning the prolific transphobe Jessie Singal, [Juni](https://bsky.app/profile/did:plc:wpp4lklhvmopw6zcy6qb42ru) made a bot to track the activity of the head of Bluesky T&S, [Aaron Rodericks](https://bsky.app/profile/aaron.bsky.team).

![A post from an account called "What's our head of T&S doing?", it has written "Aaron [Rodericks] liked:" and attached a post from a porn bot that reposts stolen "teen" content](posts/bluesky/headofts.jpg "Caught white-handed. That bot and its author were [promptly banned](https://bsky.app/profile/reminder-bot.juni-is.gay/post/3ldpw5vh3mk2l). [Source](https://bsky.app/profile/cait.siorc.eu/post/3lvbxjar2ak2c)")

![A Bluesky thread. Jay says "Too real. We're going to try to fix this. Social media doesn't have to be this way." A user responds "have y'all banned Jessie Singal yet or" Jay responds with "WAFFLES"](posts/bluesky/jessiesingal.jpg "This started a lot of literal waffle-posting from Jay, a very tone-deaf response considering the situation.")

They've also banned a long-time Black member of Bluesky for criticizing Jay, and he could no longer access any ATProto services since his PDS was hosted by Bluesky.

Another example of Bluesky's moderation is how the first post about an AI-generated video criticizing Trump and Musk playing inside a government building was removed. It was [purged from the platform completely](https://www.404media.co/bluesky-deletes-ai-protest-video-of-trump-sucking-musks-toes-calls-it-non-consensual-explicit-material/), including reposts. It was done for being non-consensual explicit material (something that's allowed when criticizing the rich and powerful, and the poster didn't even make the video playing on the TV). Bluesky did actually reinstate the post, but this was likely due to pressure from the poster as it was gone for a long time. You should not have to deal with a centralized moderation service like this on a supposedly decentralized network, ever.

![A Bluesky account you control (@marisakabas.bsky.social) posted content or shared a link that contains non-consensual explicit material, which is in violation of our Community Guidelines. As a result of this violation, we have taken down your post,” an email Kabas received from Bluesky moderation reads. “We trust that you will understand the necessity of these measures and the gravity of the situation. Bluesky explicitly prohibits the sharing of non-consensual sexual media. You cannot use Bluesky to break the law or cause harm to others. All users must be treated with respect.](posts/bluesky/fuckyou.png "Thou shalt not criticize our Lord and Savior Donald J. Trump or the (former) Right Hand of God Elon Musk.")

A longer and more detailed explanation of this was written up by [Nico Mara-McKay](https://scribe.rip/@plutopsyche/blueskys-ceo-meltdown-how-leadership-continues-to-fail-its-most-marginalized-users-8bfa7a8824b4).

DMs are also hosted separately and aren't encrypted.

>Direct Messages are Private. Content you sent to another Bluesky user through Direct Messages is private between you and the user(s). If you’ve shared this information through a third-party service, the information may be visible to them. DMs may be accessed by moderators when reported in-app, or by Bluesky Trust and Safety staff investigations into significant violations of the Community Guidelines.
>
>\- [Network Services Policy](https://bsky.social/about/support/network-services-privacy-policy)


### PLCs: Centralized Instance Identifiers

Most links to Bluesky profiles use the `did:plc` instead of the `did:web` or `profile` syntax. A PLC is a persistent ID that points to your profile regardless of username changes, intended to be more resilient than a username. It uses a keypair to tie a PLC to a user account. There is one and only one PLC [directory](https://web.plc.directory), which Bluesky PBLLC has full control over. They can choose to invalidate every single link to your profile or posts from every app at any time.

`did:web` is a more decentralized but less resilient option, which just links directly to your username. However, you must be careful because you only have one shot at this. If you need to delete your account and start over (which will probably happen because the documentation is horrid and missing important steps), your PDS will be ["burned"](https://github.com/bluesky-social/atproto/issues/3455) by Bluesky's AppView and will become completely inaccessible. Nobody on Bluesky can see it, and its owner cannot log in. This happened to one user, who only got it fixed by manual intervention because someone at Bluesky saw their [blog post](https://notes.nora.codes/atproto-again/) about it on Hacker News.

If you ever need to recreate a `did:web` for other purposes, this [fails too](https://github.com/bluesky-social/atproto/issues/3143).

This issue also seems to affect alternate AppViews like Blacksky as well.

## Not for communication

(this section was inspired by [Ploum's](https://fr.wikipedia.org/wiki/Lionel_Dricot) critiques of {{< nutshell title="our loss of communication" href="https://ploum.net/2025-12-15-communication-entertainment.html" >}})

Now let's circle back to communication networks.

I want to propose a small thought experiment. What if, instead of being able to just *send* an e-mail to a friend, you had to login to their e-mail provider's server with your e-mail address to then send them a message. Wouldn't it be easier for both parties to be able to send an e-mail to each other from their own respective servers? ATProto proposes that the former is better because each mail host could tailor a specific experience, ensuring that e-mail is not one universal thing but instead whatever each host says it is.

![Text-based e-mail client Elm. Shows a simple list on black and white, similar to the `parted` tool, along with BBS-style keyboard navigation](posts/bluesky/Elm.png "By Dave Taylor - http://www.slackbook.org/html/basic-network-commands-email.html, BSD, https://commons.wikimedia.org/w/index.php?curid=11100225")

In reality, e-mail is the most popular and robust decentralized network we've ever built because e-mail itself is universal. What do you need to do to be able to send and receive e-mail? All you need is a mailserver (which you can run yourself) and an e-mail client. There are many servers and clients, but they can all send e-mail to each other because the underlying communication system remains the same. they all send e-mail over SMTP. All servers (ideally) use IMAP, POP3, or JMAP to allow clients to connect. It doesn't matter if your client looks like the one above, it's all e-mail in the end.

E-mail itself consists of headers, text (usually HTML), and attachments. This does not change based on one's server or client. E-mail is not a short plaintext post one day, short form video the next, and a git repo the third. Its format is simple enough that it can send a lot of things, while remaining consistent. You can do pretty much anything with HTML and attachments in an e-mail.

ATProto misses the point entirely, instead creating a band-aid fix for a problem Big Tech created. The "one account per site" metaphor, which was originally created to keep users captive, is so strong it even {{< nutshell title="permeates the Fediverse" href="https://ploum.net/2025-12-04-pixelfed-against-fediverse.html" >}} and hinders its development as a communication protocol (looking at you, Daniel Supernault, Framasoft, and the Lemmy & Piefed teams). ATProto is a glorified {{< nutshell title="SSO" href="https://en.wikipedia.org/wiki/Single_sign-on" >}} system, so users are still creating accounts on a million different sites, just using their PDS instead of their e-mail and password.

And if you had to login to your recipient's mailserver for e-mail, wouldn't it be easiest for everyone to just use one mailserver? Those with other mailservers could just login to GMail and send messages to their friends because it's the biggest mailserver and it's easier for most people. This is exactly the purpose that [bsky.app](https://bsky.app) serves. 

In real life, many people self-host their own e-mail servers and mailing lists, and there are several commercial e-mail providers you can choose from as well.

Another detail with ATProto is that posts just get lost. If you use [bsky.app](https://bsky.app), you can't directly view Tangled repos or Leaflet blogs (as in the full content, not just a link) and vice versa (Leaflet doesn't let you follow Bluesky accounts and use that as your only feed). This is data loss at a fundamental level. It does not matter if the data is in your PDS when you need two different apps connecting to one unified AppView to see two different data sets[^2]. ATProto is no more connected than Twitter and Instagram.


### "Television 2.0"

>Communication networks are not profitable. Social networks are entertainment platforms, media consumption protocols. Historically, they disguised themselves as communication platforms to attract users and keep them captive.
>
>The point was never to avoid missing a message sent from a fellow human being. The point was always to fill your time with "content."
>
>We dreamed of decentralised social networks as "email 2.0." They truly are "television 2.0."
>
>\- Ploum, [How We Lost Communication to Entertainment](https://ploum.net/2025-12-15-communication-entertainment.html) (text licensed under [CC BY-SA](https://creativecommons.org/licenses/by-sa/4.0/deed.en))

Bluesky loves to claim that it is open. However, anybody who believes that hogwash has never seen the failures of Silicon Valley blitzscaling. The company owns the entire network, and there's no wordplay that you can use to change that. Their commanding presence is not a current issue or an accident. It's entirely intentional. Neo did not give them money to build something that would ultimately lose them money. 

These people funded Notion and several AI startups, they are not in the market for open protocols. The leadership operates like any other startup in the Valley, complete with the aforementioned narcissism and extreme focus on growth, seed funding from Venture Capital firms, and a focus on looks and marketing over function. 


![Go to https://www.germnetwork.com](posts/bluesky/germ.png "Looks like yet another messenger. Routes <abbr title='End-to-End Encrypted'>E2EE</abbr> messages through its own servers.")

![Go to https://sifted.app](posts/bluesky/sifted.png "Yet another video app. If the word ATProto wasn't here I'd have no idea.")


Every ATProto app copies this philosophy too, often including fancy marketing pages and prominently featuring some website or mobile app download first instead of focusing on the ATProto side. The "download" or "get early access" button is highlighted above all else. They might even have a button that says "Login with Bluesky," yet another brilliant sign that ATProto really isn't about being open. They often also try to own the words "decentralized" and "open" (as in "decentralized social networks" or "open social") like the crypto bros before them.

Now here's the landing page for [Mastodon](https://joinmastodon.org), a leading Fediverse software for microblogging:

![Go to https://joinmastodon.org](posts/bluesky/mastodon.png "Notice the difference?")

It is not an app, it has *apps*. It is not a unified platform, it has *servers*. It is not a flashy new product, it is a *server software* first and foremost. The site is different from the other two in every way and doesn't even include the words "Fediverse" or "ActivityPub" until much further down the page.

ATProto apps copy the intent of their parent platform: content.

They're all about providing more *content*. It's not about communication, it's not about simplicity, it's about being first to market, being as flashy and "new wave" as possible. Each of these must generate more content for people to consume, and the company that owns everyone's accounts *and* the primary interface with the network will eventually be able to profit from it all.

They also chose to incorporate as a for-profit. Bluesky is a PBC, which according to Brittanica has the following mission:

>The rise of PBCs reflects a shift in how some businesses view their role in society. Rather than focusing solely on maximizing shareholder returns, PBCs integrate long-term considerations for stakeholders including employees, customers, and communities. These businesses are structured to take a more active role in addressing pressing global challenges while maintaining financial sustainability.
>
>\- [Encyclopedia Brittanica](https://www.britannica.com/money/what-is-a-public-benefit-corporation)

However, PBLLCs in Delaware (where Bluesky is incorporated) are not subject to any special requirements compared to standard LLCs. Bluesky is also not a certified [B Corporation](https://www.bcorporation.net/en-us/standards/) (though this wouldn't mean too much anyway because bribery works wonders) and does not even publish <abbr title="A report PBCs should publish about how they help their stakeholders.">benefit reports</abbr>. Therefore, the PBLLC moniker means absolutely nothing and is a complete marketing ploy to get you to think they care about their users. In contrast, Mastodon is a registered nonprofit in the U.S. (but had its nonprofit status [revoked in Germany](https://blog.joinmastodon.org/2024/04/mastodon-forms-new-u.s.-non-profit/) for unknown reasons), and the <abbr title="ATProto username system">DID</abbr> and ActivityPub protocols were made by the nonprofit W3C.

Bluesky has every incentive to make fat stacks of cash off of the whole network they spawned. Their Firehose is a centralized infinite stream of pure content that they could sell to AI companies (though right now they can just take it for free). Their web client is a prime spot for ads and other bad changes. Their userbase on their PDSes is a prime resource they could monetize. Their PDS implementation is the most used PDS software and hardcodes their AppView already.

![The Postal Dude doing a middle finger with the caption "FUCK YOU"](posts/bluesky/postaldude.png "Bluesky to every single user.")

Their Terms Of Service and Privacy Policy are extremely malleable. DMs are still not on ATProto, locking people into Bluesky's web client for them (they can also be, you know, *read by anyone at Bluesky*). Every Silicon Valley startup has had to face the difficult task of monetizing or risking bankruptcy.

The question is not if, but when.

Though, people will surely leave if things get bad, right? There are even migration services to the Fediverse! Well, DoorDash is still the most popular food delivery app in the world. Twitter is still as large as ever. People are familiar with the apps they like and don't leave no matter how bad things get (as long as Bluesky sticks to the Google playbook and goes slowly).

>My own interpretation is that social media users don’t mind losing messages because they were raised on algorithmic platforms that did that all the time. They don’t see the point in trusting a platform because they never experienced a trusted means of communication.
>
>    {{< nutshell title="Facebook m’a rendu injoignable (ploum.net)" href="https://ploum.net/facebook-ma-rendu-injoignable/index.html" >}}
>
>Now that I write it, it may also explain why instant messaging became the dominant communication medium: because if you don’t receive an immediate answer, you don’t even trust the recipient to have received your messages. In fact, even if the message was received, you don’t even trust the recipient's attention span to remember the message.
>
>\- Ploum, [How We Lost Communication to Entertainment](https://ploum.net/2025-12-15-communication-entertainment.html) (text licensed under [CC BY-SA](https://creativecommons.org/licenses/by-sa/4.0/deed.en))

Some neckbeards may even wonder how such a platform and mindset even got popular in the first place. The simple answer is that communication protocols are boring. Simple websites and RSS are boring. E-mail is boring. A. Square wrote on his gemlog comparing social media feeds to food:

>When you eat a wholesome meal, you don't just enjoy the tastes (and textures, and aromas) of food. You also derive nutrition from the food, and eventually, having eaten enough to satisfy your body's needs, you feel satiated and stop eating. Highly processed snacks have poor nutritional value, so you can keep stuffing more and more of them into your face-hole. Because they don't contain much of what your body needs, some nutritional needs are going to remain unfulfilled, and therefore your body will not give you the signal that says "that's enough, you can stop now".
>
>\- A. Square, {{< gemini title="'Social' Media is Unsatisfying" href="asquare.srht.site/gemlog/socmedia_satisfaction.gmi" >}}

Communication networks are a wholesome meal that satisfies you, social networks are like a bag of potato chips. You eat a whole bag in one sitting, never satisified, and are left wondering where the time went.

>Facebook makes virtually all its money by showing ads to people.
>
>* The more ads they show, the more money they make.
>* The longer you stay on the site, the more ads they show.
>* The longer you stay on the site, the more money they make.
>
>\- Beej, {{< gemini title="On Social Media" href="gem.sdf.org/beej/blog/2025-01-10-socialmedia.gmi" >}}

## Conclusion

![Two pixelated businesspeople, one smiling in a blue suit, the other smirking in a grey suit. One says to the other: 'So you’re saying we can just add a bunch of words to a website and people will think we’re socially-minded geniuses?'](posts/bluesky/words.png "Image from [Death Generator](https://deathgenerator.com), using assets from [SOFEL](https://en.wikipedia.org/wiki/SOFEL).")

Bluesky doesn't change a thing from the networks it claims to be different from. It is not a novel open network, and simply propagates the problems of Silicon Valley startup grifting, social media division, corporate control, and {{< nutshell title="corporate Open Source." href="https://ploum.net/2023-06-19-more-rms.html" >}} It does not connect anyone, it is not billionaire proof, and every single user is being slow-cooked like an ignorant frog.

It is not good just because it has certain kinds of people on it. It is not good just because it is flashy. It is not good just because it has one clear face. It is not good just because it has one Github organization.

It is a complete lie. Decentralization theater created so companies and developers can weasel out of needing to build or support actual open and interoperable networks, while still being able to claim the "decentralized" moniker because the PDS network is *technically* decentralized.

People should focus on building things that are actually interoperable and useful.

## Appendix A: The Fediverse

<div style="position: relative; padding-top: 56.25%;"><iframe title="Mastodon in 180 Seconds 🐘" width="100%" height="100%" src="https://tilvids.com/videos/embed/wx2iLhD3pTipbKFJKLyx5t?subtitle=en&amp;warningTitle=0" frameborder="0" allowfullscreen="" sandbox="allow-same-origin allow-scripts allow-popups allow-forms" style="position: absolute; inset: 0px;"></iframe></div>
<figcaption>Small video primer for Mastodon specifically, but explains hpw the Fediverse works in general.</figcaption>

Bluesky claims to be billionaire free, but the Fediverse really is. It also neatly solves the interface problem as every server has its own UI. Developers develop server software, not "apps." They have far less power than they do on ATProto since other people still have to set up that server software and run it.

However, the Fediverse isn't perfect. Any instance could get big and take over, and some server software doesn't respect the spec. Pixelfed and Loops drop posts that aren't images or video respectively. Lemmy and PeerTube discard anything that isn't from other Lemmy and PeerTube servers. [ForgeFed](https://forgefed.org) will probably disregard everything that isn't Git activity too[^3]. However, all the microblogging options are interoperable, and all support alternate Mastodon clients. You can subscribe to Peertube channels, Pixelfed accounts, Discourse forum categories, Sublemmys, Ghost and Wordpress blogs (which post the full text!), and more from Mastodon or any other microblogging Fediverse software.

This is the closest we've ever come to e-mail 2.0. No one large server dominates (Threads has next to no presence at all, mastodon.social only has about 20% of users), and moderation and rules are instance-specific, so on smaller instances you can get to know your mods and admins as human beings. Software landing pages prominently feature other servers you can sign up to as well.

If you delete your database and reinstall your server (and it had posts), you won't be able to federate again as other servers can't verify your server's identity. This only hurts the servers that federate with you and can be worked over with other admins. It does not bar you from the entire network.

I don't think it would be impossible to make the Fediverse more interoperable, efforts here would be better-spent than efforts to continue the charade that is ATProto.

If you're inerested, you can get started here: https://fedidb.com/welcome


[^1]: I will be calling 𝕏 Twitter because its problems did not start when Musk took it over, they've been present since its creation.

[^2]: PDS explorers aren't actual social networks and present PDS data in a raw, unstructured form. You also can't interact with the data (reply, fork, follow, star, etc) from their interfaces.

[^3]: Yes, it is still better than Tangled because it integrates into existing <abbr title="Github, Gitlab, Codeberg, Forgejo, etc.">git forges</abbr> which are already very stable, secure, and familiar. It also doesn't encourage everyone to sign up for yet another centralized account host (tngld.sh), and will have working issue and PR flows (no pasting `git patch` output into a window).
