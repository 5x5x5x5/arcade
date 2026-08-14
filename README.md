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

GitHub Pages serves the repo root of `main` as-is, so every push to `main` republishes the
site. No workflow, no build.

The setting is **Settings → Pages → Build and deployment → Source: Deploy from a branch**,
pointed at `main` and `/ (root)`. The empty `.nojekyll` file keeps Jekyll from mangling the
files on the way out.

## Adding another game

Drop it in its own folder with an `index.html` — `snake/index.html` is served at
`/arcade/snake/`. The whole repo root is published as-is.
