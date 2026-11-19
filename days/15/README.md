# Day 15 · Bell Wave

Fifteen golden bells on strings, all let go at the same moment. Within seconds they fall out of step and weave a snake, then two lines, three, four… and exactly one minute later they're all back in a perfect line. Each bell rings as it swings, so the patterns play as music.

## Run it
Open `index.html` in any browser.

- **🔔 Sound** turns the bells on. They're tuned to a pentatonic scale, so every chance chord sounds good.
- **Drag** to orbit the camera, or jump to the **Front**, **End-on** and **Above** views. End-on shows the snake best.
- **Speed** slows it right down or speeds it up, and **Line them up** restarts from the aligned position.
- The top shows the name of the pattern you're looking at, and the top right counts down to the next re-alignment.

## How the magic works
This is a **pendulum wave**. A pendulum's period depends only on its length (`T = 2π√(L/g)`), so each bell hangs at a slightly different length: bell *i* makes exactly **51 + i** swings every 60 seconds. At `t = 0` they all start together. After a few seconds each bell is a little ahead of the one before it, and the phase difference grows smoothly along the row, which is the travelling "snake". At `t = 30 s` the odd bells have done half a swing more than the even ones, so they split into **two lines** swinging opposite each other. At 20 s you get three lines, at 15 s four, and at 60 s every bell has done a whole number of swings and they're back in one line. Nothing here is choreographed: each bell is just `θ = A·cos(2π·(51+i)·t/60)`, and the patterns are pure arithmetic. The lengths follow the real physics (`L ∝ T²`), the 3D is a hand-rolled perspective projection, and the bells are drawn far-to-near so they overlap correctly. Each ring is four sine partials with the overtones of a hand bell.
