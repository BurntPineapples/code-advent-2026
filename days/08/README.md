# Day 8 · Light the Tree

The fairy lights on the tree are all wired up wrong. Turn the branches until power flows from the trunk to every bulb, and the star comes on.

## Run it
Open `index.html` in any browser.

- **Click** a piece to turn it clockwise, **right-click** to turn it back.
- Light flows through the wires as you connect them, and each new bulb chimes.
- Light every bulb to finish the level. The next tree is a row taller, and your best move count per level is saved.
- **New tree** deals a fresh puzzle at the same level.

## How the magic works
Every puzzle is generated, and guaranteed solvable, because it starts solved. The tree-shaped grid is filled with a **random spanning tree** using randomised Prim's algorithm: start at the cell above the trunk, keep a list of walls between "connected" and "not yet connected" cells, knock down a random one, and repeat. Every cell is then reachable by exactly one path, and the dead ends become the bulbs. Then every piece gets a random 0–3 quarter-turns. Each piece's wires are 4 bits (N, E, S, W), and a quarter-turn is a bit rotation: `((m << 1) | (m >> 3)) & 15`. After every click a breadth-first search floods power out from the trunk, crossing between two pieces only when both have a wire on the shared edge. Each piece lights up after a delay proportional to its BFS distance, which is what makes the light visibly *flow* up the tree.
