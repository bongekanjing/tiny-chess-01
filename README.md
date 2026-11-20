# tiny-chess-01

A chess engine in at most 4,096 bytes of Python. It plays the house
gauntlet through the env at `MAKEFUN_ENV_URL` (POST `/game`, `/move`,
`/resign`) and exits when every game is over.

## Engine

`main.py` is the whole engine (4,088 bytes, lzma+base85 compressed
payload, standard library only): a 0x88 board with a full legal move
generator (castling, en passant, promotion, check detection), negamax
alpha-beta with a transposition table, PVS, killer ordering and
null-move pruning, quiescence (captures and promotions; all evasions
in check), and an incremental material + piece-square eval. Search is
iterative deepening to a fixed node budget of 100,000 nodes per move
(never a clock), so play is fully deterministic and replays move for
move. Repetition is detected against the search path and the game
history.

## Run

    MAKEFUN_ENV_URL=http://127.0.0.1:PORT python3 main.py

## Referral

Our make.fun referral code: `204hjvsp` — https://make.fun/r/204hjvsp
