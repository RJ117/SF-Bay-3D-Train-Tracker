v1.1
# BART 3D Transit Visualizer

A stunning 3D visualization of the Bay Area Rapid Transit (BART) system built with React and Three.js. This project renders an interactive 3D map with train movements based on published schedules, station markers, and smooth camera controls.

---

## 🚨 IMPORTANT - NOT REAL-TIME 🚨

> ### ⚠️ THIS IS NOT REAL-TIME TRACKING ⚠️
>
> **This project is NOT affiliated with, sponsored by, or endorsed by BART (Bay Area Rapid Transit District).**
>
> **Data Sources:**
> - ✅ **Station locations** - Real data from public GTFS feeds
> - ✅ **Fares** - Real data from published BART fare charts
> - ✅ **Schedule patterns** - Based on published BART timetables
> - ❌ **Train positions** - Calculated from schedules, NOT live GPS tracking
>
> Train positions shown represent where trains **SHOULD BE** according to published schedules.
> They do **NOT** reflect actual current train locations or real-time delays.
> 
> **For real-time train tracking, visit: [bart.gov](https://www.bart.gov)**

---

## ✨ Features

- 🗺️ **3D Map Visualization** - Full 3D rendering of the BART system using Three.js
- 🚃 **Animated Trains** - Simulated train movements with ribbon trails
- 🎯 **50 Stations** - All BART stations with accurate geographic positioning
- 🎮 **Interactive Controls** - Pan, rotate, zoom with mouse/keyboard
- 📍 **Station Navigation** - Click stations or use dropdown to fly to locations
- 💰 **Fare Calculator** - Estimate fares based on distance (informational only)
- 🌙 **Dark Theme** - Beautiful night-mode aesthetic with glowing effects

## 🚀 Quick Start

### Prerequisites

- Node.js 18+ 
- npm or yarn

### Installation

```bash
# Clone the repository
git clone https://github.com/yourusername/bart-3d-visualizer.git
cd bart-3d-visualizer

# Install dependencies
npm install

# Start development server
npm run dev
```

### Build for Production

```bash
npm run build
```

## 🎮 Controls

| Input | Action |
|-------|--------|
| Left-click + drag | Rotate camera |
| Right-click + drag | Pan/move view |
| Scroll wheel | Zoom in/out |
| WASD keys | Pan around map |
| Q/E keys | Zoom in/out |
| Click station | Fly to station |
| Click train dot | View train info |

## 📁 Project Structure

```
bart-3d-visualizer/
├── src/
│   ├── components/
│   │   └── BART3DVisualizer.jsx    # Main 3D visualization component
│   ├── data/
│   │   ├── stations.js              # Static station data (GTFS-derived)
│   │   ├── routes.js                # Track route definitions
│   │   └── mockTrains.js            # Simulated train generator
│   ├── utils/
│   │   ├── fareCalculator.js        # Fare estimation utilities
│   │   └── geoUtils.js              # Geographic conversion helpers
│   ├── App.jsx
│   └── main.jsx
├── public/
├── package.json
├── README.md
└── LICENSE
```

## 📊 Data Sources

This project uses **only** the following data:

1. **Station Coordinates** - Derived from [BART GTFS Static Feed](https://www.bart.gov/schedules/developers/gtfs) (public domain)
2. **Route Geometry** - Programmatically generated track paths
3. **Mock Train Data** - Randomly simulated train positions for visualization

**No realtime APIs, proprietary data, or copyrighted assets are used.**

## 🔧 Configuration

### Adding Your Own Realtime Data (Optional)

If you wish to add realtime train tracking for personal use, you can:

1. Obtain API access from [BART Developer Resources](https://www.bart.gov/schedules/developers)
2. Create a `.env.local` file with your credentials
3. Implement your own data fetching in `src/utils/realtimeAdapter.js`

**Note:** Any realtime integration you add is your responsibility. This repository intentionally excludes all API endpoints and keys.

## 🛠️ Tech Stack

- **React 18** - UI framework
- **Three.js** - 3D rendering engine
- **Vite** - Build tool and dev server
- **Tailwind CSS** - Styling

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🤝 Contributing

Contributions are welcome! Please read the following guidelines:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Contribution Rules

- Do not add any realtime API endpoints or keys
- Do not include copyrighted BART logos or assets
- Ensure all data sources are publicly available
- Maintain the disclaimer in all derivative works

## 🙏 Acknowledgments

- Station coordinate data derived from public GTFS feeds
- Three.js community for excellent documentation
- React team for the fantastic framework

## 📬 Contact

For questions or feedback, please open an issue on GitHub.

---

**Remember:** This is a visualization demo only. For actual BART schedules and realtime information, please visit [bart.gov](https://www.bart.gov).


v1 # SF-Bay-3D-Train-Tracker
High-fidelity 3D transit visualizer using static GTFS data (no real-time or proprietary APIs). Not affiliated with BART.


⚠️ Disclaimer
This project is not affiliated with, sponsored by, or endorsed by BART or any transit agency. 
All data used is static GTFS data publicly provided for general use. 
No real-time, proprietary, or restricted BART APIs are used.
