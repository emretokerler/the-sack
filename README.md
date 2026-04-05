# The Knack

An interactive web app for learning the **0/1 Knapsack Problem** through Dynamic Programming visualization and a physics-based packing game.

**[Try it live](https://emretokerler.github.io/the-knack/)**

## What is this?

The Knack has two modes:

### Solution (DP Analysis)
- Generates a random dataset of items with values and weights
- Computes the full **Dynamic Programming state transition table** `M[i][w]`
- Highlights the **optimal value** and traces the **backtracking path** showing exactly which items to pick
- Hover over any DP table cell to see the pick-vs-skip math behind that sub-problem

### Play The Knack (Game)
- Select items manually and try to maximize value without exceeding the weight limit
- Watch items physically drop into a bag via **Matter.js** 2D physics
- Compare your selection against the DP-optimal solution
- Overload the bag and the UI fights back with warnings and shake animations

## Features

- **Zero dependencies to install** - single HTML file, just open it
- **Bilingual** - full English/Turkish toggle (EN/TR)
- **Configurable** - adjust knapsack capacity (5-20) and item count (3-8)
- **Shuffle** - randomize item values/weights while keeping your settings
- **Glassmorphism UI** with custom SVG loot icons (Gold, Diamond, Crown, Skull, etc.)

## Usage

Open `index.html` in any modern browser. That's it.

Or serve it locally:

```bash
# Python
python3 -m http.server 8000

# Node
npx serve .
```

## Tech Stack

| Tech | Role |
|------|------|
| HTML5 / Vanilla JS | Core app logic, no build step |
| Tailwind CSS (CDN) | Styling |
| Matter.js | 2D physics engine for the bag simulation |

## Algorithm

The classic 0/1 Knapsack via bottom-up DP:

```
M[i][w] = max(
    M[i-1][w],                          // skip item i
    items[i].value + M[i-1][w - items[i].weight]  // pick item i (if it fits)
)
```

Time complexity: `O(n * W)` where `n` = item count, `W` = capacity.

## License

[MIT](LICENSE)
