# Day 12 · Hot Cocoa

A steaming mug of hot chocolate, seen from above, with real fluid physics. Stir it and the cream swirls into spirals and eddies, marshmallows ride the currents, and the steam drifts off the top.

## Run it
Open `index.html` in any browser.

- **🥄 Stir** (key 1): drag through the cocoa.
- **🥛 Pour cream** (2): hold and drag to pour.
- **✨ Cinnamon** (3): sprinkle as you drag.
- **☁️ Marshmallow** (4): click to drop one in with a little splash. They slowly melt, leaving white trails.
- **☕ Fresh cup** (5) starts over.

## How the magic works
The cocoa is a 128×128 grid running Jos Stam's **"Stable Fluids"** algorithm (1999), the same method behind a lot of real-time smoke and water in games. Every frame does three things. First, **advection**: for each cell, trace the flow *backwards* in time and copy whatever was there, which moves the velocity and the cream along the current and never blows up however hard you stir. Second, **projection**: solve for a pressure field (22 Jacobi relaxation passes) and subtract its gradient, so the flow is incompressible and liquid can't pile up or vanish. That's what turns a straight stir into curling vortices. Third, **vorticity confinement** measures the spin at each cell and gives it a nudge, putting back the fine swirls that numerical blur would otherwise smooth away. Marshmallows sample the velocity under them and float along, the mug's wall is a circular mask where velocity is forced to zero, and the shading comes from the slope of the cream layer.
