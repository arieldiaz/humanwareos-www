# humanwareos-www

The public site for [www.humanwareos.com](https://www.humanwareos.com).

HumanwareOS is the upstream framework people fork. The code lives in
[`arieldiaz/life-os`](https://github.com/arieldiaz/life-os) (rename to
`humanwareos` pending). This repo is only the site.

## Stack

Static HTML and one stylesheet. No framework, no build step, no dependencies —
what is in this directory is what ships.

```
index.html      the whole site, one page, anchored sections
styles.css      tokens + layout
assets/         logo mark, agent app icons, model + harness tiles
```

## Design

Direction C, "site as system spec sheet", from the design exploration at
`ariel-os/apps/design-hq/versions/2026-07-29-humanwareos-site-direction/`.
Palette and type are tokens at the top of `styles.css`. Ocean carries the
secondary accent; fire carries the primary. The mark is the layer stack with
its base rung split ocean / grey / fire — life and work meeting at the
foundation.

Dark and light modes follow the visitor's system preference automatically.

## Preview

```sh
python3 -m http.server 4173
```

## Deploy

Cloudflare Pages project `humanwareos-www`, custom domains `humanwareos.com` and
`www.humanwareos.com`. The project is connected to this GitHub repository and
automatically deploys every push to `main`. No build command; the repo root is
the output.

Git integration is the default deployment mode for every site backed by a
repository. Direct Upload is reserved for a site with no source repository or
one whose deployment is deliberately owned by another CI system.

Wrangler is a fallback only. If it is ever needed, the token needs Account →
Cloudflare Pages → Edit and Zone → DNS → Edit on `humanwareos.com`. Key names
only — never a value in this repo.
