# Spain Wildfire Situational Awareness — EFFIS Web GIS

A lightweight, browser-based web GIS tool built to visualize live wildfire data during the July 2026 Spain/France wildfire crisis (Ávila, Madrid, Castellón, and related fire complexes). Built as a single static HTML file — no backend, no build step, deployable anywhere.

**[Live Demo →](https://fisan-git.github.io/spain-wildfire-webgis/)**

![screenshot](screenshot.png)

## What it does

This app fuses two independent, authoritative geospatial data sources into a single live map:

- **[EFFIS](https://forest-fire.emergency.copernicus.eu/)** (European Forest Fire Information System, Copernicus Emergency Management Service) — served via WMS, providing:
  - Fire Weather Index (fire danger forecast)
  - Rapid Damage Assessment burnt-area perimeters
- **[NASA FIRMS](https://firms.modaps.eosdis.nasa.gov/)** (Fire Information for Resource Management System) — VIIRS satellite thermal hotspot detections, updated every 15 minutes

Rather than checking multiple agency dashboards separately, a responder, analyst, or curious member of the public gets one map with toggleable layers, adjustable opacity, and a live server-health indicator.

## Why this exists

Built while tracking the real-time Spain wildfire crisis of July 2026 as a demonstration of practical GIS Analyst skills: live WMS/OGC service integration, multi-agency data fusion, and designing for the reliability issues that come with consuming public emergency-response infrastructure under heavy load.

## Tech stack

- [Leaflet.js](https://leafletjs.com/) for the map engine
- OGC WMS (Web Map Service) layers from EFFIS and NASA FIRMS
- CartoDB dark basemap tiles
- Pure HTML/CSS/JS — no framework, no build tooling

## Setup

1. Clone this repo
2. Get a free NASA FIRMS API key: https://firms.modaps.eosdis.nasa.gov/api/map_key/
3. Open `index.html` and replace `YOUR_FIRMS_MAP_KEY` with your key
4. Open the file in a browser, or deploy via GitHub Pages (Settings → Pages → Deploy from branch)

## Known limitations

- EFFIS's public WMS infrastructure can be slow or temporarily unavailable during high-traffic periods (e.g., major active fire events, when public and press interest spikes). This app includes a status indicator to surface that transparently rather than silently failing.
- Layer names are sourced from EFFIS's published documentation and sample URLs on their [Data and Services](https://forest-fire.emergency.copernicus.eu/applications/data-and-services) page — EFFIS occasionally revises internal layer naming, so it's worth spot-checking against their current sample URLs if a layer stops rendering.

## Data attribution

- Fire danger and burnt-area data: © EFFIS / Copernicus Emergency Management Service
- Active fire hotspots: NASA FIRMS, using data from the VIIRS instrument aboard Suomi NPP and NOAA-20

## License

MIT — feel free to fork and adapt for other regions or events.
