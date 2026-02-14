# Hot Air Balloon Tracker 🎈

[![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-Live-orange?logo=github)](https://jackwallner.github.io/hot-air-balloon-tracker/)
[![SondeHub API](https://img.shields.io/badge/API-SondeHub%20Amateur-orange)](https://sondehub.org/)

> Track high-altitude balloons near any location worldwide using real-time data from the SondeHub Amateur network.

**Live Site:** https://jackwallner.github.io/hot-air-balloon-tracker/

## Features

- 🎈 **Balloon Tracking** - Track amateur high-altitude balloon payloads
- 📍 **Location-based** - Search by coordinates or use geolocation
- 💾 **Saved Locations** - Store multiple tracking locations
- 🗺️ **Interactive Map** - View balloon positions and trails on Leaflet map
- 📊 **Flight History** - Track closest approaches throughout the day
- 🔒 **Privacy-first** - All data stored locally in your browser
- 📱 **Mobile-friendly** - Works on desktop and mobile

## Data Source

This app uses the [SondeHub Amateur API](https://github.com/projecthorus/sondehub-infra/wiki/API-(Beta)) to track amateur high-altitude balloon payloads worldwide. SondeHub is a free, open platform for tracking weather balloons and amateur payloads.

**Note:** Balloon launches are less frequent than aircraft flights. You may need to:
- Use a larger detection radius (200km default)
- Check during active launch windows
- Visit the [SondeHub tracker](https://amateur.sondehub.org/) to see current active balloons

## Quick Start

### Use the Live Site

Visit https://jackwallner.github.io/hot-air-balloon-tracker/ and:

1. Click "Use My Current Location" or enter coordinates manually
2. Set your detection radius (default: 200km)
3. Watch for balloons!

### Run Locally

```bash
# Clone
git clone https://github.com/jackwallner/hot-air-balloon-tracker.git
cd hot-air-balloon-tracker

# Serve locally
python -m http.server 8000

# Open http://localhost:8000
```

## How It Works

```
┌─────────────────┐         ┌─────────────────┐
│  SondeHub API   │◀────────│  Your Browser   │
│  (CORS-enabled) │         │  (balloon tracker)
└─────────────────┘         └─────────────────┘
                                      │
                                      ▼
                            ┌─────────────────┐
                            │  Leaflet Map    │
                            │  localStorage   │
                            └─────────────────┘
```

## File Structure

```
hot-air-balloon-tracker/
├── index.html                  # Main app (balloon-themed)
├── js/
│   ├── sondehub.js            # SondeHub Amateur API client
│   ├── balloon-storage.js     # localStorage wrapper
│   ├── balloon-location.js    # Location management
│   ├── balloon-tracker.js     # Tracking engine
│   ├── balloon-map.js         # Leaflet map integration
│   ├── balloon-ui.js          # UI rendering
│   └── balloon-app.js         # Main controller
└── README.md
```

## Configuration

All settings stored in localStorage:

| Setting | Default | Description |
|---------|---------|-------------|
| Refresh Interval | 60s | Seconds between API calls |
| Detection Radius | 200 km | How far to search for balloons |
| Night Pause | Off | Pause updates overnight |

## Related Projects

- **[overhead-flights](https://github.com/jackwallner/overhead-flights)** - Track aircraft using OpenSky API
- **[SondeHub](https://sondehub.org/)** - The data source powering this tracker

## Tech Stack

- Vanilla JavaScript (ES6+, no frameworks)
- [SondeHub Amateur API](https://github.com/projecthorus/sondehub-infra/wiki/API-(Beta))
- [Leaflet](https://leafletjs.com/) for maps
- [Nominatim](https://nominatim.org/) for geocoding
- localStorage for persistence
- GitHub Pages hosting

## License

MIT
