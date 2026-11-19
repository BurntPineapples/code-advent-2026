# Day 18 · Bauble Selfie

Five mirror-shiny baubles hang from a pine branch. Turn on your camera and you appear inside every one of them, stretched and curved like a real reflection, and tinted red, gold, green or blue. Then snap a Christmas card.

## Run it
Open `index.html` in a browser while online (it loads Three.js from a CDN). The camera needs the page to be served over `https://` or `localhost`, so on the published site it just works. If you open the file directly and the browser blocks the camera, the baubles reflect a cosy room instead.

- **📷 Turn on my camera**: allow access, then wave. Move your mouse for a little parallax.
- **🎄 Snap a Christmas card** downloads a PNG with "Merry Christmas!" written on it.
- **Privacy:** the video only ever exists inside this page. Nothing is uploaded, and nothing is saved unless you press Snap.

## How the magic works
Shiny 3D objects get their reflections from an **environment map**, a 360° panorama of the world around them. Normally that's a photo. Here it's a canvas repainted every frame: a warm room (windows, a fireplace, a string of lights) with your webcam pasted into the exact patch of the panorama that faces the viewer, at `u = 0.75` in equirectangular coordinates, which is the direction pointing back at the camera. The baubles use a fully metallic, almost perfectly smooth material, so the GPU looks up the panorama in the **reflected** direction for each pixel. Physics does the rest: the sphere's curvature produces the fish-eye stretch, and because a reflection naturally mirrors left and right, your image behaves exactly like a real mirror. Metallic surfaces tint their reflections with their own colour, which is why the red bauble shows a red you.
