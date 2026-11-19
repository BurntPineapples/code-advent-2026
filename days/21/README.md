# Day 21 · Santa's Route

A snowy village with 60 houses and one sleigh. What order should Santa visit them in? Draw your best route by hand, then watch an AI start from a hopeless tangle and smooth it out into a clean loop, live. When you're done, press **Deliver!** and every window lights up as the presents land.

## Run it
Open `index.html` in any browser.

- **✏ Draw your own**: start at the workshop ★ and click (or drag across) houses in order. Right-click or Backspace undoes a step.
- **▶ Let the AI plan it**: watch the search. The chart shows the route length dropping as the "temperature" cools.
- **🛷 Deliver!** flies whichever route is shorter, yours or the AI's.
- Try **250 houses**. Nobody draws that one by hand.

## How the magic works
This is the **travelling salesman problem**. 60 houses have about 10⁸⁰ possible orders, roughly one for every atom in the universe, so nothing can check them all. The AI uses **simulated annealing**. Start with a random route. Pick two roads, cut them, and reconnect the four loose ends the other way round, which flips the stretch in between (a **2-opt move**). If the route gets shorter, keep the change. If it gets longer, keep it anyway with probability `e^(−Δ/T)`, where `T` is a "temperature" that slowly drops, like metal cooling in a forge. While it's hot the route can climb out of bad shapes. As it cools it settles into a good one. A final greedy 2-opt pass irons out the last kinks. The "elf's plan" is the obvious strategy, always fly to the nearest house you haven't visited yet, and annealing usually beats it by 15–25%.
