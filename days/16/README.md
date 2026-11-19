# Day 16 · Snow Globe

A glass snow globe on a wooden table, with a cottage, a tree and a glowing star inside. Shake it and watch the snow swirl, drift down and settle. There are no 3D models: every pixel is computed by one GPU program.

## Run it
Open `index.html` in any browser with WebGL (any modern browser).

- **Shake it!**, **Space**, or a hard flick of the mouse shakes the globe.
- **Drag** to turn it round. Let go mid-drag and it keeps spinning.
- It lowers its resolution automatically if your graphics card is struggling.

## How the magic works
The whole scene is a single **fragment shader** that runs once for every pixel, in parallel on the GPU. Each pixel fires a ray from the camera. The glass sphere is hit with an exact ray-sphere formula, and at that point the ray **reflects** (a Fresnel blend that's stronger at grazing angles, which is why the rim looks glassy) and **refracts** into the globe. Inside, it's **sphere tracing**: the cottage, tree, star and ground are all described by *signed distance functions*, little formulas that say "how far is this point from the nearest surface", so the ray can safely leap forward by that distance until it touches something. Snowflakes are stored per column of an invisible grid. Each one's height is just `start height − speed × time since the shake`, clamped at the ground, plus an exponentially fading swirl, so the globe needs no simulation and no memory to remember where the snow is. The reflections show a made-up room (a window, a fire, a ring of fairy lights) built from a handful of glow functions.
