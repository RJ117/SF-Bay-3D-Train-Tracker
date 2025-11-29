# CHANGELOG

All notable changes to the BART 3D Visualizer project are documented in this file.

---

## ⚠️ IMPORTANT LEGAL NOTICE

This project is **NOT affiliated with, sponsored by, or endorsed by BART (Bay Area Rapid Transit District)**.

- All train positions are **SIMULATED** and do not represent actual train locations
- No realtime BART APIs or proprietary systems are accessed
- Station coordinates derived from public GTFS static data only
- This is a **DEMO/PORTFOLIO PROJECT** for educational purposes

---

## [1.0.0] - 2025-01-XX - GitHub Release (Sanitized)

### 🛡️ Legal Sanitization
- **REMOVED** all BART API calls (`api.bart.gov`)
- **REMOVED** all API keys and authentication
- **REMOVED** all realtime ETD (Estimated Time of Departure) endpoints
- **REMOVED** all "LIVE" indicators and real-time language
- **REMOVED** Open-Meteo weather API integration
- **REPLACED** realtime data with mock train generator
- **ADDED** prominent "SIMULATED DATA" disclaimers throughout
- **ADDED** MIT License with additional BART disclaimer
- **ADDED** comprehensive README with legal notices

### ✨ Features (Simulation Mode)
- 3D visualization of all 50 BART stations
- Simulated train movements with configurable refresh
- Interactive camera controls (pan, rotate, zoom)
- Station navigation (click or dropdown)
- Fare calculator (estimates only, with disclaimer)
- Train info modal showing simulated ETAs
- Route visualization with Start/End point markers

### 📁 Project Structure
```
src/
├── components/
│   └── BART3DVisualizer.jsx    # Main component (no API calls)
├── data/
│   ├── stations.js              # Static GTFS-derived data
│   ├── routes.js                # Track route definitions
│   └── mockTrains.js            # Simulated train generator
├── utils/
│   ├── fareCalculator.js        # Fare estimation (disclaimer included)
│   └── geoUtils.js              # Geographic utilities
```

### 🔒 Data Sources (All Public/Static)
- Station coordinates: Derived from public GTFS feeds
- Route geometry: Programmatically generated
- Train positions: Randomly simulated (NOT REAL)
- Fare estimates: Approximate calculations (NOT OFFICIAL)

---

## Development History (Pre-Sanitization)

The following documents the development process. **None of these features using real APIs are included in the public release.**

### [0.5.0] - Development - Navigation & Clickability Fixes

#### Changed
- Implemented full pan/scroll navigation (right-click drag, WASD keys)
- Made all train dots clickable for ETA display
- Added individual ribbon trail per train dot
- Verified child fare policy (4 and under ride FREE per bart.gov)
- Added prominent train count display
- Fixed camera controls to allow map exploration

#### Technical Details
- Camera system: target + offset model for smooth panning
- Raycaster for 3D object clicking
- Keyboard input via Set for multi-key support

### [0.4.0] - Development - Train Names & Status

#### Added
- Unique train name generator (e.g., "R-Apollo-42")
- Train status modal with detailed information
- Location-based departure grouping (top 3 times per destination)
- Scrollable sidebar UI with collapsible sections

#### Train Name Format
- Prefix: R=Red, O=Orange, Y=Yellow, G=Green, B=Blue, K=Beige
- Name: Generated from hash of train ID
- Number: 01-99 based on hash

### [0.3.0] - Development - Fare Calculator

#### Added
- Comprehensive fare calculator modal
- Distance-based fare calculation (Haversine formula)
- All discount tiers:
  - Adult: Full fare
  - Youth (5-18): 50% off
  - Senior (65+): 62.5% off
  - Disabled (RTC): 62.5% off
  - Clipper START: 50% off
  - Child (4 & under): FREE
- Airport surcharges (SFO: $5, OAK: $6)
- Multi-trip and round-trip calculations

#### Verified Against Official Sources
- bart.gov/tickets/discounts (January 2025)
- Child fare: "Children 4 and under ride free"

### [0.2.0] - Development - Weather System

#### Added (REMOVED IN SANITIZED VERSION)
- ~~Open-Meteo weather API integration~~
- ~~Dynamic weather effects (rain, fog, clouds)~~
- ~~Location-based weather (any BART station)~~
- ~~Day/night cycle effects~~

#### Weather Types Implemented
- Clear, Partly Cloudy, Cloudy, Fog
- Drizzle, Rain, Heavy Rain
- Snow, Thunderstorm with lightning

**Note:** Weather system removed from public release to avoid external API dependencies.

### [0.1.0] - Development - Initial Implementation

#### Added
- React + Three.js foundation
- All 50 BART stations with coordinates
- 6 color-coded lines (Red, Orange, Yellow, Green, Blue, Beige)
- Track rendering using TubeGeometry
- Station markers with colored halos
- Basic camera controls (rotate, zoom)
- Dark theme aesthetic

#### Technical Stack
- React 18 with hooks
- Three.js for 3D rendering
- Tailwind CSS for styling
- Vite for build tooling

---

## API References (FOR DOCUMENTATION ONLY)

**These APIs are NOT used in the public release but are documented for anyone who wants to add realtime features privately:**

### BART Legacy API (Not Included)
- Endpoint: `https://api.bart.gov/api/etd.aspx`
- Documentation: https://api.bart.gov/docs/overview/index.aspx
- Requires: API key (free registration)
- Returns: Realtime ETD data

### Open-Meteo Weather API (Not Included)
- Endpoint: `https://api.open-meteo.com/v1/forecast`
- Documentation: https://open-meteo.com/
- Requires: No API key
- Returns: Weather data by coordinates

---

## Files Removed for Public Release

The following were present during development but **removed** for the sanitized GitHub version:

| File/Feature | Reason Removed |
|--------------|----------------|
| BART API integration | Proprietary endpoint |
| API key constants | Security/licensing |
| Weather API calls | External dependency |
| "LIVE" status indicators | Misleading for demo |
| Real ETD data parsing | Requires API access |

---

## Deployment Checklist

Before publishing to GitHub, verify:

- [ ] No API keys in any file
- [ ] No `api.bart.gov` URLs
- [ ] No "LIVE" or "realtime" claims
- [ ] All files contain disclaimer header
- [ ] README includes full legal notice
- [ ] LICENSE includes BART disclaimer
- [ ] Mock data generator is sole data source
- [ ] "SIMULATED" label visible in UI

---

## License

MIT License - See LICENSE file

**Additional Disclaimer:**
This software is not affiliated with BART. All data is simulated.
For official BART information, visit: https://www.bart.gov

---

## Contributing

When contributing, ensure:
1. No realtime API endpoints are added
2. No copyrighted BART assets are included
3. Disclaimers remain in all files
4. Mock data is clearly labeled as simulated
