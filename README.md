# Vacuum Cube Set: interactive 3D concept model

Product Innovation Management class project. A browser-based 3D model of a travel packing system:

- **4 packing "cubes"**: Small, Medium, Large (rectangular, 3-sided perimeter zipper hinged at the back) and a Cylinder (full-length zipper on the long side)
- **1 palm-size pump**: battery-powered, USB-C rechargeable, seats on a one-way valve built into every cube
- Works in backpacks, duffels and suitcases, for checked bags and carry-ons

Original whiteboard sketch: [`docs/whiteboard-sketch.jpg`](docs/whiteboard-sketch.jpg)

## What's in the page

| Mode | What it does |
|---|---|
| **Explore** | Orbit, zoom, click any cube or the pump for its spec sheet. Each cube has **Unzip & open** and **Pump air out / Release air** buttons. Four colorways. |
| **Watch demo** | 7-step animated story: unzip → open & pack → zip → attach pump → pump air out (live volume / vacuum / battery readout) → repeat for the whole set → all four compressed cubes go into a carry-on and the lid closes. Steps are clickable, with pause and restart. |

Everything is in one file: [`site/index.html`](site/index.html). No build step.

## Open it locally

Double-click `site/index.html`. It opens in any current Chrome, Edge, Safari or Firefox.

It needs an internet connection, because it loads three.js (pinned to 0.160.0) and fonts from public CDNs. If the network is blocked, the page shows a message instead of a blank screen.

## Deploy to Cloudflare

**Option A: Cloudflare Pages via GitHub (easiest, auto-deploys on every push)**

1. Cloudflare dashboard → Workers & Pages → Create → Pages → Connect to Git → pick this repo.
2. Framework preset: **None**. Build command: *(leave empty)*. Build output directory: **`site`**.
3. Save and deploy. You get a `*.pages.dev` URL. Add a custom domain under the project's Custom domains tab.

**Option B: Wrangler CLI (Workers static assets, uses `wrangler.jsonc`)**

```bash
npx wrangler login
```

```bash
npx wrangler deploy
```

**Option C: Pages direct upload from the CLI**

```bash
npx wrangler pages deploy site --project-name vacuum-cube-set
```

## Editing the product

All product numbers live in the `PRODUCT CONFIG` block at the top of the `<script type="module">` in `site/index.html`:

- `CUBES`: sizes (1 scene unit = 10 cm), positions, clothing colors, labels
- `S_MIN`: compressed height as a fraction of full height (0.48 ≈ 52% thinner)
- `COLORWAYS`, `ACCENT`: fabric and trim colors
- Product name: the `<title>` and the `<h1 id="productName">`

The sizes, compression ratio, vacuum (kPa) and battery-drain figures are **illustrative concept targets**, not measured specs. Replace them with prototype test data when you have it.
