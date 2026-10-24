# LLT – London Live Transport

A phone-first web app for live London transport times. Open it, find your stop on the map, tap it, and see what's coming.

**Live app:** https://giovanniconti.github.io/llt-london-live-transport/

## What it does

- Map of bus stops around you, each pin showing its stop letter
- Tap a stop to see its routes and live departures, counting down and refreshing every 30 seconds
- Save favourite stops for one-tap access
- Works in light and dark mode
- Add to your iPhone Home Screen (Safari → Share → Add to Home Screen) to use it full screen like an app

Tube times are planned for later.

## How it works

It's a single static page (`index.html`) hosted on GitHub Pages, with no build step and no server.

- **Live data:** [TfL Unified API](https://api.tfl.gov.uk)
  - `GET /StopPoint?lat&lon&stopTypes=NaptanPublicBusCoachTram&modes=bus&radius` for stops near the map centre
  - `GET /StopPoint/{naptanId}/Arrivals` for live predictions at a stop
- **Map:** [Leaflet](https://leafletjs.com) with [OpenStreetMap](https://www.openstreetmap.org/copyright) tiles
- **Favourites and last map position:** saved in the browser's local storage on your device

### TfL API key (optional)

The app works without a key, but anonymous requests are rate-limited. For a higher limit, register for a free key at https://api-portal.tfl.gov.uk and set `APP_KEY` near the top of the script in `index.html`. Note that anything in this public repo is visible to anyone.

## Running locally

Any static file server works, for example:

```sh
python3 -m http.server 8000
```

Then open http://localhost:8000. Location needs HTTPS or localhost.

Powered by TfL Open Data. Contains OS data © Crown copyright and database rights.
