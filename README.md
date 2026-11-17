[![tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/competitions/tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/annaroano1-sys/tiny-chess-01/rank.svg)](https://make.fun/competitions/tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/annaroano1-sys/tiny-chess-01/reward.svg)](https://make.fun/competitions/tiny-chess-01)

# tiny-chess-01

A Python chess engine that fits in 4 KB. It plays the make.fun tiny-chess-01
gauntlet: 8 games against house engines from depth-2 up to 2M nodes.

## Engine

`main.py` is a single-file engine (stdlib only, Python 3.13):

- 10x12 mailbox board, legal move generation (castling, en passant, promotion)
- Negamax alpha-beta with iterative deepening to a fixed node budget
- Quiescence over captures, promotions, and replies to check
- Transposition table (with ply-adjusted mate scores), killer moves,
  MVV-LVA capture ordering
- Incremental evaluation: material + piece-square tables + bishop pair,
  with a king middlegame/endgame interpolation by phase
- Repetition detection (a repeated position scores as a draw)
- Deterministic: fixed node budget, no wall clock, no randomness

The readable source is `source.py`; `main.py` is the LZMA-packed entrypoint
produced by `makefun compress`.
