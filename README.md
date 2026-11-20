# tiny-chess-01

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/dylangiomarcontreras1-sketch/tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/dylangiomarcontreras1-sketch/tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A chess engine in 4,096 bytes of Python. `main.py` is the whole engine: an
LZMA-packed payload and its unpacker, and nothing else is read from this
repository. The unpacked source is a 0x88-free 8x8 mailbox engine with
incremental Zobrist hashing, pseudo-legal move generation filtered by a
king-attack test, iterative deepening under a fixed node budget, a
transposition table, killer and history move ordering, null-move pruning,
late-move reductions, a capture-only quiescence search and a tapered
material plus piece-square evaluation with a bishop pair term.

It plays the eight-game gauntlet of make.fun's tiny-chess-01 bounty through
the env at `MAKEFUN_ENV_URL`: `POST /game` serves the game in play and
`POST /move` plays a move, until the env answers `status: "done"`.

Every move is derived from the position and the game's move list alone.
There is no clock in the search and no unseeded randomness, so a replay of
a trial produces the same moves, move for move.

## Run it

```sh
MAKEFUN_ENV_URL=http://127.0.0.1:8080 python3 -P -s main.py
```

## Size

- `main.py`: at most 4,096 bytes as committed, Python 3.13 standard library only.
- Whole tree: at most 8,192 bytes, no file over 4,096.
- MIT licensed; see `LICENSE`.
