# tiny-chess-01

A chess engine in 4,012 bytes of Python (standard library only).

`main.py` is a self-extracting lzma payload (explicitly allowed by the
rules): a two-line unpacker decompresses and execs the engine source.

The engine: 120-square mailbox board, incremental material + piece-square
evaluation with a tapered king, Zobrist hashing, negamax alpha-beta with
PVS, quiescence search, transposition table, MVV-LVA / killer / history
move ordering, check extensions, null-move pruning, late-move reductions,
and repetition-aware scoring (game history + search path). It searches a
fixed budget of 45,000 nodes per move — fully deterministic, no clock,
no randomness at play time.

It talks to the environment at `MAKEFUN_ENV_URL` (`POST /game`,
`POST /move`, UCI moves), exactly as the starter does.
