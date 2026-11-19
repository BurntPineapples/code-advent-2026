# Day 20 · A Million Snowflakes

A quiet street at night under a single lamp, and one million snowflakes falling through its light. The near ones are big enough to show their six-armed crystal shape. Swipe to make the wind blow, click for a gust, or try three million.

## Run it
Open `index.html` in a browser with WebGL 2 (any recent Chrome, Edge, Firefox or Safari).

- **Swipe the mouse sideways** to start a breeze in that direction. It slowly dies away.
- **Move the cursor** through the snow and the flakes part around it. **Click** for a gust.
- **10k / 100k / 300k / 1 million / 3 million** sets how many flakes fall. The frame rate shows at the bottom. If your graphics card can't keep up, it steps down by itself.

## How the magic works
There's no list of snowflakes anywhere: no array, no buffer, no simulation. The GPU is told "draw a million points", and the **vertex shader** works out where flake number *N* is from just two things, its index (`gl_VertexID`) and the current time. A fast **integer hash** turns the index into four random-looking numbers that stay the same frame to frame: horizontal position, start height, depth and fall speed. Height is `start − speed × time`, wrapped around the screen, and dividing everything by depth gives free **parallax**, so far flakes drift slowly and near ones rush past. Wind, the cursor's push and a gentle sway are all formulas added on top. The lamp's light is a cone test in the same shader: flakes inside the cone, at roughly the lamp's depth, turn warm and bright, and that's what makes snow "appear" in a street light. Points are blended additively, and the **fragment shader** draws large flakes as six-armed stars from polar coordinates (`|cos(3θ)|` raised to a high power makes the arms).
