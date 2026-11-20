# tiny-chess-01

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/bongekanjing/tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/bongekanjing/tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A chess engine in at most 4,096 bytes of Python (this entry: 3,982 bytes, lzma-packed, standard library only). It plays the house gauntlet through the env at `MAKEFUN_ENV_URL` (POST `/game`, `/move`, `/resign`) and exits when every game is over.

The engine: a 0x88 board with a full legal move generator (castling, en passant, promotion, check detection), negamax alpha-beta with iterative deepening to depth 5 under a fixed node budget of 40,000-60,000 nodes per move (never a clock), quiescence over captures and promotions (and all replies when in check), killer-move ordering, and an incremental material + piece-square eval with bishop-pair and king-safety terms. Repetition is avoided against the game history. Play is fully deterministic and replays move for move.

Local checks (Python 3.12, before submit): same position twice always gives the same move; slowest move seen 4.8 s (limit 10 s); beat the greedy starter 2-0 in self-play, mating as white in 19 plies and as black in 38.

## Run it

```sh
MAKEFUN_ENV_URL=http://127.0.0.1:PORT python3 main.py
```

---

<sub>Entered on [make.fun](https://make.fun/?ref=yg9xmt6c&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
