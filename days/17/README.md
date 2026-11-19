# Day 17 · Northern Lights

A winter night by a frozen lake: snowy mountains, a cabin with a lit window, and the aurora rippling overhead in green curtains that fade to violet. Look around, put the sound on, and trigger a solar storm.

## Run it
Open `index.html` in any browser with WebGL.

- **Drag** to look around the sky. The curtains stretch away in every direction.
- **⚡ Solar storm** sends the aurora into overdrive for about 12 seconds: faster, brighter, taller, with red and pink at the top, like the rare real ones.
- **♫ Sound** plays a slow ambient pad that opens up during a storm.

## How the magic works
Each aurora curtain is a mathematical sheet, not a texture: a wavy line across the landscape (built from smooth noise plus a slow sine) that's bright where you're close to it and fades with distance. The fine vertical streaks come from noise that varies only sideways, and the sharp lower edge with a slow fade upward copies how real aurora light is emitted at about 100 km altitude and thins out above. For every pixel, the shader **ray-marches** through the band of sky between those altitudes, adding up the glow of three curtains at 48 points along the ray. The colour changes with height, from oxygen green at the bottom to violet above (and red in a storm), which matches the physics of real auroras. A tiny per-pixel random jitter in the sample positions hides the banding. The mountains are *ridged fractal noise* in angle-space, the lake mirrors the whole sky with a little wobble, and the pine silhouettes are a row of random-height triangles.
