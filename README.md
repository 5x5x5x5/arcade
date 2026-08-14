# arcade

Vibe coded games. Every game is a single static HTML file — no build step, no dependencies.

**Play: https://5x5x5x5.github.io/arcade/**

The root `index.html` is the landing page that lists the games.

## Penelope's Waffle Match (`waffle-match/`)

A match-3 diner. Fill the order on the ticket before the syrup runs out.

Two modes, picked from the title card:

- **Waffle Rush** — each level is an order (e.g. `🧇 0/12`) and a syrup bar that drains.
  Fill the order and it's "Order up!", leftover syrup cashes in at 10 points a second,
  and the next order is bigger with less time. Run dry and it's "Out of syrup!" — the run
  ends with your score, orders served, and a best score kept in `localStorage`.
- **Cozy mode** — the same orders and levels with no timer and no losing, which is the
  game as it was before.

Either way:

- Tap a tile, then tap a neighbor to swap. Bad swaps wobble back — no penalty.
- Five tiles: 🐱 🧇 🚕 🗽 🍎. Matches of 4+ and cascades trigger toasts ("Purr-fect!", "Big Apple Bonus!").
- Every order tile you match pours a little syrup back (`+1.5s`), so playing well buys time.
- The cat on the ticket gets progressively happier as the order fills.
- A cascade that lands right after the buzzer still counts — if it finishes the order, the level clears.
- The clock pauses when the tab is hidden.
- Out of moves? It announces "Fresh waffles!" and reshuffles itself.
- Sound toggle in the HUD. Works on phone or tablet; add it to the home screen for a full-screen version.

Difficulty knobs, in the block marked `Difficulty knobs` at the top of the `<script>`:

- `BASE_TIME` / `TIME_DROP` / `MIN_TIME` — seconds on level 1, seconds lost per level, and the floor.
- `ORDER_BASE` / `ORDER_STEP` — tiles to collect on level 1 and how many more each level adds.
  From level 3 the order splits across two tile types, from level 6 across three.
- `TIME_BONUS` — seconds back per order tile matched. The single biggest kid-friendliness dial.
- `TYPES` — adding a sixth emoji makes matches rarer and the game harder.

## Puppy Chase 3D (`puppy-chase/`)

You're the cat; chase the pups around a 3D park. No timer, no losing.

- Drag anywhere (or arrow keys / WASD) to run. Pups flee when you get close, but
  you're faster.
- Each catch is a bone for the score. Every 5 catches adds another pup, up to 6.
- The 3D is a dependency-free sprite scaler: emoji billboards perspective-projected
  onto a ground plane, camera trailing the cat. No WebGL, no libraries.

Difficulty knobs, at the top of the `<script>`: `CAT_SPEED`, `DOG_FLEE` (the gap
between them is how hard catching is), `FLEE_RADIUS`, and `START_DOGS`/`MAX_DOGS`.

## Deploying

GitHub Pages serves the repo root of `main` as-is, so every push to `main` republishes the
site. No workflow, no build.

The setting is **Settings → Pages → Build and deployment → Source: Deploy from a branch**,
pointed at `main` and `/ (root)`. The empty `.nojekyll` file keeps Jekyll from mangling the
files on the way out.

## Adding another game

Drop it in its own folder with an `index.html` — `snake/index.html` is served at
`/arcade/snake/`. The whole repo root is published as-is. Then add a card for it
to the `.games` list on the landing page.
