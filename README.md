# tiny-chess-01

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/bongekanjing/tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/bongekanjing/tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A chess engine in at most 4,096 bytes of Python (this entry: 3,305 bytes, lzma-packed, standard library only). It plays the house gauntlet through the env at `MAKEFUN_ENV_URL` (POST `/game`, `/move`, `/resign`) and exits when every game is over.

The engine: a 0x88 board with a full legal move generator (castling, en passant, promotion, check detection), negamax alpha-beta with a transposition table, PVS, killer ordering and null-move pruning, quiescence (captures and promotions; all evasions in check), and an incremental material + piece-square eval. Search is iterative deepening to a fixed node budget of 100,000 nodes per move (never a clock), so play is fully deterministic and replays move for move. Repetition is detected against the search path and the game history.

Local practice-trial results (compressed final version): trial 0: 4-1-1 (~1545 Elo), trial 1: 4-0-2 (~1451 Elo), trial 2: 1-1-4 (~997 Elo).

## Run it

```sh
MAKEFUN_ENV_URL=http://127.0.0.1:PORT python3 main.py
```

---

<sub>Entered on [make.fun](https://make.fun/?ref=204hjvsp&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
