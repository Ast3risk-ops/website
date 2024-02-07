---
title: "Moving to Blowfish"
date: 2024-01-23
draft: true
description: "Leaving HBS and coming to Blowfish"
tags: ["Personal Experience"]
---

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

![404](https://private-user-images.githubusercontent.com/83875983/298305842-85fb7ba1-451e-4dd3-a6e0-5a3a66d935f3.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MDcyNjQyNjIsIm5iZiI6MTcwNzI2Mzk2MiwicGF0aCI6Ii84Mzg3NTk4My8yOTgzMDU4NDItODVmYjdiYTEtNDUxZS00ZGQzLWE2ZTAtNWEzYTY2ZDkzNWYzLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNDAyMDYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjQwMjA2VDIzNTkyMlomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTc1MTQyMGM5NTRkNDUxZDQ3NGRhMDhjYjMwM2NlMWU2ZDI0ODQwZGFmMDdmYjVkYTFiZDIyN2JmZDA1MjY0NTYmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JmFjdG9yX2lkPTAma2V5X2lkPTAmcmVwb19pZD0wIn0.Z-zdpUlIyRclOPa2-azZ9Zm3DEkYIx7629ZTpGwyCDg ":sob:")

I actually made a [GitHub issue](https://github.com/nunocoracao/blowfish/issues/1184) for this, but found a quick fix on my own; I forgot to uncomment `theme = "blowfish"` in `config.toml` :facepalm:.

Once I got it working, I had to start configuring it, something I spent days on.

## Building the site

### Basics

I started with the basics like a title, icon, socials, etc, which the tool did well.

### Theme

Eventually I set a background image and chose a colour scheme. I looked through the [available ones](https://blowfish.page/docs/getting-started/#colour-schemes), and chose Congo as a holdover until I could make my own, because it looked very similar to my old blog.

Here it is:

{{< swatches "#71717a" "#8b5cf6" "#d946ef" >}}

However, I just ended up sticking with it.





## Compared to my old blog




