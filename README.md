# Personal Web Page

GMT 458 Web GIS - Assignment 1

**Live site:** https://zinetoytekin.github.io/gmt458_hw1/

## Pages

| File | Content |
|---|---|
| `index.html` | Home page with an introduction, an animated drawing, and contact information |
| `background.html` | My education and a Leaflet map of my campus |
| `technologies.html` | A table of the tools I use, with their logos |
| `internships.html` | Information about my two internships and an OpenLayers map of their locations |
| `style.css` | Shared CSS file. The color variables are at the top of the file. |

## How I Met the Assignment Requirements

- **HTML:** I used four HTML pages. All pages are linked by the same menu.
- **CSS animation:** The drawing on the home page moves up and down with `@keyframes float`. The menu links also have an animated underline.
- **Table with images:** The `technologies.html` page has a table with logos, software names, and their uses.
- **OpenLayers:** The `internships.html` page shows both internship locations on one map.
- **Leaflet:** The `background.html` page shows the Hacettepe University Beytepe Campus.
- **Issue 1 (overlapping markers):** The Leaflet markers are in an `L.layerGroup`. The group is added to the map when the zoom level is 9 or higher. It is removed when the zoom level is below 9. The page also shows the current zoom level and whether the markers are visible.
- **Issue 2 (repeating world map):**
  - **Leaflet:** I used `noWrap: true` on the tile layer. I also used `maxBounds` and `maxBoundsViscosity: 1.0` to stop the map from being dragged outside the world.
  - **OpenLayers:** I used `wrapX: false` on the OSM source and set an `extent` for the map view.
- **Git:** I made commits on at least three different days.

## Problem: Map Tiles Showed "403 Access Blocked"

When I opened `background.html` by double-clicking the file, the address started with `file:///C:/...`. All map tiles showed a grey error image. The image contained a 403 error message from OpenStreetMap.

**Cause:** OpenStreetMap tile servers check where map requests come from. A page opened with `file:///` does not have a normal web address as its origin. This can cause tile requests to be blocked.

**How I Tested and Fixed the Problem:**

1. I stopped opening the file directly. Instead, I used a local web server. I used VS Code Live Server.
2. I changed the tile URL from `https://{s}.tile.openstreetmap.org/...` to `https://tile.openstreetmap.org/{z}/{x}/{y}.png`. I also set `maxZoom: 19`.
3. I tested the maps on GitHub Pages. The maps work there without the local server because the website is hosted online.

The OpenLayers map on `internships.html` uses OpenStreetMap tiles too. Therefore, I also need to test it with a local web server. I checked the map on GitHub Pages as well.

## Other Things I Learned from AI

- **Changing the drawing's appearance:** My drawing is a JPG file with a white background. I used `filter: invert(1)` and `mix-blend-mode: screen` to make the drawing fit the dark background. This allowed me to change its appearance without editing the image file.
- **Managing colors:** I used CSS variables in `:root`, such as `--gold`, `--panel`, and `--indigo-600`. This makes it easier to change the site's colors in one place.
- **Fixing nested boxes:** A missing `</section>` tag caused one box to appear inside another. Adding the missing tag fixed the problem.
- **GitHub Pages:** I used `Settings > Pages > Deploy from a branch > main / (root)` to publish the website.

## AI Usage

Estimated total AI usage: 3 h
