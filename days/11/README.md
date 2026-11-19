# Day 11 · Murmuration

Thousands of starlings swirl over a snowy village at sunset, folding into one shape-shifting cloud. Every so often a hawk dives through, and a wave of panic ripples across the flock.

## Run it
Open `index.html` in any browser.

- **Move your mouse** into the sky and you become the hawk. Watch the flock tear open around you and heal behind you.
- **Birds** sets the flock size, from 500 to 4,000.
- **Togetherness** (cohesion) and **Follow-the-neighbour** (alignment) change the flock's personality: try either one at 0.
- Untick **Hawk attacks** for a calm evening.

## How the magic works
Nobody is in charge of the flock. Each bird follows three local rules from Craig Reynolds' 1986 **"boids"** model: don't crowd your neighbours (*separation*), match their heading (*alignment*) and drift towards their centre (*cohesion*). The twist that makes it look like real starlings comes from a 2008 field study (Ballerini et al.), which found that each starling reacts to its **~7 nearest neighbours**, however far away they are, not to everyone within some distance. So each bird here stops counting after 7. That's why a disturbance travels across the flock as a visible wave instead of instantly. The flock lives in 3D, with a slow orbiting camera, and birds are drawn as short dark strokes in three depth layers. Where the cloud folds towards you, the strokes stack up and the flock darkens. That darkening is the eerie "breathing" of real murmurations. A 3D spatial hash grid keeps the neighbour search fast enough for thousands of birds in plain JavaScript.
