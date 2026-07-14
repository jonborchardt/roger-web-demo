# Betrayed Alliance Book 1 — enhanced by Roger (web demo)

**Play it:** https://jonborchardt.github.io/roger-web-demo/

Roger re-renders classic SCI adventure games with high-resolution art
generated from the original game resources — game logic untouched. This
demo runs [Betrayed Alliance Book 1](https://github.com/Slattstudio/BetrayedAllianceBook1)
(v1.3.3.1) in the browser through ScummVM's Emscripten target with Roger's
enhanced rendering. Press F10 in-game to compare: Enhanced → Original →
Side-by-Side. Type parser commands (*look room*, *take map*), click to walk.

Saves live in your browser's storage and can be evicted — don't rely on
them long-term.

## Credits & licensing

- **Game:** Betrayed Alliance Book 1 © 2024 Ryan Slattery /
  [Slattstudio](https://slattstudio.com), released under the MIT license
  ([source](https://github.com/Slattstudio/BetrayedAllianceBook1)). The
  license ships with the demo at
  [site/betrayed-alliance/LICENSE-BetrayedAlliance.txt](site/betrayed-alliance/LICENSE-BetrayedAlliance.txt).
  This demo is an independent showcase and is not affiliated with
  Slattstudio.
- **Engine:** [ScummVM](https://www.scummvm.org) with the Roger display
  enhancement, GPLv3+ (see [COPYING](COPYING)). The compiled
  `scummvm.wasm`/`scummvm.js` served by this site are built from the
  public source at https://github.com/jonborchardt/scummvm (branch
  `jon-wasm`); the exact commit each deployment was built from is recorded
  in [site/betrayed-alliance/build-info.txt](site/betrayed-alliance/build-info.txt).

## How this repo works

This repo is a **publish target only** — it builds nothing (see `CLAUDE.md`).
Pushing to `main` triggers `.github/workflows/deploy.yml`, which publishes the
whole `site/` tree to GitHub Pages.

- `site/index.html` + `site/comparisons.html` + `site/upstreaming.html` +
  `site/style.css` are the **hand-authored explainer site** at the root URL.
- `site/betrayed-alliance/` is the **compiled game bundle** (wasm, packaged
  game data + art cache, landing page). It is assembled from the ScummVM fork's
  build output by `dists/emscripten/build-assemble_demo.sh` in the source repo
  and mirrored in — see `docs/roger/WEB_DEMO.md` there for the rebuild flow.
