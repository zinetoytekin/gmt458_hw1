# Personal Web Page

GMT 458 Web GIS - Assignment 1

**Live site:** https://zinetoytekin.github.io/gmt458_hw1/

## Pages

| File | Content |
|---|---|
| `index.html` | Home page: introduction, animated drawing, contact |
| `background.html` | Education and a Leaflet map of my campus |
| `technologies.html` | Table of the tools I use, with logos |
| `internships.html` | My two internships and an OpenLayers map of both locations |
| `style.css` | Shared stylesheet (colours are variables at the top of the file) |

## How the requirements are met

- **HTML:** four different HTML files linked by a shared menu.
- **CSS animation:** the drawing on the home page floats up and down (`@keyframes float`). Menu links also have an animated underline.
- **Table with images:** `technologies.html` (logo, software, use case).
- **OpenLayers:** `internships.html` shows both internship locations on one map.
- **Leaflet:** `background.html` shows the Hacettepe University Beytepe campus.
- **Issue 1 (overlapping markers):** the Leaflet markers live in an `L.layerGroup`. On every `zoomend` event the group is added to the map only if the zoom level is 9 or higher, and removed otherwise. The page shows the current zoom and whether the markers are visible.
- **Issue 2 (Earth repeating):**
  - Leaflet: `noWrap: true` on the tile layer, plus `maxBounds` with `maxBoundsViscosity: 1.0` so the map cannot be dragged outside the world.
  - OpenLayers: `wrapX: false` on the OSM source, plus an `extent` on the view.
- **Git:** committed on at least three different days.

## Problem : map tiles showed "403 Access blocked"

When I opened `background.html` by double-clicking the file (the address started with `file:///C:/...`), every map tile was replaced by a grey "403 - Access blocked - App is not following the tile usage policy of OpenStreetMap" image.

**Cause:** the OpenStreetMap tile servers check the `Referer` header to see which website is requesting tiles. A page opened from `file:///` sends no Referer, so OpenStreetMap blocks it. My code was not wrong.

**How I solved it:**
1. I stopped opening the file directly. I served the folder through a local web server instead (VS Code Live Server, address `http://127.0.0.1:5500`; `python -m http.server` also works), so the browser sends a Referer.
2. I changed the tile URL from `https://{s}.tile.openstreetmap.org/...` to `https://tile.openstreetmap.org/{z}/{x}/{y}.png` (OpenStreetMap no longer recommends the `{s}` sub-domains) and added `maxZoom: 19`.
3. On GitHub Pages (`https://...github.io`) the maps work without any extra step, because the site is served over https.

The OpenLayers map on `internships.html` uses the same OpenStreetMap servers, so it behaves the same way: it needs a local server when testing and works on GitHub Pages.

## Other things I learned from AI

- **Drawing with a transparent look:** my drawing is a JPG with a white background. `filter: invert(1)` plus `mix-blend-mode: screen` hides the white and turns the black lines white, so it fits the dark background without editing the image.
- **Keeping colours in one place:** CSS variables in `:root` (`--gold`, `--panel`, `--indigo-600`) change the theme of the whole site from one place.
- **Nested boxes bug:** a missing `</section>` tag made one box appear inside another.
- **GitHub Pages:** Settings > Pages > Deploy from a branch > `main` / `/ (root)`.

## AI usage

Estimated total AI usage: **[WRITE YOUR OWN ESTIMATE HERE, e.g. about 3 hours]**

