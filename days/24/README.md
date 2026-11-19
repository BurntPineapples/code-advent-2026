# Day 24 · Gingerbread Gait

80 gingerbread creatures made of gumdrops and icing bars, and none of them knows how to walk. Generation 0 mostly flops and twitches. Each generation the furthest walkers become parents, and within a few minutes you're watching cookies that scuttle, hop and inchworm across the snow, with gaits nobody designed.

## Run it
Open `index.html` in any browser. Evolution starts by itself.

- Each generation, the **top 10** replay their test run. The leader wears a face, and the others are faint ghosts.
- **⏩ Turbo evolve** skips the replays and breeds as fast as your computer can, showing the record holder. Turn it off to watch again.
- The **chart** shows the best and median distance per generation. The **hall of fame** on the left keeps a snapshot every time the record jumps.
- **🍪 New batch** starts again from random blobs. Every run evolves something different.

## How the magic works
Each creature is a **genome**: a list of gumdrops (position, plus a "grip" value; red ones are sticky, green ones are slippery), a list of icing bars joining them, and for each bar a rhythm: how far it stretches (amplitude) and when (phase), all sharing one beat (period). Bars with zero amplitude are rigid bones, the rest are muscles. The physics is **position-based dynamics**: every gumdrop remembers where it was a moment ago (Verlet integration), gravity pulls it down, and each bar is repeatedly nudged back toward its target length. Walking comes from **friction asymmetry**. A sticky foot holds while a slippery one slides, so a rhythmic wiggle turns into forward motion. Each creature gets a 12-second test, and fitness is how far its centre moved. The **genetic algorithm** keeps the 4 best unchanged (elitism). It fills most of the next batch with mutated copies of tournament winners: positions, grips and rhythms nudged, and now and then a gumdrop or bar added or removed. It also adds a few brand-new random cookies to keep ideas fresh. There's no crossover, so every child is a tweaked copy of one parent, and that's plenty. (Early versions found a physics bug that let them launch themselves 18 m into the air. Evolution is very good at finding bugs, which is why there's now a speed limit.)
