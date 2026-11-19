# Day 7 · The Neural Painter

A neural network that starts with random weights learns to paint a Christmas picture while you watch. It begins as a muddy smear and sharpens into the real thing over about 30 seconds. Paint on the original and it re-learns live.

## Run it
Open `index.html` in any browser. Training starts on its own.

- **Tree / Snowman / Bauble / Sweater** swap the picture. The Sweater is the hard one.
- **Paint** on the left picture with the colour swatches, and watch the network chase your brush strokes.
- **Fourier features: on/off** retrains without them, and you'll see why they matter.
- **Render at 4× size** asks the trained network for a 256×256 image, 16× more pixels than it ever saw.
- The right-hand panel shows what each of the 64 neurons in the second hidden layer responds to.

## How the magic works
The network is a function `f(x, y) → (r, g, b)`: two hidden layers of 64 ReLU neurons, about 6,000 weights, written from scratch in plain JavaScript with no libraries. Each training step it guesses the colour of 32 random pixels, measures the squared error, works out every weight's share of the blame with **backpropagation**, and nudges them all with the **Adam** optimiser, about 1,300 steps a second. It never stores the picture. The picture ends up *encoded in the weights*, which is why it can render at any resolution. The trick that makes it sharp is **random Fourier features**: before the network sees `(x, y)`, the position is turned into `sin` and `cos` waves along 32 random directions. Plain networks have a "spectral bias" toward smooth, blurry functions, and handing them ready-made waves lets them build fine detail out of the waves instead. (This is the same idea that powers NeRF-style 3D scene reconstruction.)
