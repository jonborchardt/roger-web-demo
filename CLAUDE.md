# CLAUDE.md — roger-web-demo (publish target, NOT a source repo)

This repo only **publishes** the Roger web demo + explainer site to GitHub
Pages. It does not build anything. Read this before editing.

## What deploys
`.github/workflows/deploy.yml` publishes the whole `site/` tree to GitHub Pages
on pushes to `main` that touch `site/**` (or the workflow file itself — paths
filter added 2026-07-15; repo-root docs pushes like README/CLAUDE.md/COPYING no
longer trigger a redeploy, and `workflow_dispatch` is the manual escape hatch).
Live at https://jonborchardt.github.io/roger-web-demo/.

## Hand-authored here (safe to edit directly, then commit + push)
- `site/index.html`, `site/comparisons.html`, `site/upstreaming.html`
- `site/style.css`, `site/img/`, `site/svg/`, `site/.nojekyll`
- `README.md`, `CLAUDE.md`, `COPYING`

A one-line text fix to any of these is a single commit + push; Pages redeploys
in ~1 minute. No wasm rebuild needed.

## GENERATED — never hand-edit
- `site/betrayed-alliance/**` (and any future `site/<game>/**`) is the compiled
  game bundle: `scummvm.wasm`, `scummvm-game.data`, `data/`, `build-info.txt`,
  etc. It is mirrored in from the fork's build output with `robocopy /MIR`, which
  **deletes anything in the target folder that isn't in the fresh build**. Edits
  here are wiped on the next redeploy.

## The coupled source repo
Engine / Roger / wasm / game-bundle source-of-truth lives in the fork
**`jonborchardt/scummvm`**, branch **`jon-wasm`**. To rebuild and redeploy the
game bundle, follow the **Redeploy runbook** in that repo's
`docs/roger/WEB_DEMO.md` — the mirror step targets `site/betrayed-alliance/`,
never `site/` root (targeting `site/` would delete the explainer). Never try to
build the wasm in this repo.
