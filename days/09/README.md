# Day 9 · Chimney Drop

A one-button game. Fly the sleigh over a snowy town at night and drop presents down the chimneys. The catch is physics: presents slow down in the air, so you have to let go *before* you reach the chimney.

## Run it
Open `index.html` in any browser.

- **Space**, **click** or **tap** to drop a present.
- Consecutive hits build a **combo** that multiplies your score, and every 5 in a row refills your sack with 3 presents.
- **Golden chimneys** (with a star) are worth triple.
- Later on the sleigh speeds up, chimneys get narrower and the **wind** picks up (shown top right).
- The game ends when your sack is empty. Your best score is saved.

## How the magic works
Each present is launched with the sleigh's speed, but air drag pulls its horizontal velocity towards the wind speed every frame: `vx += (wind − vx) × 0.9 × dt`. Gravity adds `900 px/s²` downward. That small drag term is the whole game. Without it, the present would stay exactly under the sleigh and you'd drop right on top of the chimney. With it, the present lags behind by a distance that grows with speed and height, so your brain has to learn a "lead" that changes as the game speeds up. A hit is detected when the present crosses the chimney's top edge while falling and is inside the opening. The town is generated endlessly just off-screen to the right and thrown away once it scrolls off the left. Every sound (chimes, thuds, whooshes) is a Web Audio oscillator with a pitch or volume ramp.
