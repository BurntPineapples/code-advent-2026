# Day 14 · Reindeer Flight School

250 young reindeer, each with a randomly wired brain, try to fly between chimneys and icicles. Almost all of them crash at first. The best ones become the parents of the next generation, and within a few generations the herd flies the whole course. Then you can race the champion.

## Run it
Open `index.html` in any browser. Training starts by itself.

- **1× / 5× / 30× / Max** fast-forward the evolution.
- The panel at the bottom left shows **the leading reindeer's brain thinking, live**: five senses on the left, eight hidden neurons, and one decision, "FLAP!" or "glide". Blue links push towards flapping and orange ones push against it, with thickness showing strength.
- The chart shows the **best** (gold) and **average** (blue) chimneys passed per generation. The best learns fast, while the average shows the whole herd catching up.
- **🦌 Race the champion**: you (with the green scarf) against the best brain evolved so far, on a brand-new course. **Space** or **tap** to flap.

## How the magic works
This is **neuroevolution**: training a neural network with no teacher, no gradients and no examples, just survival of the fittest. Each reindeer's brain is a tiny network (5 inputs → 8 tanh neurons → 1 sigmoid output, 57 weights in total). It sees its height, vertical speed, distance to the next obstacle, and how far the top and bottom of the gap are. Fitness is simply how far it flew, plus a bonus per chimney. When everyone has crashed, the five best are copied unchanged ("elitism"). Everyone else is a child of two parents picked by tournament from the top 20%: each weight is copied from one parent or the other, and 12% of weights get random Gaussian noise. The noise shrinks over the generations, so early generations explore and later ones fine-tune. Every reindeer in a generation flies the same course, so the comparison is fair, and the course changes each generation, so they can't just memorise it. The gap narrows the further they fly, and the 100th chimney is the finish line.
