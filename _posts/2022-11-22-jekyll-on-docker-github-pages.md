---
title: "Build Jekyll on Docker and Publish with GitHub Pages"
author: marcia
date: 2022-11-22 20:45:00 +0100
categories: [Tutorial]
tags: [web dev, blogging, docker, jekyll]
image:
  path: '/posts/jekyll-docker.png'
  width: 800
  height: 500
  alt: "Jekyll on Docker and GH Pages."
# pin: true
---

# How to publish a Jekyll website on a Docker container and why

If you are wondering why someone would want to use Docker to generate
something as simple as a static website, here's why:

> You install Docker on your computer, add a `docker-compose.yml` file to your site's root, and you're done.
{: .prompt-info }

This means:

- No fuzzy dependency managers.
- No Ruby crash-management chaos.
- No extra dependencies to run your Jekyll site.

## How to deploy a Jekyll website on Docker

To Deploy a Jekyll websiste in a Docker container locally:

1. Install [Docker Desktop](https://www.docker.com/products/docker-desktop/).
1. Download a Jekyll theme, start a new site from stratch, or use your own.
1. Copy the [`docker-compose.yml`](https://github.com/VirtuaCreative/tutorials/blob/pages/docker-compose.yml) file from this repo and put it in your Jekyll's root directory.
1. Open the terminal on your Jekyll's website directory.
1. Run `docker-compose up`.
1. Magic! It takes a couple minutes to build the image and run it in a container and bam, up and running on `localhost:4000`.

To stop the server:

- Type <kbd>Ctrl</kbd> + <kbd>C</kbd> to stop `jekyll serve`.
- Run `docker-compose down` to stop the Docker container.

To restart Jekyll, run `docker-compose up` again.

## How to publish your Jekyll website on GitHub Pages

Now that your Jekyll website is up and running, it's time to release it. For this tutorial,
let's use GitHub Pages with GitHub Actions (their CI tool) to publish it:

1. Push your website's codebase to a repository on GitHub.
1. Go to **Settings > Pages > Source > GitHub Actions**.
1. Commit the prompted default template.

Magic. Done! Your website is up and running.
