# The Sack

An interactive web app for learning the **0/1 Knapsack Problem** through Dynamic Programming visualization and a physics-based packing game.

**[Try it live](https://emretokerler.github.io/the-knack/)**

## What is this?

The Sack has three tabs:

### Problem
- Full explanation of the 0/1 Knapsack Problem
- Why greedy fails (with a concrete counterexample)
- DP recurrence relation and backtracking logic
- Time/space complexity

### Solution (DP Analysis)
- Generates a random dataset of items with values and weights
- Computes the full **Dynamic Programming state transition table** `M[i][w]`
- Highlights the **optimal value** and traces the **backtracking path** showing exactly which items to take
- Hover over any DP table cell to see the step-by-step math behind that sub-problem

### Play The Sack (Game)
- 10-level progression from easy (3 items) to hard (8 items)
- Select items manually and try to maximize value without exceeding the weight limit
- Watch items physically drop into a bag via **Matter.js** 2D physics with shape-matched polygon colliders
- Star rating system (1-3 stars), streak tracking, and difficulty scaling
- Compare your selection against the DP-optimal solution
- Optional countdown timer for extra pressure

## Features

- **Zero dependencies to install** - single HTML file, just open it
- **Bilingual** - full English/Turkish toggle (EN/TR)
- **Museum Heist theme** - detailed SVG artwork (Painting, Sculpture, Diamond, Crown, Gold Mask, Chalice, Jade Idol, Ming Vase)
- **Difficulty levels** - Easy, Medium, Hard with smart puzzle generation ensuring greedy != optimal on hard
- **Configurable** - adjust knapsack capacity (5-20), item count (3-8), timer, and difficulty

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
| poly-decomp | Convex decomposition for polygon colliders |

## Algorithm

The classic 0/1 Knapsack via bottom-up DP:

```
M[i][w] = max(
    M[i-1][w],                          // skip item i
    items[i].value + M[i-1][w - items[i].weight]  // take item i (if it fits)
)
```

Time complexity: `O(n * W)` where `n` = item count, `W` = capacity.

## License

[MIT](LICENSE)
