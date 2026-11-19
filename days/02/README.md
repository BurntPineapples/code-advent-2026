# Day 2 · Fairy Lights

Strings of glowing bulbs hang against a dark brick wall, and every one of them is a physical object. Grab a wire and fling it, cut it, unhook it, or hang your own.

## Run it
Open `index.html` in any browser.

- **Drag a wire** to swing it. Let go mid-swing and it keeps the momentum. Drag a **hook** to re-hang it.
- **Drag across empty space** to string up a new set of lights.
- **Double-click** a wire to snip it, or a hook to unhook it.
- **Swipe the cursor** quickly through the lights to knock them about.
- **Keys 1–5** switch between Steady, Chase, Twinkle, Rainbow and Breathe.

## How the magic works
Each string is a chain of points simulated with **Verlet integration**: instead of storing velocity, every point remembers where it was last frame, and its velocity is just "now minus then". Each frame, gravity nudges every point, then a dozen passes of "stick constraints" pull each neighbouring pair back to its rest length. Repeating that quickly settles the chain into a natural droop (a catenary) with no physics formulas at all. Throwing works for free, because a dragged point's last position is wherever your mouse just was. The glow is additive blending: each bulb paints a soft radial gradient in `lighter` mode over a darkened brick texture, so overlapping colours mix and the wall seems to be lit by the bulbs.
