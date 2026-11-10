# KV Island

A small god game in one HTML file. You watch over a procedurally generated 3D island, drawn with WebGL as a sunlit toy diorama, while a village grows across it. The villagers run their own lives; you nudge the world to help them.

**Play:** https://kaveish.github.io/kvisland/ (GitHub Pages serves `index.html` from the root of `main`). You can also open `index.html` straight from disk in any modern browser, on a phone or a desktop. There is nothing to install or build.

## What happens on the island

- **Villagers** chop wood, quarry stone, pick berries, fish, farm, build, pray, chat by the fire and sleep at night. Each has a name, an age, hunger and a mood. Tap one to see what they are doing.
- **One island, all sea around it:** every map is a single island whose whole coast fits on the map. Palms fringe the beaches, pines climb the hills and the odd tree turns gold.
- **No words:** the interface uses icons and numbers only, drawn from the game's own icon set.
- **Needs** show as speech bubbles. When a villager stops and looks up at you, they are asking for something: an apple for food, a house for a home, a log for wood, a tree for more trees, a water drop for rain on dry crops, a red gate for a shrine. Happy villagers show hearts, smiles and music notes.
- **Families** grow when a house has two adults, a spare bed and food in the store. Children grow up in three days and later move into new houses. Villagers die of old age, or of hunger if the food runs out.
- **Building takes wood** (and stone for some things). You choose the spot, the cost is taken from the store, and villagers do the work. Villagers also plan their own houses, farms and storehouses.
- **Plants and animals:** forests spread and regrow, berry bushes ripen, crops grow faster on wet soil, sheep graze, chickens lay eggs at a coop, birds fly over and fish jump.
- **Day and night:** a day lasts two minutes at 1× speed. The sun crosses the sky and every tree, house and villager casts a shadow that swings round with it. At night windows and campfires glow, fireflies come out, and everyone heads home to sleep.
- **Weather:** rain clouds drift in from the sea every few days and trail their shadows over the hills. Soil near water or a well stays moist; elsewhere it dries out.
- **Footpaths** wear into the grass where villagers walk most.

## Your powers

The row of keys along the bottom holds your tools, in this order:

| Key | Tool | What it does | Cost |
| --- | --- | --- | --- |
| 1 | Hand | Drag to pan, pinch or scroll to zoom, tap to inspect | free |
| 2 | Hammer | House, farm, storehouse, well, fishing hut, chicken coop, shrine, campfire | wood / stone |
| 3, 4 | Raise, lower | Sculpt the terrain: raise land from the sea, build mountains to quarry, dig lakes | faith |
| 5 | Rain cloud | Summon a rain cloud | 15 faith |
| 6 | Sprout | Plant trees, bushes and flowers on grass, or ripen crops and trees | 1 faith |
| 7 | Axe | Remove plants and boulders | free |

Faith (the sparkle) builds up over time, faster when the village is fed, housed and happy. A shrine raises the limit and lets villagers pray for more.

To demolish a building, tap it with the hand and press the bin, then the tick. Half the materials come back.

## Controls

- **Touch:** one finger uses the selected tool, two fingers always pan and zoom. Let go mid-swipe and the map glides to a stop.
- **Mouse:** left button uses the tool, right or middle button drags the map, wheel zooms towards the pointer.
- **Keyboard:** arrows or WASD move the map, `+` and `-` zoom, `1`–`7` pick a tool, space pauses, Esc returns to the hand.
- The camera tips down towards the village as you zoom in and flattens into a map view as you zoom out.
- The play key in the top right cycles speed: 1×, 2×, 4×, pause.

## Title screen, saving and new islands

The game opens on a title screen with the island turning slowly behind it.

- The big play button continues the saved island, or starts the one on show.
- The island button offers a new island, which rises out of the sea. The dice roll another, and the return arrow goes back to the saved one. The save is only replaced when you press play.
- The menu key in the game returns to the title screen.

The island saves itself to the browser's local storage every few seconds and whenever you leave the page. Time does not pass while the page is closed.

## Code

Everything lives in `index.html`: plain JavaScript and WebGL, with no dependencies.

- **Terrain** is a 64×64 height map drawn as a lit mesh with a painted texture. Trees, buildings and villagers are low-poly shapes built in code.
- **Light** comes from a sun with a shadow map, fitted each frame around what the camera can see, plus soft sky light, firelight at night and a little distance haze.
- **Water** is one shader: it reads the height map to find the shore, where it draws foam lines that roll in, and scatters drifting highlights further out.
- **Interface** is HTML over the canvas: inked paper tiles and a set of about seventy SVG icons defined in the script.
- **Villagers** find their way with a breadth-first search over walkable tiles.
- **Frame rate:** if a device cannot hold 30 frames a second, the game lowers its render resolution, and as a last step swaps the shadow map for simple blob shadows. Add `#hq` to the address to keep full quality.
