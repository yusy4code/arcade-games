# 🕹️ Kids Arcade Games

A collection of browser-based mini-games built with plain HTML, CSS, and JavaScript. No frameworks, no build tools — just open a file and play.

## Games

| Game | File | Players |
|------|------|---------|
| 🐍 Snake | `snake.html` | 1 |
| ⭕ Tic Tac Toe | `tic-tac-toe.html` | 2 |
| 🧱 Breakout | `breakout.html` | 1 |
| 🔢 Sudoku | `sudoku.html` | 1 |

## Getting Started

No installation needed. Just open `index.html` in any modern browser.

```
basic-games/
├── index.html        ← Start here
├── snake.html
├── tic-tac-toe.html
├── breakout.html
├── sudoku.html
├── favicon.svg
├── CLAUDE.md
└── README.md
```

## Features

- **Player profiles** — Enter your name on the home screen; scores are saved per player using `localStorage`
- **Score tracking** — Best scores, wins, levels, and completion times are stored and displayed on the home screen
- **Mobile friendly** — Responsive layouts, touch controls, and on-screen D-pad for Snake
- **Shared design** — Consistent dark theme across all games

## Controls

### Snake
| Device | Control |
|--------|---------|
| Keyboard | Arrow keys or WASD |
| Mobile | On-screen D-pad |

### Breakout
| Device | Control |
|--------|---------|
| Keyboard | Arrow keys (← →) |
| Mouse | Move over canvas |
| Mobile | Touch and drag |

### Tic Tac Toe
Click or tap a cell to place your mark. Player X always goes first.

### Sudoku
- Click/tap a cell, then tap a number or use the on-screen numpad
- Keyboard: type a number, `Backspace` to erase, arrow keys to navigate
- **Check** — highlights errors and correct cells
- **Solve** — reveals the solution
- **New Game** — returns to the setup screen

## Sudoku Options

| Setting | Options |
|---------|---------|
| Grid size | 4×4 · 6×6 · 9×9 |
| Difficulty | Easy · Medium · Hard |

## Score Storage

All scores are saved in `localStorage` under the key `arcade_scores`, keyed by username:

```json
{
  "Alice": {
    "snake":    { "best": 12, "bestLevel": 3, "gamesPlayed": 7 },
    "breakout": { "best": 40, "bestLevel": 2, "gamesPlayed": 4 },
    "ttt":      { "wins": 5, "draws": 2, "losses": 1, "gamesPlayed": 8 },
    "sudoku":   { "completed": 3, "bestTime": 142, "gamesPlayed": 5 }
  }
}
```

## Browser Support

Works in any modern browser (Chrome, Firefox, Safari, Edge). No internet connection required after the files are downloaded.
