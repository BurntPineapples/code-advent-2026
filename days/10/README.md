# Day 10 · Ornament Lathe

Draw the outline of half a Christmas ornament, and it spins into a shiny 3D bauble with real reflections. Choose a colour, pattern and finish, then hang your creations on a garland.

## Run it
Open `index.html` in a browser while you're online. It loads Three.js from a CDN, and there's nothing to install.

- **Draw** on the right half of the profile box, from top to bottom. The left half mirrors it as you go.
- Or start from a preset: **Classic, Teardrop, Onion, Bell, Icicle, Finial**.
- Pick **colours**, a **pattern** and a **finish** (Glossy, Chrome, Satin or Glitter).
- **Drag** the 3D view to orbit and **scroll** to zoom.
- **Hang it on the garland** adds the current ornament to the row along the top.

## How the magic works
A real lathe spins wood against a chisel, and this one spins your drawing around an axis. Your stroke is sampled into 64 radius-at-height values, lightly smoothed, then handed to `THREE.LatheGeometry`, which sweeps the 2D profile through 360° in 128 steps to build a closed surface of revolution. The shine comes from **physically based rendering**: a `MeshPhysicalMaterial` with metalness, roughness and a clear-coat layer, lit by an environment map pre-filtered from a virtual room (`RoomEnvironment` + `PMREMGenerator`), so every curve picks up believable reflections. The glitter finish is a home-made normal map of pure random noise: every texel tilts the surface a different way, so thousands of tiny facets catch the light. Patterns are painted into a canvas texture whose x-axis wraps around the ornament and whose y-axis runs top to bottom.
