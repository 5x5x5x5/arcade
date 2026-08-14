# arcade

Vibe coded games. Everything here is a single static HTML file — no build step, no dependencies.

**Play: https://5x5x5x5.github.io/arcade/**

## Penelope's Waffle Match (`index.html`)

A cozy match-3. No timer, no losing.

- Tap a tile, then tap a neighbor to swap. Bad swaps wobble back — no penalty.
- Five tiles: 🐱 🧇 🚕 🗽 🍎. Matches of 4+ and cascades trigger toasts ("Purr-fect!", "Big Apple Bonus!").
- Every 300 points adds a waffle to her stack, and the cat next to it gets progressively happier.
- Out of moves? It announces "Fresh waffles!" and reshuffles itself.
- Sound toggle in the HUD. Works on phone or tablet; add it to the home screen for a full-screen version.

Difficulty knobs, both near the top of the `<script>`:

- `TYPES` — adding a sixth emoji makes matches rarer and the game harder.
- `Math.floor(score / 300)` in `addScore` — the points per waffle in the stack.

## Deploying

`.github/workflows/pages.yml` publishes the repo root to GitHub Pages on every push to `main`.

One-time setup: **Settings → Pages → Build and deployment → Source: GitHub Actions**. The
workflow can't do this for itself — the Actions token isn't permitted to create the Pages
site (`Resource not accessible by integration`).

## Adding another game

Drop it in its own folder with an `index.html` — `snake/index.html` is served at
`/arcade/snake/`. The whole repo root is published as-is.
