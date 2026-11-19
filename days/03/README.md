# Day 3 · No Two Alike

Real snowflakes grow out of a single frozen seed, live, one after another. Each one is different, and they collect in a gallery along the bottom.

## Run it
Open `index.html` in any browser.

- It runs by itself: each flake grows for about 10 seconds, rests, and a new one starts.
- **N** or **New flake** skips ahead. **Save PNG** downloads the current flake.

## How the magic works
This is **Reiter's snowflake model**, a cellular automaton on a hexagonal grid. Every cell holds some amount of water. Cells with at least 1 unit are ice. Ice cells and their direct neighbours are "receptive": they hold on to their water and slowly gain more from the air (γ). Every other cell just shares its water with its six neighbours, which is diffusion (α), against a background vapour level (β). That's the whole rule. Nobody programs the six arms or the side branches. They appear because a tip sticking out into the damp air grabs vapour faster than the hollows behind it, so tips grow faster and faster. The hex grid gives the six-fold symmetry, and each new flake picks random α/β/γ values, which is why you get ferns, stars and plates. The colouring shows *when* each cell froze, which brings out the growth rings, plus a highlight on the frozen edge.
