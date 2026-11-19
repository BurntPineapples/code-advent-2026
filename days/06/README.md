# Day 6 · The Music Box

A wind-up music box with a punched paper strip. It comes loaded with four traditional carols, and you can punch your own tune and send it to someone as a link.

## Run it
Open `index.html` in any browser.

- **Play** (or **Space**) runs the motor, and **Speed** sets the tempo.
- **Drag the crank** round to pull the paper through by hand, as slow or as fast as you like.
- **Click the paper** to punch a hole, or to patch one closed.
- **Blank strip** gives you 64 empty columns. **Copy link** saves your tune into the URL, and anyone who opens the link gets the same strip.
- The songs are all traditional and public domain: Jingle Bells, Deck the Halls, We Wish You a Merry Christmas and Silent Night.

## How the magic works
The strip is just a grid: 15 rows (one per tine, a C-major scale from G3 to G5) by N columns. Melodies are typed as `note:beats` pairs and unrolled into columns, two per beat. Whenever the strip moves, from the motor or your crank, every column whose holes cross the comb line gets "plucked". The sound is synthesised with **additive synthesis**: a steel tine is mostly a pure sine with a 3 ms attack and a long exponential ring, plus a quiet octave and a short inharmonic overtone at about 5.9× the pitch. That overtone is the metallic "tink" that makes it sound like a music box rather than a flute. A homemade reverb (a convolver fed with two seconds of decaying noise) adds the wooden-box resonance. Share links pack each column's 15 holes into one base-36 number.
