# Code Advent 2026 🎄

A coding advent calendar: **25 small Christmas programs**, one behind each door, from December 1 to Christmas Day. Each one is meant to make you go *"wait, that's cool"*. There are toys, games, simulations, little AIs that learn while you watch, and a finale on the 25th.

Everything runs in the browser. Nothing to install, nothing to build.

## How to use your advent calendar

**1. Open the calendar.** Open `index.html` in a modern browser (Chrome, Edge, Firefox or Safari), or visit the GitHub Pages link if this repo is published.

**2. Open today's door.** Doors unlock at midnight (your local time) on their date. Today's door pulses gold. Locked doors shake and tell you how long to wait. Opened doors stay open, and your browser remembers them.

**3. Play.** Every day is a single page with its own controls. A **← Calendar** link in the corner takes you back. Days with sound start muted until you click, because browsers require that.

**4. Read how it works.** Each day's folder has a `README.md` with what it does, how to drive it, and a short **"How the magic works"** section explaining the trick behind it.

**5. Christmas Day.** Door 25 is the big one. It gathers all 24 previous days into one place, so try to open the others first.

### Peeking early
Can't wait, or testing? Add `?peek` to the calendar URL (`index.html?peek`) and every door unlocks. `?peek=0` locks them again. There's also a secret word: type **northpole** anywhere on the calendar page.

### Running it locally
Double-clicking `index.html` works for almost everything. Two days use your **camera** (one shows you in a bauble, one tracks your hands), and browsers only allow cameras on `https://` or `localhost`. For those, either use the published GitHub Pages site or run a tiny local server in this folder:

```
python -m http.server 8000
```

then visit `http://localhost:8000`.

### What you need
- A browser from the last couple of years. A few of the later days use **WebGL / WebGL 2** (any normal laptop or phone GPU is fine) and lower their own quality on slower machines.
- An internet connection for the days that load a library from a CDN (Three.js, a hand-tracking model, a retro font). Everything else works offline.
- Sound on, for the musical days.

### Publishing your own copy
1. Push this folder to a GitHub repository.
2. In the repo go to **Settings → Pages**, set the source to **Deploy from a branch**, then pick `main` and `/ (root)`.
3. After a minute your calendar is live at `https://<username>.github.io/<repo>/`.

<details>
<summary><b>Spoilers: all 25 days</b> (don't open this if you want surprises)</summary>

| Day | Name | What it is |
|---:|---|---|
| 1 | First Snow | Snow settles on a hidden message |
| 2 | Fairy Lights | Strings of lights with real rope physics |
| 3 | No Two Alike | Grow a unique snowflake with a cellular automaton |
| 4 | Hearth | A crackling fire made of text characters |
| 5 | Gift Within a Gift | An infinite zoom through nested presents |
| 6 | The Music Box | A punch-card music box you compose on |
| 7 | The Neural Painter | A neural network learns to paint a picture, live |
| 8 | Light the Tree | Rotate the wires until the whole tree lights up |
| 9 | Chimney Drop | One-button present-dropping game |
| 10 | Ornament Lathe | Draw a curve and it spins into a 3D bauble |
| 11 | Murmuration | A 3D flock of birds swirling at dusk |
| 12 | Hot Cocoa | A fluid simulation you stir |
| 13 | The Carol Machine | A Markov chain writes new carols from old ones |
| 14 | Reindeer Flight School | Neuroevolution: reindeer learn to fly between chimneys |
| 15 | Bell Wave | A pendulum wave of hand bells |
| 16 | Snow Globe | A ray-marched snow globe in a shader |
| 17 | Northern Lights | An aurora over a frozen lake |
| 18 | Bauble Selfie | Your webcam reflected in a Christmas bauble |
| 19 | Midnight Forest | An endless flight through a snowy forest at night |
| 20 | A Million Snowflakes | One million GPU snowflakes under a street lamp |
| 21 | Santa's Route | Simulated annealing plans Santa's route. Can you beat it? |
| 22 | The Snow Conductor | Conduct a snowstorm with your hands (hand tracking) |
| 23 | SLEIGH-OS | A retro green-screen terminal with a text adventure inside |
| 24 | Gingerbread Gait | Gingerbread creatures evolve to walk |
| 25 | The Grand Tree | The finale |

</details>

## Credits
All the code, art, sounds and music are original. The carols in the music days are traditional and in the public domain. Libraries used: [Three.js](https://threejs.org) (MIT), [MediaPipe Tasks Vision](https://developers.google.com/mediapipe) (Apache 2.0), and the [VT323](https://fonts.google.com/specimen/VT323) font (SIL Open Font License), all loaded from public CDNs.
