# BuildVerse

**Team The Game Changers · Hack Day S01 Genesis · St. Peter's College of Engineering and Technology**

BuildVerse takes a family from a plot of land to a safe, costed 3D home design in minutes. It also includes **Richter Rise**, a 3D game that teaches earthquake engineering by letting you build a tower and survive a quake.

Everything runs in the browser, including the 3D engine and the neural network. Nothing to install and no server. It also works offline once opened.

| Part | File | What it does |
|---|---|---|
| BuildVerse Studio | `index.html` | Land plotting, auto blueprint, 3D model, safety analysis, AI cost prediction |
| Richter Rise | `game.html` | 3D tower-stacking + earthquake survival game |
| BV3D engine | `engine3d.js` | Our own WebGL2 3D engine used by both |
| Mobile app | `manifest.webmanifest`, `sw.js` | Installable Progressive Web App with offline cache |

## How to run

- **Online:** open the GitHub Pages link (see below).
- **Offline:** download the repo and double-click `index.html`. Chrome or Edge is recommended.
- **As a phone app:** open the link in Chrome on Android, then choose *Add to Home screen*.

## BuildVerse Studio: five drawing sheets

The app is organised like an engineering drawing set. Each sheet feeds the next.

1. **C-01 Land & Plot:** enter a rectangular plot, or tap corner stones on a survey grid (house plot, large plot or farm land). You get the area in sq ft, m², cents, grounds, acres and hectares, plus the perimeter, setbacks, buildable footprint, ground coverage and how many floors the FSI allows.
2. **A-01 Blueprint:** a floor plan is generated for 1–4 BHK, with walls, doors, windows, staircase, pooja room, stilt parking and dimensions in feet and inches. Every room is checked against the **NBC 2016** minimum sizes. The plan can be downloaded as SVG.
3. **A-02 3D Model:** the plan is extruded into a 3D house in Modern, Contemporary or Traditional (terracotta roof) style. It includes a compound wall, trees, a rooftop water tank and solar panels. Two extra tools:
   - **Cutaway view** to see inside the rooms.
   - **Sun study** to watch shadows move from 6 AM to 6 PM.
4. **S-01 Safety Analysis:** an **IS 1893:2016** equivalent static earthquake calculation. It covers:
   - Zone factor, soil type and natural period
   - Sa/g, the design coefficient Ah, seismic weight and base shear
   - Storey forces and the response spectrum graph
   - An **IS 875-3** wind load check

   A rule-based expert system turns all of this into an explainable **design-risk index** (out of 100) with a precaution checklist covering design, foundation, site safety and fire safety.
5. **Q-01 AI Cost & Materials:** a **neural network** (13 inputs → 24 ReLU neurons → 2 outputs, Adam optimiser) trains live in the browser on 600 sample projects. It predicts:
   - Construction cost with an 80% range
   - Build time

   The sheet also shows the training curve, R² and error, permutation feature importance, a cost breakdown, material quantities (cement, steel, M-sand, aggregate, bricks, paint, tiles) and a Gantt timeline.

## Richter Rise: the game

1. **Build:** floors swing in from a tower crane. Tap or press Space to drop each one. Any overhang gets sliced off, so narrow floors are weak floors. Three perfect drops in a row grow the floor back.
2. **Retrofit:** spend coins on real earthquake engineering:
   - Steel cross-bracing
   - A tuned mass damper
   - Base isolators
   - A deep pile foundation
3. **Survive:** an earthquake hits. The tower is simulated as a **shear-building model**, with masses, storey springs and dampers solved 1,200 times a second. If a storey drifts past its limit it fails, and the floors above collapse. Keep 60% of the floors standing to face a stronger quake.

## Technology

- HTML5, CSS3 and JavaScript, with GLSL shaders
- Custom WebGL2 renderer: soft shadow maps, fog, sky with sun glow, procedural lit windows, ACES tone mapping and frustum culling
- Neural network and Adam optimiser written from scratch
- SVG charts with hover read-outs, light and dark theme, and mobile layout
- No external libraries, so the app works offline

## Engineering references

- IS 1893 (Part 1):2016, Criteria for Earthquake Resistant Design of Structures
- IS 875 (Part 3):2015, Wind Loads
- National Building Code of India 2016, Parts 3 and 4
- IS 13920:2016 and IS 4326:2013
- Tamil Nadu Combined Development and Building Rules, 2019
- A. K. Chopra, *Dynamics of Structures* (shear-building model)
- Kingma & Ba, *Adam: A Method for Stochastic Optimization*, 2015

## Disclaimer

BuildVerse is an educational prototype. Cost data comes from synthetic sample projects based on 2025–26 Tamil Nadu rate ranges, and the engineering checks are simplified. Real buildings need drawings approved by the local authority and structural designs signed by a licensed engineer.
