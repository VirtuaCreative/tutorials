---
title: "I'm back with Jekyll on Docker and GH Pages"
author: Marcia
date: 2022-11-22 23:45:00 +0100
categories: [Blogging, Tutorial, Docker, Jekyll]
tags: [Web dev]
image:
  path: /commons/devices-mockup.png
  width: 800
  height: 500
  alt: "Jekyll on Docker and GH Pages."
pin: true
---

# Jekyll on Docker? Hell yeah!

This is a new Virtua Creative website. After a few year focusing on a full-time job,
I'm back on playing around with different technologies.
Not sure how often I'll be blogging but I'll try to come back here more often.

This website is based on the Jekyll theme "[Chirpy](http://jekyllthemes.org/themes/jekyll-theme-chirpy/)",
very nicely done. Adjusting the template is still a WIP.

The happy thing about this is that it is running on Docker with a `docker-compose.yml` file. Which means:
- No fuzzy dependency managers.
- No Ruby crash-management chaos.
- No "this-is-fine" dog to run your Jekyll site:

## Jekyll on Docker

1. Install [Docker Desktop](https://www.docker.com/products/docker-desktop/).
1. Clone a Jekyll theme or start a Jekyll website from stratch, or use your own.
1. Copy the [`docker-compose.yml`](https://github.com/VirtuaCreative/jekyll-on-docker/blob/pages/docker-compose.yml) file from this repo and put it in your Jekyll's root dir.
1. Open the terminal on your Jekyll's website directory.
1. Run `docker-compose up`.
1. Magic! It will take a couple minutes to build an image and run it in a container but, bam!
It's up on `localhost:4000`.
1. Run `docker-compose down` to stop it when you're done.

I've got a little help from [this guy](https://www.youtube.com/watch?v=ZHQ3IwIL590) to get this
right, by the way. But the GH part I figure out on my own.

## Jekyll on GitHub Pages

To get this up and running on GitHub Pages, I tried the
GitHub Actions thing. I think they could've given a
better name for they CI tool, but that's me being nitty.

It was easy too:

1. I pushed the content to my repo.
1. Went to Settings > Pages > Source > GitHub Actions.
1. Committed the prompted default template.
1. Magic. Done!

Pretty cool. Worth giving it a try.

Happy Jekylling!
