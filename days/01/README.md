# Day 1 · First Snow

Snow falls on a dark night sky. Wait a few seconds and it starts sticking to something you can't see, until a message has frosted itself out of thin air.

## Run it
Open `index.html` in any browser.

- **Drag** to brush the snow off the letters
- **Space** or **double-click** to shake everything loose
- Type in the box at the top right to hide **your own message**. The URL updates (`?msg=...`) so you can send someone the link.

## How the magic works
The message is drawn once into a tiny invisible canvas, one pixel per snow grain, and every opaque pixel is marked "sticky". Each falling flake checks the grid cell it's passing through. If that cell is sticky and still empty, there's a small chance per cell travelled that the flake freezes there, and it often drags a neighbour or two with it. Because the chance is small, flakes sink partway into the letters before sticking, so the words fill in evenly, like real frost, instead of only collecting on top. The stuck layer is one pixel per grain, scaled up with smoothing and a blue glow, which is why it looks soft instead of blocky.
