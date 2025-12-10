# Harbour Pools Passport — Learner Edition

This project is a small **single-page web app** plus an overview map:

- `index.html` — splash screen with your gold-foil crest
- `overview.html` — Sydney overview map (all pools at once)
- `app.html` — detailed view (one pool + stamp at a time)

The code has been refactored into small ES modules and heavily commented
so you can learn from it and extend it.

## File map

**HTML**

- `index.html` — cover page; loads `owner-name.txt` and waits for a tap
- `overview.html` — overview map, loads `overview.js`
- `app.html` — main passport / stamps app, loads `app.js`

**JavaScript modules**

- `data.js`
  - `loadPools()` — fetches `pools.json` and normalises lat/lng to numbers

- `storage.js`
  - All `localStorage` access lives here
  - `readVisited()` / `writeVisited()` — visited map `{ done, date }`
  - `countVisited()` — how many pools are visited
  - `readSelection()` / `writeSelection()` — which pool is selected
  - `readStampsPage()` / `writeStampsPage()` — current passport page

- `overview.js`
  - Renders the Sydney map with one marker per pool
  - Uses the same visited map as the main app (shared storage module)

- `app.js`
  - Main Harbour Pools logic
  - Shows one pool at a time, with:
    - big arrows to move between pools
    - map that pans to the selected pool
    - stamps + optional visit date

**Data**

- `pools.json` — simple list of pools with name, lat, lng
- `owner-name.txt` — name printed on the splash screen

**Assets**

- `carpe-diem.png` — crest image used on splash
- `stamp.svg` — stamp icon in the passport view
- `style.css` — all shared styling for splash, overview, and app

## Where to start reading the code

1. Open **`app.html`** to see the structure of the main page.
2. Then open **`app.js`** and follow the `init()` function at the bottom.
3. Trace the functions it calls (`loadPools`, `setupMap`, `selectIndex`, etc).

Everything has comments that explain what each function does and *why* it
exists. This project is meant to be a safe playground for learning JavaScript
and web app structure.
