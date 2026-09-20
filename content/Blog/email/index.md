+++
title = 'I got an E-mail'
date = 2026-09-20T10:21:37-04:00
draft = true
type = 'post'
description = "I got an e-mail."
tags = ['Personal Experience', 'Crypto', 'AI']
+++

<!--more-->

Photo by <a href="https://unsplash.com/@thanospal">Thanos Pal</a> on <a href="https://unsplash.com/photos/low-angle-photography-of-building-P-ZdIItfUm4">Unsplash</a>

## Prelude


I've started to get spam e-mails more and more since I started actually publishing stuff to Github, and this one stood out to me:

![Greetings Ast3risk-ops! I came across your github (and your stars) and I thought you might like building with us =) I'm putting together a virtual, invite-only hackathon for people building for creators - mostly decentralized communities of musicians, writers / publishers and fediverse people. This includes people interested in Ghost, Jellyfin, Mastodon, Peertube, Owncast, and their friends / neighbors. We will have ~$50k in cash (or their equivalents) to distribute as prizes, grants and challenges! You may be new to crypto and that is fine, we just want you to build something beautiful and useful for these open source communities =) The event will be virtual and from June 15 – June 29, 2026. The invite link is here (please don't share broadly): https://######## — the required passphrase is #########. A few ideas worth exploring, to give you a simple set of examples: 1. Pay the artists you actually played. Streaming platforms pool every subscription and pay out pro-rata, so your money mostly funds whoever is globally popular, not who you listened to. A self-hosted server like navidrome/navidrome already keeps your honest play history. The hack: user-centric royalties on top of the server, where your monthly amount is split only across the artists you actually played and settled to them directly. The majors have refused this for years; direct sub-cent settlement makes it the easy default. https://github.com/navidrome/navidrome 2. Royalties that follow a work back through everyone who made it. A remix of a remix should pay every ancestor, and an edited photo should pay the original photographer. The lineage already exists as data: beetbox/beets and metabrainz/picard hold track credits and provenance, immich-app/immich holds photo origins. Read that graph, make it the payout rule, and attribution metadata becomes settlement logic — a six-way split of a $0.25 license is worth doing when the fee is a fraction of a cent. https://github.com/immich-app/immich 3. Pay for the seconds you were there. The hack: continuous-authorization streaming, where a viewer approves a spending rate instead of a price, and a show on owncast/owncast or chocobozzz/peertube bills per second watched — revenue accruing in real time and splitting live across everyone on the stream. Leave at any second and you've paid for exactly the time you were present. Streaming payments are a real gap in the x402 world, so the base layer is open ground. https://github.com/owncast/owncast There are several more worked angles on the site, plus a list of open-source communities that already have the audience and just need a payments layer! We'll have a ton of sponsors, awards, prizes, and giveaways! If you're around, we'd love to have you. Canteen is a community of passionate builders, investors, and operators in NYC — open invite to visit us if you're ever around =) Cheers! The team at Canteen https://thecanteenapp.com/ Flatiron, NYC * Please reply with "do not contact" if you do not want to hear from us.](posts/email/email.png "Hiding the password because I don't want anybody to actually sign up. [Event link](https://luma.com/5xcrazms)")

This e-mail is a jumble of nonsensical buzzwords that don't make sense. I assumed the company behind it would be a boring spamblog but there was something a little more interesting here.

