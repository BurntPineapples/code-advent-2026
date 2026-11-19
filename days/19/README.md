# Day 19 · Midnight Forest

Fly low along a winding path through an endless snowy pine forest at midnight. Lanterns light the way, some trees are wrapped in glowing lights, cabins glow between the trunks, the moon hangs over it all, and it snows. It never ends, and no two minutes are the same.

## Run it
Open `index.html` in a browser while online (it loads Three.js from a CDN).

- **Move the mouse** left and right to steer.
- **Hold the mouse button** (or **Space**) to speed up from a gentle 30 km/h to over 120.
- **🔔 Sound** adds wind that rises with your speed, plus sleigh bells.

## How the magic works
There are only 1,500 trees, yet the forest is endless. They're drawn with **instancing**: one tree shape uploaded to the GPU once, then drawn 1,500 times in one call, each copy with its own position, size and rotation. As you fly, any tree that slips behind the camera is **recycled** to the far end of the forest, with a fresh random spot beside the winding path (two sine waves added together), so you're always flying into new terrain. Lanterns, lights, cabins and snow loop the same way. Each tree's colour is baked into its vertices, green at the bottom of each tier fading to frost at the tips, so no textures are needed. The glow comes from **bloom post-processing**: the scene is rendered, the brightest pixels (bulbs, lanterns, windows, the moon) are cut out, blurred at several sizes and added back on top, which is how cameras and eyes see bright lights at night. Exponential fog in the sky's colour hides the forest's edge, and only the four lanterns nearest you carry real lights.
