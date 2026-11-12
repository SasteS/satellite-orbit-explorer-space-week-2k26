# 🛰️ Satellite Orbit Explorer

A Python-based two-body Keplerian satellite orbit propagator and visualization tool built during **Space Career Week 2026 (GNSS Academy)**.

The project ingests CelesTrak General Perturbations (OMM JSON) orbital records, converts mean motion into Keplerian orbital elements, propagates positions across a common UTC time grid using Greenwich Mean Sidereal Time (GMST) Earth rotation, and exports both 2D ground track maps and 3D animated KMLs for Google Earth Pro.

---

## Orbits Analyzed

| Satellite | Regime | Semi-Major Axis ($a$) | Period | Inclination ($i$) | Description |
|---|:---:|:---:|:---:|:---:|---|
| **PULSAR-0** | LEO | ~6,881 km | 1.58 h | 97.48° | Sun-synchronous, near-polar retrograde orbit. |
| **GSAT0225 (Galileo 29)** | MEO | ~29,600 km | 14.08 h | 55.22° | European GNSS constellation satellite. |
| **SES-5** | GEO | ~42,164 km | 23.93 h | 0.05° | Geostationary telecommunications satellite locked at 5°E. |
| **QZS-2 (Michibiki-2)** | IGSO | ~42,170 km | 23.94 h | 39.25° | Inclined geosynchronous orbit forming an analemma (figure-8) over Japan. |

---

## Key Features

1. **OMM JSON Ingestion**: Validates real CelesTrak GP orbital parameters (no hardcoded/invented data).
2. **Kepler Solver**: Solves Kepler's equation ($M = E - e \sin E$) via Newton-Raphson iteration.
3. **Earth Rotation (GMST)**: Converts orbital plane coordinates into an Earth-Centered, Earth-Fixed (ECEF) reference frame using IAU-1982 sidereal time rotation.
4. **Visualizations**:
   - 2D ground track scatter plot overlaying global coastlines.
   - Stacked orbital speed profiles over 24 hours.
5. **Google Earth Pro Export**:
   - `orbit_tracks_ecef.kml`: 3D Earth-fixed trajectories at true altitude.
   - `orbit_animation.kml`: Interactive, time-stamped ground tracks with antimeridian seam-handling.

---

## Tech Stack

- **Python 3.10+**
- **Libraries**: `matplotlib`, `requests`, `xml.etree.ElementTree`
- **Output Formats**: KML 2.2 (`gx:MultiTrack`), PNG (200 dpi), TXT reports

---

## How to Run Locally

1. **Clone the repository**:
   ```bash
   git clone https://github.com/<your-username>/satellite-orbit-explorer.git
   cd satellite-orbit-explorer
   ```

2. **Create and activate a virtual environment**:
   ```bash
   python -m venv .venv
   # On Windows:
   .\.venv\Scripts\activate
   # On macOS/Linux:
   source .venv/bin/activate
   ```

3. **Install dependencies**:
   ```bash
   pip install matplotlib requests ipykernel
   ```

4. **Launch the notebook**:
   Open `satellite_orbit_explorer.ipynb` in VS Code or JupyterLab and select the `.venv` kernel to run all cells.
