# KV Island

A small god game in one HTML file. You watch over a procedurally generated 3D island, drawn with WebGL from a fixed angle, while a village grows across it. The villagers run their own lives; you nudge the world to help them.

**Play:** https://kaveish.github.io/kvisland/ (GitHub Pages serves `index.html` from the root of `main`). You can also open `index.html` straight from disk in any modern browser, on a phone or a desktop. There is nothing to install or build.

## What happens on the island

- **Villagers** chop wood, quarry stone, pick berries, fish, farm, build, pray, chat by the fire and sleep at night. Each has a name, an age, hunger and a mood. Tap one to see what they are doing.
- **One island, all sea around it:** every map is a single island whose whole coast fits on the map.
- **No words:** the interface uses icons and numbers only.
- **Needs** show as speech bubbles. When a villager stops and looks up at you, they are asking for something: 🍎 food, 🏠 a home, 🪵 wood, 🌳 more trees, 💧 rain for dry crops, ⛩️ a shrine. Happy villagers show ❤️ 😊 🎵.
- **Families** grow when a house has two adults, a spare bed and food in the store. Children grow up in three days and later move into new houses. Villagers die of old age, or of hunger if the food runs out.
- **Building takes wood** (and stone for some things). You choose the spot, the cost is taken from the store, and villagers do the work. Villagers also plan their own houses, farms and storehouses.
- **Plants and animals:** forests spread and regrow, berry bushes ripen, crops grow faster on wet soil, sheep graze, chickens lay eggs at a coop, birds fly over and fish jump.
- **Day and night:** a day lasts two minutes at 1× speed. At night windows and campfires glow, fireflies come out, and everyone heads home to sleep.
- **Weather:** rain clouds drift in from the sea every few days. Soil near water or a well stays moist; elsewhere it dries out.
- **Footpaths** wear into the grass where villagers walk most.

## Your powers

| Tool | What it does | Cost |
| --- | --- | --- |
| ✋ | Drag to pan, pinch or scroll to zoom, tap to inspect | free |
| 🔨 | House, farm, storehouse, well, fishing hut, chicken coop, shrine, campfire | wood / stone |
| ⛰️ 🌊 | Sculpt the terrain: raise land from the sea, build mountains to quarry, dig lakes | faith |
| 🌧️ | Summon a rain cloud | 15 faith |
| 🌱 | Plant trees, bushes and flowers on grass, or ripen crops and trees | 1 faith |
| 🪓 | Remove plants and boulders | free |

Faith (✨) builds up over time, faster when the village is fed, housed and happy. A shrine raises the limit and lets villagers pray for more.

To demolish a building, tap it with ✋ and press 🗑️ twice. Half the materials come back.

## Controls

- **Touch:** one finger uses the selected tool, two fingers always pan and zoom.
- **Mouse:** left button uses the tool, right or middle button drags the map, wheel zooms.
- **Keyboard:** arrows or WASD move the map, `1`–`7` pick a tool, space pauses, Esc returns to Look.
- The ▶ button in the top right cycles speed: 1×, 2×, 4×, pause.

## Title screen, saving and new islands

The game opens on a title screen with the island turning slowly behind it.

- ▶ continues the saved island, or starts the one on show.
- 🏝️ offers a new island, which rises out of the sea. 🎲 rolls another, and ↩️ goes back to the saved one. The save is only replaced when you press ▶.
- ☰ in the game returns to the title screen.

The island saves itself to the browser's local storage every few seconds and whenever you leave the page. Time does not pass while the page is closed.

## Code

Everything lives in `index.html`: plain JavaScript and WebGL, with no dependencies. The terrain is a 64×64 height map drawn as a lit mesh with a generated texture; trees, buildings and villagers are low-poly shapes built in code. Villagers find their way with a breadth-first search over walkable tiles.
