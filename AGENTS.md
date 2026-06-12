# AGENTS.md

## Cursor Cloud specific instructions

This repository is a single, self-contained **static website**: `index.html` plus image
files under `assets/`. There is no package manager, build step, test suite, or linter.
All third-party JS/CSS (GSAP, ScrollTrigger, Lenis, Mapbox GL, Lucide, Google Fonts) is
loaded from CDNs at runtime, so an internet connection is needed for full rendering.

### Running it (dev)

Serve the repo root over HTTP (opening `index.html` via `file://` is not recommended
because of relative asset paths and CDN behavior):

```
python3 -m http.server 8000
```

Then open `http://localhost:8000/`. The page is a scroll-driven animated landing page —
verify it by scrolling, which triggers GSAP/Lenis animations and section transitions.

### Non-obvious notes

- **Mapbox token**: `index.html` defines `const MAPBOX_TOKEN = 'pk.YOUR_TOKEN_HERE'`. When
  the token is the placeholder, `canUseMapbox()` returns false and the map sections fall
  back to a code-generated satellite texture. No token/secret is required to run or test
  the site; replace the token only if you need live Mapbox tiles.
- There is nothing to install: Python 3 (preinstalled) is only used as a static file
  server. No `node_modules`, virtualenv, or dependency refresh is needed.
- There are no lint/test/build commands for this repo.
