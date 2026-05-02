# Local Top-Down 2D PvP Shooter (v1)

## Run
1. Copy the whole folder to a Windows PC.
2. Double-click `index.html`.
3. Game runs directly from `file://` (no server required).

## Controls
- Player 1 Move: `W A S D`
- Player 1 Fire: `Space`
- Player 2 Move: `Arrow Keys`
- Player 2 Fire: `Numpad 0`
- Debug: `G` grid, `C` collision mode toggle, `P` pause

## Assets used
- floor_title_0.png
- floor_title_1.png
- floor_title_2.png
- wall_1.png
- player_one_down.png
- player_one_down_move.png
- player_two_down.png
- player_two_down_move.png
- muzzle_flash_down.png
- laser_beam_horizontal.png
- laser_beam_vertical.png

## Add a new weapon
1. Add a weapon entry under `WEAPONS` in `src/config.js`.
2. Add fire/behavior logic in `src/weapons.js` if needed.
3. Set `player.weapon` to the new weapon key in `src/game.js`.

## Add a pickup
1. Add pickup definition under `PICKUP_DEFS` in `src/config.js`.
2. Add spawn data in `src/pickups.js`.
3. Add pickup effect handling in pickup update/collision flow.
4. Render sprite in `Pickups.render`.

## Edit the map
- Modify `window.LEVEL_01.tiles` in `src/level_01.js`.
- Legend:
  - `0`: floor_0
  - `1`: floor_1
  - `2`: floor_2
  - `W`: wall (blocking)
