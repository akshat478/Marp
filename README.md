# OSM R-Tree Leaflet Spatial Indexing Project

> **Comprehensive Documentation**: For an in-depth, mathematical, architectural, and algorithmic explanation of the entire project, please refer to [PROJECT_EXPLANATION.md](file:///c:/Users/a12ks/Downloads/R/osm-r-tree-leaflet/PROJECT_EXPLANATION.md).

---

## Overview
This project demonstrates high-performance spatial indexing using the **R-Tree** data structure to index and query OpenStreetMap (OSM) geographic data. It integrates with **Leaflet** for interactive map visualization, comparing hierarchical R-tree bounding box queries against naive brute-force linear scans in real-time.

### Highlights
- ⚡ **R-Tree vs. Brute-Force Telemetry**: Live HUD panel displaying real-time query latency (ms) and performance speedups on every map pan and zoom.
- 🌳 **Hierarchical MBR Visualization**: Visualizes Minimum Bounding Rectangles (MBRs) across internal and leaf tree levels directly on the map.
- 🎬 **Animated Traversal (Showcase Mode)**: Step-by-step visual playback showing explored tree branches (blue) vs. pruned branches (red).
- 🖱️ **Shift + Drag Bounding Box Search**: Draw custom spatial selection windows on the map to query intersecting features.
- 🏛️ **Dual-Architecture**:
  1. **Interactive Web App (`src/`)**: Powered by TypeScript, Leaflet, Vite, and RBush, loading 4,000 real-world amenity nodes across New Delhi via the OSM Overpass API.
  2. **Pure Guttman R-Tree Engine (`files/`)**: Zero-dependency implementation of Antonin Guttman's 1984 R-Tree paper (Quadratic Split, CondenseTree, Morton bulk load, Min-Heap $k$-NN search) with a 1,830+ test benchmark harness delivering **~280x speedup** on 100,000 items.

---

## Quick Start

### 1. Install Dependencies
```bash
npm install
```

### 2. Run Interactive Web App
```bash
npm run dev
```
Open your browser at `http://localhost:5173/` (or the port indicated by Vite).

### 3. Build for Production
```bash
npm run build
```

### 4. Run Algorithmic Benchmark & Invariant Tests
```bash
npx tsx files/test.ts
```

---

## Project Structure

```
osm-r-tree-leaflet/
├── PROJECT_EXPLANATION.md            # Exhaustive project documentation & technical paper
├── README.md                         # Project overview & quick start
├── index.html                        # Web app entry point & dark theme styles
├── src/                              # Interactive web application
│   ├── main.ts                       # App bootstrap, Overpass fetch & tree initialization
│   ├── map/
│   │   └── mapView.ts                # Leaflet map, HUD panel, controls, animation engine
│   ├── rtree/
│   │   ├── RTree.ts                  # RBush spatial wrapper, telemetry & traversal inspector
│   │   └── types.ts                  # Abstract R-Tree & MBR interfaces
│   ├── osm/
│   │   ├── osmLoader.ts              # Live Overpass API client
│   │   ├── types.ts                  # OSM feature & response typings
│   │   └── cityData.ts               # Offline fallback dataset of 1,500+ Indian cities
│   └── logging/
│       └── logger.ts                 # Logging utilities
├── files/                            # Standalone custom R-Tree engine
│   ├── rtree.ts                      # Dependency-free Guttman (1984) R-Tree implementation
│   ├── geo.ts                        # GeoJSON arbitrary geometry bounding box utilities
│   ├── leaflet-integration-example.ts# Minimal Leaflet + custom RTree integration example
│   └── test.ts                       # 1,830+ test suite & 100,000-item benchmark harness
├── tests/                            # Unit tests
│   ├── RTree.test.ts                 # R-Tree unit test suite
│   └── osmLoader.test.ts             # Overpass loader unit test suite
├── package.json                      # Dependencies and npm scripts
├── tsconfig.json                     # TypeScript compiler configuration
└── vite.config.ts                    # Vite bundler configuration
```

For complete technical details, mathematical formulas, and algorithmic breakdowns, see [PROJECT_EXPLANATION.md](file:///c:/Users/a12ks/Downloads/R/osm-r-tree-leaflet/PROJECT_EXPLANATION.md).