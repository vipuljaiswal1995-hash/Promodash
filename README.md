# PromoDash — Custom Drinkware Prototype

An interactive, hi-fi prototype of the PromoDash drinkware ordering experience:
product page → design studio (AI + editor) → cart → checkout (single or split-grid multi-address) → confirmation.

Built as a self-contained static site — **no build step, no dependencies.** Every page is plain HTML that runs directly in the browser.

## What's inside

| File | Purpose |
|------|---------|
| `index.html` | Landing entry — redirects to the prototype |
| `PromoDash Prototype.dc.html` | The main app (PDP, studio, cart, checkout) |
| `Bottle.dc.html` | Reusable 3D bottle preview component |
| `PromoDash - UX Deck.dc.html` | The UX story / design deck |
| `support.js` | Component runtime (required by the `.dc.html` files) |
| `deck-stage.js` | Slide-deck shell used by the UX deck |

> The `.dc.html` files load `support.js` and reference each other by name, so they must stay in the same folder.

## Run locally

It's static — just serve the folder with any static server:

```bash
# Python
python3 -m http.server 8000

# or Node
npx serve .
```

Then open `http://localhost:8000/`.

Opening `index.html` directly via `file://` also works.

## Deploy to Vercel

### Option A — Git (recommended)

1. Create a new repo and push:
   ```bash
   git init
   git add .
   git commit -m "PromoDash prototype"
   git branch -M main
   git remote add origin https://github.com/<you>/<repo>.git
   git push -u origin main
   ```
2. Go to [vercel.com/new](https://vercel.com/new), import the repo.
3. **Framework Preset:** Other · **Build Command:** (leave empty) · **Output Directory:** `./`
4. Deploy. Vercel serves the files as-is.

### Option B — Vercel CLI

```bash
npm i -g vercel
vercel        # preview
vercel --prod # production
```

No build settings needed — `vercel.json` marks it as a static site.

## Notes

- Product and review imagery are styled placeholders; drop in real assets when available.
- State (cart, design, addresses) is in-memory and resets on reload — this is a prototype, not a backend.
