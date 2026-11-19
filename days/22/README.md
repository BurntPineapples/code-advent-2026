# Day 22 · The Snow Conductor

Stand in front of your webcam and conduct a snowstorm. Your hands show up as glowing ice skeletons, and the snow reacts to them. Sweep it aside, squeeze it into a snowball, throw it, or draw with frost. Raise your hand and the blizzard (and the music) swells. Swoop down and a bell rings on the beat.

## Run it
Open `index.html` in a recent Chrome, Edge, Firefox or Safari and press **✋ Use my camera**. The page needs internet the first time, to download the hand-tracking model (about 8 MB).

- ✋ **Sweep** through the snow with your fingers
- ✊ **Make a fist** to pull the snow into a snowball. **Open your hand** to throw it.
- 🤏 **Pinch** thumb and index finger to draw with coloured frost
- ↕ **Raise a hand** for a blizzard, lower it for a hush
- ⤵ **Swoop down fast**, like a conductor, to ring a chord. Each beat moves to the next chord.

No camera? **🖱 Use the mouse instead**: hold the button for a snowball, hold Shift to draw frost.

> Browsers only allow the camera on `https://` pages or `localhost`, so it works on GitHub Pages. If you open the file straight from disk and the camera is refused, use the mouse mode, or run `python -m http.server` in the project folder and visit `http://localhost:8000/days/22/`.

## How the magic works
Each video frame goes to **MediaPipe Hands**, a pair of small neural networks that run on your own GPU. One finds palms in the picture. The other places **21 landmarks** on each hand: the wrist plus four joints per finger. Gestures are just geometry on those points. If your fingertips are close to your wrist compared with the size of your palm, that's a fist. If thumb tip and index tip touch, that's a pinch. The snow is a 2,600-particle system. Every fingertip pushes nearby flakes away and drags them along at the hand's speed. A fist becomes a gravity well that captures flakes into an orbiting ball. Opening the hand sends every captured flake off in a random direction at once. A "beat" is detected the way a conductor's downbeat looks: fast downward speed that suddenly stops. Each beat moves a synthesizer pad to the next chord, and how high your hand is picks the top note.
