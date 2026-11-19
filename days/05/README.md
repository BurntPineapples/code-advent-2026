# Day 5 · Gift Within a Gift

A wrapped present. You open it, and there's another present inside. You open that one, and…

## Run it
Open `index.html` in any browser.

- **Press and hold** (or hold **Space**) to dive in. Lids rip off as you approach.
- **Scroll** to move back out, or to scrub through at your own pace.
- **M** mutes the paper-rip sound.
- Keep going. Every box has its own paper, ribbon and lining, a few have something tucked in a corner, and a handful of milestones are waiting for the dedicated.

## How the magic works
It's an **infinite zoom** (the Droste effect). Instead of moving a camera through a world that goes on forever, every box is drawn at `size = base × 0.6^(k − t)`, where `k` is the box number and `t` is how far in you are. Raise `t` by 1 and every box grows to exactly the size of the one that used to be around it, so the picture repeats perfectly and never runs out of detail. Only about 6–10 boxes are on screen at once, and any box number can be generated on demand: its paper, colours and trinket come from a tiny seeded random generator (`mulberry32(k)`), so box #4,812 always looks the same. Each box is also turned 0.16 rad more than the one around it, and the view rotates by the same amount as you go in, which turns the dive into a spiral. The rip is a burst of crinkly noise through a band-pass filter that sweeps from 4.5 kHz down to 900 Hz.
