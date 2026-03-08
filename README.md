# GBDA302 Week6 Example 04: HUD, Enemies & Audio

## Authors

Nicole Wu | n9wu | 21085480

## Description

This project is a side‑scrolling platformer built with p5.play (a p5.js
extension). It adds a heads‑up display, collectible leaves, boar enemies, fire
hazards, and rudimentary combat mechanics. A small world is constructed via a
tilemap, and the player can run, jump, attack, and collect items while avoiding
or defeating enemies. Sound effects and background music enhance the feedback.

## Gameplay

- **Move**: A/D or left/right arrows
- **Jump**: W or up arrow (higher jump tuned to clear obstacles)
- **Attack**: Space bar (hit enemies in front of you)
- **Restart**: R (when dead)

Leaves scattered in the level are collectibles; gathering enough triggers a
level transition. The first map contains exactly 15 mushrooms and has been
scaled back slightly with only a couple of boars and a pair of fire tiles so
new players can get a feel for the mechanics. The second map has also been
rebuilt programmatically: every row is exactly the same width and there are no
stray walls. To prevent the player from spawning inside enemies, the layout
places the ground one row below the start position and boars on the row above;
both the player and the pigs drop one tile before coming to rest, which keeps
the characters free to move. A full ground row followed by deep ground keeps
enemies patrolling in a reliable strip while leaves and a bit of fire add some
challenge, making level‑2 immediately playable. Two distinct maps are
provided. Boars patrol platforms, turn at edges or when encountering hazards /
other boars, and can be damaged by the player's attack. Contact with fire or a
boar reduces health; losing all health results in death.

## Features

- Tile‑based level construction with multiple maps
- Player animation states (idle/run/jump/attack/hurt/death)
- Boar AI using probes to detect ground, walls, fire, leaves, and other boars
- HUD displaying score and health using a bitmap font
- Sound effects for jumping, hitting, collecting, getting hurt, plus looping
  background music
- Simple world reset and level progression logic

## Assets & Credits

- **Visual sprites**: `playerSpriteSheet.png` and `enemySpriteSheet.png` were
  adapted from art at [Sunnyland Forest](https://ansimuz.itch.io/sunnyland-forest)
  (AnsImuz) – used under the site's terms.
- **Sound effects**: `hit.wav`, `hurt.wav`, `jump.wav`, and `collect.wav` were
  downloaded from [Freesound.org](https://freesound.org) and are credited to the
  respective authors (see metadata in the archive). Background music
  (`background music.wav`) was also sourced from Freesound.

## Technical Notes

- The game logic lives in `sketch.js`; asset loading happens in `preload()` and
  the world is constructed in `makeWorld()`.
- Level arrays (`level1`/`level2`) define tiles; an array of levels allows
  progression.
- Physics uses `p5.play` groups and sprites with manual stepping for pixel
  stability (`world.autoStep = false`).
- Sound is handled via p5.sound; files are loaded in `preload()` and played in
  response to events (jump, collect, hit, hurt) with background music looping.

## Running the Game

1. Open a terminal in this folder.
2. Start a simple server, e.g. `python -m http.server 8000`.
3. Navigate to `http://localhost:8000` in a browser that supports Web Audio.

## References

- [p5.js Documentation](https://p5js.org/reference/)
- [p5.sound Reference](https://p5js.org/reference/#/libraries/p5.sound)
- Dr. Karen Cochrane & David Han lecture materials, GBDA302
