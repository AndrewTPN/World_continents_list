# World – Continents & Country Shapes

Interactive world map showing all continents and the geographic shape of each country.

---

## Why I made this (beginner notes)

I wanted a small project where I could **see geography and code work together**. The goal was: pick a country from a list or search, and have the globe spin to it and zoom in — so I could learn where countries are and what they look like on the map.

I also wanted to practice **one real web app** that uses:

- **HTML** for structure (sidebar, search box, map area)
- **CSS** for layout and a simple dark theme (variables, flexbox, hover states)
- **JavaScript** for all the behavior (clicks, search, animations)
- **D3.js** to draw the map and handle geographic data (projections, paths, drag/zoom)
- **TopoJSON** to get real country shapes from the web (no backend needed)

So this project is both a **geography tool** and a **learning project** for building an interactive single-page app.

---

## What I learned from this

1. **HTML/CSS**
   - A two-column layout (sidebar + map) with `flexbox`
   - CSS variables (`:root`) for colors so one change updates the whole theme
   - Styling lists, inputs, and hover/focus states

2. **JavaScript**
   - **async/await** to load the map data (TopoJSON) from a URL before drawing
   - Keeping state in variables (`selectedCountry`, `currentCenter`, `animating`, etc.) and updating the UI when they change
   - **Event listeners**: click on a country or list item, type in search, drag the map, scroll to zoom
   - **requestAnimationFrame** to animate the globe spinning and zooming smoothly instead of jumping

3. **D3.js**
   - **d3.geoOrthographic()** — the globe is a “view from space” projection, not a flat map
   - **d3.geoPath()** — turns geographic coordinates into SVG paths so we can draw country outlines
   - **topojson.feature()** — converts TopoJSON into GeoJSON so D3 can use it
   - **d3.geoCentroid()** — finds the center of a country so the globe can spin to it
   - **d3.drag()** and wheel events to rotate and zoom the globe

4. **Data**
   - Storing which country belongs to which continent in a simple object (`CONTINENTS_DATA` / `countryToContinent`)
   - Matching country names from the list to the map data (names must match what’s in the TopoJSON)

5. **UX**
   - Search with live results, keyboard (Enter, Arrow keys, Escape)
   - Tooltip on hover with country name and continent
   - Highlighting the selected country and dimming others so the chosen one stands out

In short: I learned how to **structure a page**, **style it**, **load external data**, **draw a map with D3**, and **wire up interactions** so the globe and list stay in sync. It’s one file (`index.html`) so it’s easy to open in a browser and play with.

---

## Features

- **Continents list** – All 7 continents with their countries (Africa, Asia, Europe, North America, South America, Oceania, Antarctica)
- **Country shapes** – Real geographic boundaries for each country, drawn from Natural Earth data
- **Interactive** – Click a continent to expand and highlight its countries on the map; click a country (list or map) to spin the globe and zoom; hover for name and continent
- **Search** – Type to filter countries; select with mouse or keyboard

## Run locally

Open `index.html` in a browser (double-click or drag into a tab). The map loads country boundaries from a CDN and works without a server.

Or use a simple HTTP server:

```bash
npx serve .
```

Then open http://localhost:3000
