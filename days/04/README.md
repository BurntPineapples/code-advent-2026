# Day 4 · Hearth

A crackling fireplace drawn entirely in text characters. The flames flicker, sparks drift up, the wallpaper glows with the firelight, and the fire burns down unless you keep feeding it.

## Run it
Open `index.html` in any browser.

- **Click** to throw another log on: the flames flare up and sparks burst out.
- **Sweep the mouse sideways** to send a draught through the room, and the flames lean with it.
- **Sound** (top right) turns on crackles and a low rumble. Every sound is synthesised from noise in your browser. Nothing is recorded.
- Leave it alone and after about a minute the fire dies down to embers.

## How the magic works
The flames use the classic **"doom fire"** trick from 1990s demos. The bottom row of a grid is set to "hot". Every frame, each cell copies the heat of the cell below it, a little cooler and nudged randomly one column left or right. That tiny rule makes the heat climb, cool and wobble into flame tongues. Each cell's heat then picks a character (sparse `.,:` when cool, dense `0 8 @` when hot) and a colour from black through red and orange to white. Two tricks make it glow: a tiny copy of the heat map is drawn blurred behind the text, and every static character in the room (bricks, stockings, wallpaper) is lit by the fire's average brightness, faded with distance. The sound is pure Web Audio: short band-passed bursts of white noise for crackles, and slowly wandering "brown" noise through a low-pass filter for the roar.
