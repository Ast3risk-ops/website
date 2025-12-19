---
title: "Moving to Blowfish"
date: 2024-02-07
draft: false
description: "Leaving HBS and coming to Blowfish"
tags: ["Personal Experience"]
type: "post"
---

<!--more-->

<style>
.emoji {
    width: 50px;
}
</style>

## The Beginning

I used to use the [HBS theme](https://hbs.razonyang.com/v1/en/), which had a lot of features and utilities.

![old-blog](old-blog.png "What the old blog [used to look like](https://web.archive.org/web/20240105161828/https://blog.asterisk.lol/).")

It had everything I needed, and I was happy with it. I also had a horrible [carrd site](https://web.archive.org/web/20240123185248/https://ast3risk-ops.carrd.co/) that haunts me to this day.

![carrd](carrd.png "My [old carrd site](https://web.archive.org/web/20240123185248/https://ast3risk-ops.carrd.co/).")

I wrote posts here, and the arrangement worked, but eventually I went looking for a theme to replace my main site.

I looked in a lot of places. Ghost, Astro, Nuxt, even WordPress.

Eventually I thought about [Jekyll](https://jekyllrb.com/), but I couldn't find any good themes. However, it did introduce me to [jamstackthemes](https://jamstackthemes.dev), where I kept digging through Jekyll and Astro themes.

Eventually I decided to go back to browsing Hugo themes, and after a lot of digging and testing, I ended up finding [Blowfish](https://blowfish.page).

It seemed really powerful and robust, and had a [configuration tool](https://www.npmjs.com/package/blowfish-tools) available, and the [examples](https://blowfish.page/users/) blew me away.

## Initial Struggles

Initially, the theme did not work correctly, displaying a 404 every time. 

![404](404.png ":sob:")

I actually made a [GitHub issue](https://github.com/nunocoracao/blowfish/issues/1184) for this, but found a quick fix on my own; I forgot to uncomment `theme = "blowfish"` in `config.toml` :facepalm:.

Once I got it working, I had to start configuring it, something I spent days on.

## Building the site

### Basics

First setting it up involves running `npx blowfish-tools` (just runs it) or

`npm i -g blowfish-tools` (installs it)

I started with the basics like a title, icon, socials, etc, which the tool did well.

### Theme

Eventually I set a background image and chose a colour scheme. I looked through the [available ones](https://blowfish.page/docs/getting-started/#colour-schemes), and chose Congo[^1] as a holdover until I could make my own, because it looked very similar to my old blog.

However, I just ended up sticking with it.

Setting up the menus and icons was a real breeze, and adding more was easy (more on that soon:tm:).

### Deployment

Deployment was fairly easy, no special Hugo flags required. The only caveat was I had to disable Cloudflare's [Rocket Loader:tm:](https://developers.cloudflare.com/speed/optimization/content/rocket-loader/) to fix the appearance switcher.

### Icons

This theme comes with a very small subset of icons from FontAwesome 6 Free. However, there is an easy procedure for adding more.

All I had to go was go to FontAwesome's [icon page](https://fontawesome.com/search?o=r&m=free), search for an icon, and download it into <mark>assets/icons</mark>. I will be using the Discord icon from `fa-brands` as an example.

![fas-search](fas-search.png "A world of free icons awaits...")

![fas-dl](fas-dl.png "So easy!")

From there it *does* get a bit more complicated, as you now have to edit the SVG file.

Using our Discord SVG as an example (normally this would be minified onto a single line), we need to add the attribute `fill="currentColor"` to our `path` item, turning this:

{{< highlight xml "linenos=table" >}}

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 512">
    <!--!Font Awesome Free 6.5.1 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license/free Copyright 2024 Fonticons, Inc.-->
    <path
        d="M524.5 69.8a1.5 1.5 0 0 0 -.8-.7A485.1 485.1 0 0 0 404.1 32a1.8 1.8 0 0 0 -1.9 .9 337.5 337.5 0 0 0 -14.9 30.6 447.8 447.8 0 0 0 -134.4 0 309.5 309.5 0 0 0 -15.1-30.6 1.9 1.9 0 0 0 -1.9-.9A483.7 483.7 0 0 0 116.1 69.1a1.7 1.7 0 0 0 -.8 .7C39.1 183.7 18.2 294.7 28.4 404.4a2 2 0 0 0 .8 1.4A487.7 487.7 0 0 0 176 479.9a1.9 1.9 0 0 0 2.1-.7A348.2 348.2 0 0 0 208.1 430.4a1.9 1.9 0 0 0 -1-2.6 321.2 321.2 0 0 1 -45.9-21.9 1.9 1.9 0 0 1 -.2-3.1c3.1-2.3 6.2-4.7 9.1-7.1a1.8 1.8 0 0 1 1.9-.3c96.2 43.9 200.4 43.9 295.5 0a1.8 1.8 0 0 1 1.9 .2c2.9 2.4 6 4.9 9.1 7.2a1.9 1.9 0 0 1 -.2 3.1 301.4 301.4 0 0 1 -45.9 21.8 1.9 1.9 0 0 0 -1 2.6 391.1 391.1 0 0 0 30 48.8 1.9 1.9 0 0 0 2.1 .7A486 486 0 0 0 610.7 405.7a1.9 1.9 0 0 0 .8-1.4C623.7 277.6 590.9 167.5 524.5 69.8zM222.5 337.6c-29 0-52.8-26.6-52.8-59.2S193.1 219.1 222.5 219.1c29.7 0 53.3 26.8 52.8 59.2C275.3 311 251.9 337.6 222.5 337.6zm195.4 0c-29 0-52.8-26.6-52.8-59.2S388.4 219.1 417.9 219.1c29.7 0 53.3 26.8 52.8 59.2C470.7 311 447.5 337.6 417.9 337.6z"
    />
</svg>
{{< /highlight >}}

into this:

{{< highlight xml "linenos=table,hl_lines=4" >}}

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 512">
    <!--!Font Awesome Free 6.5.1 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license/free Copyright 2024 Fonticons, Inc.-->
    <path
        fill="currentColor"
        d="M524.5 69.8a1.5 1.5 0 0 0 -.8-.7A485.1 485.1 0 0 0 404.1 32a1.8 1.8 0 0 0 -1.9 .9 337.5 337.5 0 0 0 -14.9 30.6 447.8 447.8 0 0 0 -134.4 0 309.5 309.5 0 0 0 -15.1-30.6 1.9 1.9 0 0 0 -1.9-.9A483.7 483.7 0 0 0 116.1 69.1a1.7 1.7 0 0 0 -.8 .7C39.1 183.7 18.2 294.7 28.4 404.4a2 2 0 0 0 .8 1.4A487.7 487.7 0 0 0 176 479.9a1.9 1.9 0 0 0 2.1-.7A348.2 348.2 0 0 0 208.1 430.4a1.9 1.9 0 0 0 -1-2.6 321.2 321.2 0 0 1 -45.9-21.9 1.9 1.9 0 0 1 -.2-3.1c3.1-2.3 6.2-4.7 9.1-7.1a1.8 1.8 0 0 1 1.9-.3c96.2 43.9 200.4 43.9 295.5 0a1.8 1.8 0 0 1 1.9 .2c2.9 2.4 6 4.9 9.1 7.2a1.9 1.9 0 0 1 -.2 3.1 301.4 301.4 0 0 1 -45.9 21.8 1.9 1.9 0 0 0 -1 2.6 391.1 391.1 0 0 0 30 48.8 1.9 1.9 0 0 0 2.1 .7A486 486 0 0 0 610.7 405.7a1.9 1.9 0 0 0 .8-1.4C623.7 277.6 590.9 167.5 524.5 69.8zM222.5 337.6c-29 0-52.8-26.6-52.8-59.2S193.1 219.1 222.5 219.1c29.7 0 53.3 26.8 52.8 59.2C275.3 311 251.9 337.6 222.5 337.6zm195.4 0c-29 0-52.8-26.6-52.8-59.2S388.4 219.1 417.9 219.1c29.7 0 53.3 26.8 52.8 59.2C470.7 311 447.5 337.6 417.9 337.6z"
    />
</svg>

{{< /highlight >}}

That's really easy! And now it follows our current color scheme and will work like any other icon! I already use this feature in lots of places in this website. 

Technically you can pull from any icon set you want, I just prefer to use FontAwesome 6 as it fits the rest of the site, however [Simple Icons](https://simpleicons.org) also works well if you need more brand icons.

You can find more icon sets at [Icones](https://icones.js.org).

### Comments

Adding comments is quite easy. For this example, I will be using [giscus](https://giscus.app), a comment system powered by github discussions used on this site. 

After setting everything up and obtaining your script snippet, just paste it into a new file called `comments.html` in <mark>layouts/partials</mark>. Then, edit <mark>params.toml</mark>  and set `article.showComments` to `true`.

## My opinion

Compared to my old blog theme, this is missing certain shortcodes or features but it has everything I need and looks a million times better. It's also a framework to build basic pages for an actual site, not just for a blog.

I've been able to use this to make a decent site that's more than a blog or a <abbr title="Link In Bio, think Linktree, solo.to or bio.link">LIB</abbr> site, while being simple to edit and maintain and looking good. I can edit content in local markdown editors (Markdown CMSes like Decap I find weird and unnecessary), license it myself and have full control over my content, all while keeping a modern appearance.

It also gets people to ask if I made this myself because nobody checks the footer. This [theme](https://blowfish.page) was made by [Nuno Coração](https://n9o.xyz), by the way. {{< figure src="tro.jpg" class="emoji" nozoom=true >}}

It's a hell of a lot more professional, and it *works*.

[^1]: Congo Scheme Colours: {{< swatches "#71717a" "#8b5cf6" "#d946ef" >}}