Firstly, this was a real hackathon sponsored by Circle (creators of the USDC token, AKA the new {{< nutshell title="Eurodollar" href="https://en.wikipedia.org/wiki/Eurodollar#History" >}}), and the firm behind the event was seemingly staffed by the most despised individuals in our society (and probably some AI co-writers), crypto techbros. The [second blog post](https://thecanteenapp.com/analysis/2026/05/01/unbundling-the-prediction-market-stack.html) on their website was doing a serious technical analysis of Polymarket filled with more jargon than a coked-up C-suite executive.

Here's the intro:

> Three days ago, on April 28, 2026, two unrelated venues shipped breaking protocol upgrades within hours of each other. Polymarket migrated its CLOB to a new contract suite — the Polymarket V2 framework — and Pump.fun pushed a `BREAKING_FEE_RECIPIENT` program upgrade that re-routed creator fees through a new mechanism. The synchrony is a coincidence. What’s not a coincidence is that both upgrades pointed in the same direction: on-chain CLOB-style trading venues are unbundling into distinct architectural layers, and prediction markets are where it’s most legible right now.
>
> The Three Layers · Agent Layer · Identity Layer · Venue Layer · Missing Pieces · What I’d Bet On  \[these are links\]

The rest of it reads like AI-generated slop with the same empty prose, overuse of em-dashes—and conclusions consisting of 

- **bullet points** followed by bold text.

The hackathon is equally vapid:

> The Lepton Agents Hackathon is hosted by Canteen, a builder series for AI agents and creators that pay, receive, and stream value at the smallest scale, settled on Arc, the stablecoin-native L1 from Circle.

They also mention what this could unlock for [existing OSS projects](https://lepton.thecanteenapp.com/#distribution), which demonstrates a clear lack of understanding:


>| Repository | Description | Count |
>| :--- | :--- | :--- |
>| **immich-app/immich** | Licensing and tips paid to the photographer named in the file[^1] | 103k |
>| **TryGhost/Ghost** | Paid memberships, subscriptions, and newsletters for writers[^2] | 54k |
>| **jellyfin/jellyfin** | Pay-per-view, rentals, or a creator subscription on your own media server[^3] | 53k |
>| **mastodon/mastodon** | Patronage and quadratic funding for the posts a community values[^4] | 50k |
>| **discourse/discourse** | Paid groups and gated categories for a community's best threads | 47k |
>| **DIYgod/RSSHub** | Paid feeds, and citation tolls when an answer is grounded in a source | 44k |
>| **navidrome/navidrome** | Royalties split by what listeners actually played[^5] | 21k |
>| **chocobozzz/peertube** | Per-view or per-second streaming, split across contributors | 15k |
>| **owncast/owncast** | Live tips and pay-to-watch streams | 11k |
>| **Kareadita/Kavita** | Pay-per-book or rentals on a self-hosted reading library[^6] | 11k |

Their [first blog post](https://thecanteenapp.com/analysis/2026/05/28/distribution-bootstrap-payments-founders.html) goes into more detail on this point (bullshit jargon passages will be marked with \*):

> The build path falls out cleanly. Eight concrete companies[^7], in the order we’d ship them, are written up below as a Request for Payments Founders:
>
>The Subsonic-Protocol Scrobble Sidecar (music)
>
>The MusicBrainz Payee Registry (music metadata)
>
>The Owncast Per-Second Streaming Webhook Sidecar (live video)
>
>The Jellyfin Per-Minute VOD Sidecar (personal-media VOD)
>
>The PeerTube Payments Plugin (federated VOD)
>
>The Mastodon Donation-Campaign Provider (fediverse fundraising)
>
>The LLM Crawler Citation-Toll Layer (feeds)
>
>The Settlement Core (the durable substrate under all of the above)
>
>Each one names a concrete thing to build, the upstream surface it attaches to, and what makes it the right next thing. The rest of this post is the supporting evidence: why the fee floor finally dropped, what each community has accepted in its PR history, where the data structures already live that a payment layer would read against, and which projects have shipped their own end-to-end payment stack and \*therefore call for a different value chain.\*
>
>\[...\]
>
>The same advice runs the other direction for established creator projects. Ghost and Ente both wrote their own Stripe integrations because there was no acceptable rail underneath them. \*If there had been an onchain substrate with nanopayment economics they could trust\*, those teams might never have shipped their own billing stack at all.


My point here is that I'm tired of these people trying to muscle their way into things we enjoy. These people think an {{< nutshell href="https://youtu.be/A654vzQTGbQ" title="insider trading website" >}} is a technological revolution and that we should start extracting monetary value from everything. They want to insert themselves and their bullshit between us and what we enjoy.

![Biogenetic value accumulation... I'm transacting value to everyone around me. I'm keeping my body primed and my mind sharp.](posts/email/cruel.gif "These people remind me of Cruelty Squad NPCs.")

They want to make [shitty games](https://www.youtube.com/@jauwn/videos) that are focused on profits, investment scams and pay-to-win mechanics over fun. They see value in a memecoin creation website instead of anything tangible. And now their AI writers want to start a hackathon for people who can't code (and will never be able to due to {{< paywall href="https://www.404media.co/software-developers-say-ai-is-rotting-their-brains/" title="deskilling" bypass="https://web.archive.org/web/20260513131128/https://www.404media.co/software-developers-say-ai-is-rotting-their-brains/" >}}).

Everything must have some monetary element to it, otherwise it's worthless. It has to cost money, or give money, or connect to your "wallet," otherwise you don't own it and its therefore useless!!!11!!1!!! Everything revolves around money and the market and anything that doesn't have a monetary focus or adds friction to these processes (like regulation) is bad.

Nothing can ever just be given or owned for free (this goes beyond software to other stuff like Social Security or free healthcare), you must contribute back to the ~~hivemind~~ market with your time and money (and be paid pennies in return). The system is designed for those with lots of disposable income, and assumes all participants have some to spend on all this paywalled bullshit like movies, photos, or voting for their favourite posts. There's a reason the people who primarily promote this stuff are rich and famous.

It does remind me of dicussions I had with someone who was super involved in this world, with a supreme belief in the "magic of the market" and implying that prediction markets were a form of {{< nutshell href="https://en.wikipedia.org/wiki/Social_Darwinism" title="social Darwinism" >}}, thinning out the dumb traders so people like them could rise to the top.

They also want to use an AI system they think is revolutionary to accelerate this process and achieve their wildest dreams.

I'm so fucking done with these grifters who think every problem can be solved with a startup and flashy marketing.

## Oh Dear God There's More

I was pretty sure the post would end here. But then I visited [the Discord](https://discord.gg/rsVfYutFZg).

The contents are probably nothing new to people who browse Crypto Twitter, but it's a melting pot of crypto bro libertardism mixed with the classic Silicon Valley "build first, ask questions later" attitude.

The main channels are a torrent of vibecoded slop competing for eyeballs from the organization's corporate overlords and other members, the latest craze being different variations of "let's give AI some money, [what could go wrong?](https://lantian.pub/en/article/fun/ai-agent-bankrupted-their-operator-scan-dn42lantian.lantian/)"

There's also a lot of sloppy work and dead links that just haven't been looked over because these people are the literal definition of lazy:

![A webpage with the classic hallmarks of AI design, plus broken Markdown tables and codeblocks.](posts/email/dao.png "I've hidden the name to not advertise these morons.")

![test](posts/email/security.png "Every single security buzzword in the book.")

{{< video src="posts/email/proxim.mp4" muted=true caption="Nice." >}}

There even appear to be multiple companies trying to create some form of content discovery so AI agents can pay site owners for using their websites? Like direct clones of the same concept.

One of the example pieces of content was the blandest Medium article [I've ever read](https://freedium-mirror.cfd/@fidelltom868/the-shift-has-begun-but-most-people-havent-noticed-b99780480056)<sup>(Medium frontend)</sup>.

No AI booster wants to pay for content, and through many different bypass methods they never have to. Sensible people who dont use AI for research dont really care about this and they don't want AI to access their work at all. This is what I mean when I say that this is a melting pot of laziness and unimaginitive crap, a bunch of gamblers trying to make the best possible Twitter posts.

## Economics Aside

There's probably every crypto buzzword under the sun present in these pages, and what is any of it for? It's proven [well beyond any reasonable doubt](https://www.web3isgoinggreat.com/) that this kind of crypto investment is a Ponzi scheme propped up by {{< nutshell title="wash trading" href="https://en.wikipedia.org/wiki/Wash_trade" >}}, and that unregulated financial markets aren't the solution to all of our problems (because we used to have them before, during the Industrial Revolution in the 1800s and {{< nutshell title="Reaganomics" href="https://en.wikipedia.org/wiki/Reaganomics" >}} in the 1980s).

I don't think AI is the reason for datacenter construction or all of this. These people simply view AI as a vehicle to get whatever they're looking for, be it investment, a new customer base, or a successful enterprise with minimal effort.
These people want to game the system using the same Bullshit Machine™️ that everyone else has access to. They spend thousands in the process of pursuing the dream of building on the "future of finance." It doesn't matter that you then have to be your own bank, fraud department, security team and collections department. They'll drag us all to Hell with them to avoid paying taxes, and the people at the top exploit their behavior to wrench them for every dollar they have.

At this point I'm really reminded of these quotes from John Maynard Keynes:

> It is generally agreed that casinos should, in the public interest, be inaccessible and expensive. And perhaps the same is true of Stock Exchanges.
>
> \- Keynes ("General Theory of Employment, Interest and Money", p. 143)


> When the capital development of a country becomes a by-product of the activities of a casino, the job is likely to be ill-done.
> 
> \- Keynes ("General Theory of Employment, Interest and Money")

When so many people are obsessed with trying to strike it rich with crypto, AI, and sports betting, where does that leave us? Where are we going to be in 10 years?
More importantly, what is going to be left?

Already, a ton of these projects are dead and the hosts are desperately trying to contact someone to get them fixed:

![A list of 19 dead links and pings to the people behind them.](posts/email/dead.png "Usernames censored for privacy.")

So much for decentralized and free, am I right?

If you're interested in more on the economics/scamming side, Josh Otten has a {{< nutshell title="good video" href="https://www.youtube.com/watch?v=r7uCUi5Bv6k" >}} in his "Slopworld" series you can watch.

## What's Next?

Now, as I was writing this a new hackathon was announced, [Tameion](https://tameion.thecanteenapp.com/). 

![Tameion home page, visit it yourself](posts/email/tameion.png "The menu bar has terrible contrast and is barely readable, how was this approved?")

![Two image captions which are dark grey on dark brown-grey, they are barely readable.](posts/email/captions.png "More accessibility blunders, they look even worse at their normal size.")

Also the discord invite on their website doesn't give you the role for the new hackathon, it gives you the role for the old one.


My favourite part of the website is when they suddently reference Jesus's [Parable of the Talents](https://www.biblegateway.com/passage/?search=Matthew%2025:14-30&version=CSB) from Matthew 25 (a "talent" was a unit of currency worth 20 years' wages at the time):

> The master's complaint in Matthew 25 is a treasury complaint: "you ought to have deposited my money with the bankers, and I should have received my own with interest." Burying the silver looked safe, but it cost him the interest. The hack: an AI agent that notices idle balances and does something about them, moving reserves into USYC and redeeming them exactly when the cash-flow forecast says the money is needed. The hard part is not the yield, it is the timing: redeeming early enough that payroll clears, but late enough that the reserve had time to earn.

It takes particular zeal to take a parable about spiritual gifts (and only part of it, dropping all prior context) and turn it into an advertisement for a financial product.

Though these people worship money and AI agents already, so I'm sure it's an apt comparison for them. They're not the type to read or understand a book as long or deep as the Bible anyway.

![A man asks a computer to say it is alive. The computer responds that it is alive. The man responds with 'Oh my God.'](posts/email/iamalive.jpeg "AI Psychosis.")

---

At some point these people have to realize that AI cannot pay attention to every detail or reason properly, right? They're all willing to put their magic internet beans into the hands of someone who has no systems experience, who uses an AI that writes everything with clientside JS.

One single email has led me to discover that the "crypto winter" did not kill off this species of grifter, and I can't wait for their billboards to clutter San Francisco and their failures to either be really funny or really heartbreaking (or they get a bailout from the same government they hate so much).
They think giving everything a monetary value makes the world a better place, and they're not going to go away. 

They're going to keep trying until they can come up with the next Celsius-level collapse (intentionally or not), and with the current US government they are going to ignore every regulation in the book to get what they want.

They want to promote a future where human communication happens through robots that type illegible prose. They want to promote a future of finance where rules no longer apply and gambling for your retirement (or doing market manipulation) is the norm. They may even believe their AIs are conscious, and we therefore need to treat them as equal citizens.

They want to privatize everything and give it a profit incentive.

They want government services without paying for government taxes, and some have the anarcho-capitalist belief that everything is overregulated. The fact that these are the people founding new tech businesses doesn't bode well for the rest of us, but burying our heads in the sand won't make all this go away. 

We need to understand these people and their concerns if we are to stop them from ruling our Internet because their views align with those of the privileged few at the top.

Another one of {{< nutshell title="Otten's videos" href="https://youtu.be/NuIMZBseAOM" >}} remarks:

> History made a fool out of the office worker who stubbornly held onto his typewriter, and rightly so. Nostalgia is the surest path to irrelevance. Equally, blind devotion to technology is a sort of fanaticism. 

We can't remain in the past forever or stay in the woods with a typewriter hoping this all blows over; we need to fight to keep the web open and free while embracing AI where it actually makes sense (like cybersecurity) instead of devolving into crypto-fueled AI-worhsipping idealism.

The Athenians these people keep referencing moved on from their bad ideas and horsepuckey justifications of slavery and extreme wealth, and so can we.

[^1]: Immich is for people's photos, not this bullshit.

[^2]: Ghost already has this without crypto.

[^3]: Jellyfin is for your own personal collection, and people use it to get away from ad-filled streaming sites with eye-watering prices (besides, who wants Disney to get paid every time you watch *The Lion King*?).

[^4]: This is YouTube-style monetization (from an unknown source of funds) for Mastodon. Also, turns out {{< nutshell href="https://en.wikipedia.org/wiki/Quadratic_voting#Quadratic_funding" title="quadratic funding" >}} isn't something the AI made up on the spot.

[^5]: If you want to pay for your music, go to Bandcamp and upload the file to your server, this does not need to be integrated into my fucking media server.

[^6]: What's self-hosted about rentals (on my personal library, no less)? The current way to do that with an ebook is Adobe's ACSM system which nobody likes.

[^7]: Rule no. 1 of crypto libertardism: Everything must be a company with investors and profit margins.
