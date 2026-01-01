# Barndo-nizer 🛠️🏡

Barndo-nizer is a simple, web-based Barndominium (aka "barndo") Floor Plan Generator. It helps you quickly sketch interior layouts for metal buildings that combine living space with workshop/garage areas — perfect for planning cozy, functional barndos. Generate grid-based layouts, view labeled room sizes, tweak dimensions, and export plans as PNG or PDF.  

Built for speed, clarity, and practicality — whether you're sketching ideas or preparing a layout to discuss with a builder.

---

## ✨ Features

- 🎯 Intuitive inputs for building dimensions (feet + inches)
- 🧱 Grid-based automatic layout generation
- 🏷️ Labeled rooms with dimensions shown on the plan
- 🔄 One-click generate / regenerate layouts (randomized variations)
- 📤 Export as PNG or PDF
- 🌙 Clean dark-themed UI for comfortable long sessions

---

## 🖼️ Screenshots

Main interface and example layout (30ft × 20ft building):

![Main app interface with sample generated layout](https://raw.githubusercontent.com/seetinc10/Barndo-nizer/main/screenshots/app-screenshot.jpg)

Real-world barndominium example:

![Example of a completed barndominium exterior](https://raw.githubusercontent.com/seetinc10/Barndo-nizer/main/screenshots/real-barndo-example.jpg)

---

## 🚀 Installation / Usage

(Assuming the app is a web project — adjust commands for your stack)

1. Clone the repository:
   ```bash
   git clone https://github.com/seetinc10/Barndo-nizer.git
   cd Barndo-nizer
   ```
2. Install dependencies (example using npm):
   ```bash
   npm install
   npm run dev   # or npm start
   ```
3. Open the app in your browser (usually http://localhost:3000 or port shown in terminal).  
4. Enter building dimensions (feet + inches), click "Update Dimensions", then "Generate Layout". Export using the PNG/PDF buttons.

---

## 🧠 How the algorithm works (high level)

This section explains the layout-generation approach used by Barndo-nizer — a practical, grid-driven packing/placement algorithm that balances room sizes, adjacency, and circulation.

1. Normalize dimensions → create grid
   - Convert the user-entered building length/width (feet + inches) to a working measurement (e.g., inches or feet).
   - Choose a grid resolution (for example, 1ft per cell or 1ft = 20px on canvas). The whole floor is represented as a 2D grid of cells.

2. Define room templates and priorities
   - Rooms are expressed in approximate sizes (e.g., Master: 14ft×12ft, Bedroom: 10ft×10ft, Bath: 6ft×8ft, Shop: variable).
   - Assign priorities/constraints: must-have (kitchen, bathroom), flexible (closet, porch), and large-volume (garage/shop).
   - Optionally allow user constraints (e.g., garage on left side).

3. Seed rooms (placement order)
   - Place high-priority or large rooms first (master suite, garage/shop).
   - Use heuristics to choose placement location: corners for private rooms, edge/garage-adjacent for workshops, center for living areas.

4. Greedy packing with adjacency & adjacency preferences
   - For each room in priority order:
     - Try to place it on the grid where it fits without overlap.
     - Prefer placements that satisfy adjacency rules (e.g., kitchen near living room, bathrooms near bedrooms).
     - If multiple placements possible, score them by heuristics (minimize corridor area, maximize natural adjacency).
   - If a room doesn't fit exactly, allow small dimension adjustments constrained by min/max sizes.

5. Circulation & door placement
   - After rooms are placed, detect circulation gaps between rooms.
   - Create minimal corridors or ensure direct door-to-room adjacency so the plan is connected.
   - Place doors on shared walls at suitable positions (not blocked by corners).

6. Iterative improvement and randomization
   - Optionally run a few quick local-improvement steps:
     - Try swapping similar rooms or shifting room edges to reduce wasted space.
     - Use small random perturbations to provide alternative layouts (useful for the "Generate new layout" button).
   - Keep best-scored configuration based on compactness, adjacency satisfaction, and proportion constraints.

7. Rendering and labeling
   - Convert the placed room cells to vector-style rectangles on a canvas.
   - Draw room outlines, fill colors, and place text labels with measured dimensions.
   - Scale canvas coordinates to the target export DPI for PNG/PDF.

8. Export
   - Export uses the rendered canvas snapshot and converts to PNG or embeds the image into a PDF (e.g., via canvas.toDataURL/ jsPDF or similar).

Notes:
- The algorithm is deliberately heuristic and deterministic with randomized seeds available — it’s optimized for readable, practical layouts rather than exhaustive architectural optimization.
- You can tweak grid resolution, room min/max sizes, and placement priorities to favor different layout styles (compact vs. open-plan, larger shop area, etc).

---

## 🧩 Example pseudo-workflow (simplified)

1. Input: 30ft × 20ft → grid 30×20 (1 cell = 1ft).
2. Priority list: [Garage/Shop, Master, Living, Kitchen, Bath, Bedroom(s)].
3. Place Garage at left edge (if specified) occupying 12×20 cells.
4. Place Master in a corner with 14×12 cells.
5. Fill remaining area with living/kitchen and bedrooms using greedy packing.
6. Add doors and minimal corridor, label rooms with sizes.
7. Render and allow export.

---

## ⚙️ Tips & Customization

- Increase grid resolution for more detailed layouts but expect longer generation times.
- Define custom room templates to reflect your personal needs (e.g., large workshop, multiple small bedrooms).
- Use the regenerate button to explore different randomized variations quickly.

---

## 🤝 Contributing

Contributions welcome! If you want to:
- Improve the algorithm (better heuristics, simulated annealing, genetic approach)
- Add UI features (drag-and-drop rooms, manual adjustments)
- Improve exports (vector SVG export, scale-aware dimensions)

Please open an issue describing the idea, or submit a PR.

---

## 📜 License & Contact

- License: (update this section with your chosen license)
- Author / Maintainer: seetinc10  
- Questions? File an issue or reach out via GitHub.

---

Have fun planning your barndo! 🎉 Build something useful, practical, and tailored to your lifestyle.
