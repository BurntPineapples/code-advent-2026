# Day 23 · SLEIGH-OS

A glowing green-screen terminal from the North Pole's 1980s mainframe. It boots up, logs you in, and gives you a shell to poke around in. There are files to read, eye candy to run, and a whole text adventure hidden inside. Something has gone missing tonight, and the clues are in the file system.

## Run it
Open `index.html` in any browser and start typing. (The retro font loads from Google Fonts. Offline, it falls back to Courier.)

Good first commands: `help`, `ls`, `cat readme.txt`, `play`, `tree`, `snow`, `sleigh`, `fortune`, `say hello`, `color amber`.
↑/↓ walk through your command history, **Tab** completes names, and any key skips slow printing.

**Spoiler-free hint:** the adventure and the terminal talk to each other. If you get stuck in the game, `quit` (your progress is saved), look around the files, then `play` again. Win the game and you'll learn how to open `/secret/vault.txt`.

## How the magic works
Everything is plain HTML, CSS and JavaScript, and the "old CRT" look is pure CSS. A repeating gradient draws the **scanlines**. A radial gradient darkens the corners like curved glass. Two stacked `text-shadow`s make the phosphor **glow**. A stepped animation adds a faint **flicker**. The file system is just a nested JavaScript object, so `cd ..` and `cat ~/todo.txt` are a few lines of path resolution. The adventure is a classic two-word **parser**: it strips filler words ("the", "to", "at"), takes the first word as the verb, and matches the rest against known nouns. The world is a little table of rooms with exits, items with locations, and a handful of flags, which is how text adventures have worked since the 1970s. Output goes through a queue that prints one line at a time with a delay, to fake an old serial connection, and the key clicks are tiny bursts of filtered noise.
