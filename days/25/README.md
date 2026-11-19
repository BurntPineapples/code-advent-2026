# Day 25 · The Grand Tree

Merry Christmas! Press **Light the tree**. Falling snow gathers into a Christmas tree of 60,000 glowing points, with a garland of lights chasing up it, while a music-box waltz plays. On every beat of the first verse an ornament pops onto the tree: 24 beats, 24 ornaments, one for each day of this calendar. Then the star lights up and the finale begins: fireworks, a star, a snowflake, a message, and finally snow that falls and builds the tree again.

## Run it
Open `index.html` in a browser with WebGL. It needs internet the first time, for Three.js from a CDN. Turn your sound on.

- **Hover an ornament** to see which day it is, and **click** it to jump there. Ornaments for days you opened glow brightly. The dim ones are days you missed.
- **Drag** to spin the tree.
- **Click the star** or press **✨ Finale** to see the finale again. **↻ Again** replays everything from the snow.

## How the magic works
Every shape here (tree, fireworks, star, snowflake, the words) is the **same 60,000 points** in a different arrangement. Each point carries two positions and two colours, "from" and "to". The GPU's vertex shader blends between them with a single number, `uMorph`. Each point gets its own random head start and a sideways swirl while it's moving, so shapes pour into each other instead of sliding in a straight line. The falling snow is computed in the shader too (`mod(y − time × speed)`), so snow can turn into a tree without any frame-by-frame bookkeeping. The words are made by drawing text onto a hidden canvas and sampling its pixels. The garland's chasing lights are a sine wave of height and angle. A **bloom** pass makes anything bright glow. The waltz is original, written for this calendar, and played by code: every note is a few sine waves shaped like a music-box tine, with a waltz bass, a soft pad and a synthetic reverb. One clock schedules both the music and the visuals, so ornaments land exactly on the beat.

Thanks for opening all the doors. 🎄
