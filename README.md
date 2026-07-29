# humanwareos-www

The public site for [humanwareos.com](https://humanwareos.com).

HumanwareOS is the upstream framework — the thing people fork. `ariel-os` is
Ariel's distro of it. This repo is only the marketing/thesis site; the code
lives in [`arieldiaz/life-os`](https://github.com/arieldiaz/life-os) (rename to
`humanwareos` pending).

## Stack

Static HTML and one stylesheet. No framework, no build step, no dependencies —
what is in this directory is what ships. Fonts come from Google Fonts; the
palette and type are tokens at the top of `styles.css`.

```
index.html      the whole site (single page, anchored sections)
styles.css      tokens + layout, dark-first with a light mode
assets/         mark.svg (favicon), og.png when it exists
```

## Preview

```sh
python3 -m http.server 4173
```

Then open http://localhost:4173

## Deploy

Cloudflare Pages, project `humanwareos-www`, custom domain `humanwareos.com`.
The repo root is the build output — no build command, output directory `/`.

Deploying from the CLI needs a Cloudflare API token with **Account → Cloudflare
Pages → Edit** plus **Zone → DNS → Edit** on `humanwareos.com`. The existing
`CF_API_TOKEN` in Doppler (`arielos-core/prd`) is scoped to `arieldiaz.com`
only and cannot create this project.

```sh
npx wrangler pages deploy . --project-name humanwareos-www
```

## Content source

The narrative follows the HumanwareOS intro-video outline: the ladder, the
problem with agent tooling, Slack as the surface, human-first vision,
architecture, cost. Sections are anchored so video embeds can be dropped in
per section as those clips are cut.

## Naming

**HumanwareOS**, one word, lowercase `w`. Capital `W` is how HumanWare Inc
styles its own name. *humanware* is the layer; *HumanwareOS* is the project
that operates it. Never "Humanware OS" as two words.
