# Kids Arcade Games

A collection of browser-based games built with plain HTML, CSS, and JavaScript — no frameworks, no build tools.

## Project Structure

```
basic-games/
├── index.html          # Landing page — game picker + username + stats
├── snake.html          # Snake game
├── tic-tac-toe.html    # Tic Tac Toe (2-player)
├── breakout.html       # Breakout / brick-breaker
├── sudoku.html         # Sudoku (chooseable size & difficulty)
├── favicon.svg         # Shared SVG favicon (game controller)
└── CLAUDE.md
```

## Design System

All pages share the same dark theme:

| Token        | Value     | Usage                        |
|--------------|-----------|------------------------------|
| Background   | `#1a1a2e` | Page background              |
| Surface      | `#16213e` | Cards, canvas, panels        |
| Border       | `#0f3460` | Default borders              |
| Snake/teal   | `#4ecca3` | Snake game accent            |
| TicTacToe    | `#e94560` | TTT accent / error states    |
| Breakout     | `#f7b731` | Breakout accent              |
| Sudoku       | `#a29bfe` | Sudoku accent                |
| Font         | `Segoe UI`, sans-serif       |

## User & Score System

Scores are persisted in **`localStorage`** under two keys:

- `arcade_username` — the current player's name (string)
- `arcade_scores` — JSON object keyed by username:

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

Each game reads `arcade_username` from localStorage and writes into `arcade_scores` at the end of each game session.

## Game Notes

### Snake (`snake.html`)
- Controls: Arrow keys or WASD
- Canvas: 600 × 500, grid cell = 20px
- Levels up every 5 points; speed increases each level
- Score saved on game over

### Tic Tac Toe (`tic-tac-toe.html`)
- 2-player, same device
- X always goes first; session scores persist until page reload
- Wins tracked as X wins (player 1) for localStorage

### Breakout (`breakout.html`)
- Controls: Arrow keys or mouse movement
- 3 lives; losing a life resets ball/paddle only — bricks stay as-is
- Clears all bricks → next level (speed increases)
- Score saved on game over or when all lives lost

### Sudoku (`sudoku.html`)
- Grid sizes: 4×4, 6×6, 9×9
- Difficulties: Easy / Medium / Hard (controls number of pre-filled clues)
- Keyboard navigation with arrow keys; numpad or click to enter numbers
- Check, Solve, and New Game actions available
- Best completion time saved on win

## Adding a New Game

1. Create `<game-name>.html` following the existing page structure:
   - Same dark theme colors
   - `← Back to Home` link pointing to `index.html`
   - `<link rel="icon" type="image/svg+xml" href="favicon.svg">` in `<head>`
   - Score-saving block reading `arcade_username` from localStorage

2. Add a card to `index.html`:
   - New `.card.<game>` CSS class with a `--accent` color
   - `<div class="card-stat" id="stat-<game>">` for mini stats
   - Update `renderStats()` to populate that stat

3. Add the game's score key to the `arcade_scores` schema above.
