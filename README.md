# Barndo-nizer 🏡🔨🤠

**Random Floor Plan Layout Generator** 🛠️✨

Endless rustic barndominium-inspired layouts with one click! 🚀🏠

## What It Does 🌟

Generates random 2D floor plans for spacious, open-concept barndominiums! 📐🏠

- Sliders for building size, bedrooms, baths, etc. 👆
- Click generate ➡️ Unique layout every time!
- Features: Labeled rooms, thick walls, animated door swings 🚪✨

Great for inspiration or fun brainstorming! 💡😎

### Dream Interiors & Layouts 🖼️

## How the Algorithm Works 🔍🧠

The current generator uses a **simple recursive subdivision + room placement** approach (common in basic procedural floor plans):

1. Start with a large rectangular building envelope 📏
2. Place key rooms first (e.g., large open living/kitchen area in the center) 🏠
3. Recursively subdivide remaining space into smaller rectangles ➗
4. Assign room types (bedrooms, baths, utility) to subdivisions based on size & count 🎲
5. Add doors/connections with fun animated swings 🚪
6. Draw everything on canvas/SVG ✏️

This creates connected, logical layouts quickly – perfect for barndo-style open plans!

### Example Procedural Outputs 📊

## Cooler Possibilities & Upgrades 🚀🔥

Want even better layouts? Here are advanced alternatives to implement:

### Wave Function Collapse (WFC) 🌊🧩
- Powerful constraint-based algorithm (famous for dungeons & towns)
- Define "tiles" (room types, wall patterns) with adjacency rules
- Propagates possibilities until a valid floor plan "collapses"
- Guarantees realistic, non-overlapping rooms with perfect connections!

### Examples of WFC in Action 🏰

### Other Ideas 💡
- **Graph-based placement**: Model rooms as nodes, desired connections as edges 📈
- **Binary Space Partitioning (BSP)**: Like old-school dungeon generators ➗
- Add furniture, 3D export, or style themes (modern, rustic, etc.) 🛋️

PRs for these upgrades very welcome! 🤝

## Quick Start 🚀

1. Clone it 📥
2. Open `index.html` or run `python main.py` 🖥️
3. Generate endless barns! 🎉

## Tech Stack 🛠️

- HTML / JS / Canvas 🎨
- Python Flask 🐍

---

**Randomize your dream barndo today!** 🏡✨🤠

⭐ Stars power the generator! 🌟
