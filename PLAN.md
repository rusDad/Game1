# Top-Down 2D PvP Shooter Plan

## Architecture Overview
The game is a file://-safe browser game built with plain HTML, CSS, and vanilla JavaScript using a single HTML Canvas for world rendering and fixed DOM HUD overlays.

Core loop architecture:
1. `index.html` loads all scripts in dependency order via regular `<script src="...">` tags.
2. `src/main.js` boots the game and starts a `requestAnimationFrame` loop.
3. `src/game.js` owns state, update, and render orchestration.
4. Systems (`input`, `collision`, `weapons`, `pickups`, `renderer`, `ui`) are modular globals on `window`.

No modules, fetch, backend, bundler, npm, or framework are used.

## File Responsibilities
- `index.html`: Canvas + HUD shell and script loading.
- `README.md`: Run instructions, controls, architecture extension docs.
- `src/config.js`: All gameplay/render constants and data-driven definitions.
- `src/level_01.js`: Embedded tile-map data on `window.LEVEL_01`.
- `src/assets.js`: Image loading/asset registry.
- `src/input.js`: Key state tracking and scroll prevention.
- `src/collision.js`: Tile blocking checks + pixel AABB collision helpers.
- `src/weapons.js`: Weapon firing, cooldowns, projectile simulation/collision.
- `src/pickups.js`: Placeholder data-driven pickup system structure.
- `src/renderer.js`: Tile/world/player/projectile/effect rendering.
- `src/ui.js`: Fixed HUD updates independent from world camera.
- `src/game.js`: State setup, per-frame update, round reset logic.
- `src/main.js`: Bootstrapping.
- `.logs/*.md`: Plan / implementation / test logs.

## Implementation Phases
1. Scaffold required folders/files and baseline HTML/CSS shell.
2. Add config, level data, input, and asset loading systems.
3. Implement collision + player movement + facing.
4. Implement weapon/projectile system and hit resolution.
5. Implement round reset, respawn, HUD updates, and debug toggles.
6. Implement layered renderer with nearest-neighbor sprites.
7. Add pickup architecture placeholder.
8. Document in README and validate with manual checklist.

## Known Constraints
- Must run from `file://` (double-click `index.html`) on Windows.
- No ES modules and no local `fetch()` data loading.
- Map must render from tile strings, not a baked map image.
- Existing asset filenames are fixed for integration.
- Fixed camera with full map in viewport.

## Manual Test Checklist
- Open `index.html`; confirm game starts and map is visible.
- Confirm both players spawn opposite corners and render.
- P1 movement: WASD; P2 movement: Arrow keys.
- P1 fire: Space; P2 fire: Numpad 0.
- Hold movement and fire simultaneously for both players.
- Confirm wall collisions block players.
- Confirm projectiles are destroyed by walls.
- Confirm projectile hits reduce enemy health.
- Confirm death triggers win increment + respawn + reset health/projectiles.
- Confirm HUD remains fixed at screen top corners.
- Confirm `G` grid toggle, `C` collision toggle, `P` pause toggle.
