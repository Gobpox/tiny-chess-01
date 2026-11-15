# tiny-chess-01 entry

A chess engine in at most 4,096 bytes of Python (`main.py`, packed by
`makefun compress` from the readable source kept beside it).

Design: 0x88 board, negamax alpha-beta with a transposition table,
quiescence search, null-move pruning, MVV-LVA move ordering, and a
tapered material + piece-square evaluation. The root avoids repeating
positions already seen in the game. The search budget is a fixed node
count, never a clock, so every replay plays the same moves.

It plays each game through the env at `MAKEFUN_ENV_URL`: POST /game
serves the game in play, POST /move plays a move.
