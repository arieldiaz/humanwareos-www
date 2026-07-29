# HumanwareOS website

The public website for [humanwareos.com](https://humanwareos.com).

HumanwareOS is an open-source, human-first operating system for running life
and work with AI agents through Slack. This repository is deliberately static:
plain HTML, CSS, and a tiny amount of JavaScript, deployed on Cloudflare Pages.

## Local preview

```sh
python3 -m http.server 4173
```

Open `http://localhost:4173`.

## Deploy

The production site is deployed from this directory to the `humanwareos-www`
Cloudflare Pages project.
