# Day 13 · The Carol Machine

A machine that writes brand-new Christmas carols, live, forever. It learned from five traditional carols, and you can watch it "think" about every note: what it remembers, which notes it's considering, and which song each idea was borrowed from.

## Run it
Open `index.html` in any browser and press **▶ Play**. Turn your sound on.

- **Memory: 1 / 2 / 3 notes** controls how much of the recent melody it looks at before choosing the next note.
- **New carol** starts a fresh song with a freshly made-up title.
- **Tempo** speeds it up or slows it down.
- Colours on the piano roll show which training carol each transition came from, and the **Originality** score shows how much of the tune is genuinely new.

## How the magic works
It's a **Markov chain**, one of the oldest ideas in generative AI (Markov himself used it on poetry in 1913). Training is just counting: for every point in every carol, note down "after these *k* notes, this note came next". To compose, look at the last *k* notes played, gather every continuation that ever followed them, and roll weighted dice. With a 1-note memory it knows only "what tends to follow an E", so it wanders (about 90% original, rather aimless). With 3 notes it has so little choice that it mostly quotes its training songs (about 15% original). Two notes is the sweet spot. If it reaches a combination it has never seen, it **backs off** to a shorter memory instead of getting stuck. Every so often it leans towards a long note on C, so phrases come to rest like real carols. A simple harmoniser picks C, F, G, Am or Dm chords that contain each melody note for the bass and pad, and a lookahead scheduler queues every note on the Web Audio clock, so the timing stays tight.

The training songs, Jingle Bells, Deck the Halls, We Wish You a Merry Christmas, Silent Night and Joy to the World, are all traditional and in the public domain.
