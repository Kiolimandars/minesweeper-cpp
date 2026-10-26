# Minesweeper (C++ Console)

A classic Minesweeper game for the Windows console, written in object-oriented C++ (2021).

## Features

- **Three difficulty levels:** Easy (8×8, 8 mines), Medium (12×12, 30 mines), Hard (18×18, 140 mines)
- **Three actions per turn:** reveal a tile, toggle a flag, or mark a tile with a question mark
- **Auto-reveal:** opening a tile with no neighbouring mines automatically uncovers the surrounding area
- **Player profiles:** enter your name at startup; your wins and losses are saved to `Scores.txt` and loaded again next time
- **Coloured console output** for victories, defeats and player stats

## How to play

1. Enter your name, then choose a difficulty (1, 2 or 3).
2. Each turn, pick an action: `p` reveal, `f` flag / unflag, `m` question mark, `q` quit.
3. Enter the row and column of the tile.
4. Revealing a mine ends the game. Once you have placed as many flags as there are mines, the game checks your flags: if every one is on a mine, you win.

## Build and run

The game uses `windows.h` for console colours, so it runs on Windows. With MinGW:

```bash
g++ -std=c++11 -o minesweeper.exe main.cpp demineurboard.cpp Tile.cpp difficulty.cpp Player.cpp
minesweeper.exe
```

Run it from the repository folder so it can find `Scores.txt`. Any C++11 IDE on Windows (Code::Blocks, Visual Studio) works too.

## Project structure

| File | Responsibility |
|---|---|
| `main.cpp` | Game loop, player input, win/loss handling |
| `demineurboard.cpp` | Board creation, random mine placement, display, auto-reveal (*démineur* is French for Minesweeper) |
| `Tile.cpp` | State of a single tile: hidden, revealed, flagged, question mark, neighbouring-mine count |
| `difficulty.cpp` | Difficulty presets and level selection |
| `Player.cpp` | Player name, wins and losses |
| `headers/` | Class declarations, plus reading and writing the scores file |

`DemineurBoard` inherits from `Difficulty` and `Tile`, and the board is a 2D grid of `Tile` objects.
