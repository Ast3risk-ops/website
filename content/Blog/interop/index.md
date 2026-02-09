+++
title = 'On Interoperability'
description = 'Interopability is more than just two web UIs.'
date = 2026-02-09T15:30:18-04:00
draft = false
tags = ['Bluesky', 'Fediverse']
type = 'post'
series = ["Bluesky"]
series_order = 2
+++

<!--more-->

[Cover image](https://commons.wikimedia.org/w/index.php?curid=3712503) by <a href="https://en.wikipedia.org/wiki/User:Audriusa" class="extiw" title="en:User:Audriusa">Audriusa</a> at <a class="external text" href="https://en.wikipedia.org">English Wikipedia</a>, licensed under <a href="http://creativecommons.org/licenses/by-sa/3.0/" title="Creative Commons Attribution-Share Alike 3.0">CC BY-SA 3.0</a>.

-------

(Bit of a short one, but I felt it had to be said)

You may have heard about the [integration](https://notes.cosmik.network/3me2iifnwic2x)[^1] of the web-annotation services [Semble](https://semble.so) and [Margin](https://margin.at).

They linked this brilliant analysis by an """experience designer""" named Tynan Purdy:

!['The killer app of ATProto is interop', said in response to a post about the Margin+Semble integration](posts/interop/tynan.png)

Unfortunately, people that say this don't understand what true interopability even is.

This was a manual effort by two developers to coordinate their Lexicons and web UIs. Real interoperability is innate and part of a shared spec.

As I explained in my [previous post](../atproto-is-a-lie), e-mail is interoperable by design. All clients and all servers use one shared {{< nutshell title="SMTP" href="https://en.wikipedia.org/wiki/Simple_Mail_Transfer_Protocol" >}} protocol to send e-mail, and either {{< nutshell title="IMAP" href="https://en.wikipedia.org/wiki/Internet_Message_Access_Protocol" >}} or {{< nutshell title="POP3" href="https://en.wikipedia.org/wiki/Post_Office_Protocol" >}} to read it. If a client or server does not support SMTP, it is breaking the spec and will not be supported. There is no need for clients to manually support each other, because they all use the same shared protocol.

The Fediverse is no exception. All "types" of servers are at the very least interoperable with servers of the same type. However, the spec makes interoperability between different server types possible, and software like Mastodon or Pixelfed actually tries to fulfill that. 

From Mastodon, Pixelfed or any other microblogging Fediverse software, you can follow: Lemmy/Piefed groups, PeerTube channels, Discourse forum categories, Flipboard accounts, Ghost/Wordpress/Micro.blog/WriteFreely blogs, Pixelfed accounts, bridged Bluesky accounts, accounts from other microblogging software (duh), Mobilizon events, Funkwhale music, Castopod podcasts, and more. 

These also aren't just webapps, but full server software that many people run. ActivityPub software is expected to have at least a basic level of interoperabiliy for publishing (subscribing is another matter, as Ploum points out in a section of his article on {{< nutshell title="our loss of communication" href="https://ploum.net/2025-12-15-communication-entertainment.html#the-lost-messages" >}}), published content should be visible and interactable from other server software. The results of this show.

You can have one account that can reach everything from your server, with no extra effort from the developer of your server software or any other. The shared spec is what provides interopability here. It's not perfect as it is right now, but that's a solvable problem.

The cover image for this article demonstrates this well:

![Interoperability: playing the two role network game (dots and boxes), where one of the player clients (top left) runs under Sun Microsystems and another under GNU Classpath with JamVM. The applications execute the same bytecode and interoperate using the standard RMI-IIOP messages for communication.](featured.png)

This really old photo shows two programs on two different virtualized systems communicating using a shared protocol. Neither client had to specifically support the other, the underlying protocol did all the work. 

ATProto Lexicons allow each app to define its own storage systems, and therefore, its own spec. There is no shared system to make interoperability automatic. Like adding support for random NFTs to a video game, it's a manual effort each time. Nothing is automatically interoperable and discoverable.

E-mail, IRC, and the Fediverse all had interoperability for a long time before the venture capital blitzscalers decided they wanted to reinvent the wheel and make it worse. With a manual effort system you can't account for every single app, and a shared Lexicon wouldn't work too well for other kinds of apps. A better underlying protocol with a shared spec is needed for true interoperability.



[^1]: Their blog is hosted on Leaflet (even if the data is on their PDS it is only accessible via Leaflet or a PDS explorer), because of course it is. None of this is actually decentralized.
