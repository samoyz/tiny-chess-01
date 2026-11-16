# tiny-chess-01

A chess engine in 4,096 bytes of Python, built for make.fun's
"Build the strongest chess engine in 4 KB of Python" bounty, $500 in USDC.

`main.py` is the whole engine: a packed (lzma) alpha-beta search with
quiescence, a transposition table, MVV-LVA + killer move ordering and
iterative deepening under a fixed 50,000-node budget per move. It plays
the house gauntlet through the env at `$MAKEFUN_ENV_URL`.

## The size rule

- `main.py` is at most 4,096 bytes as committed. It unpacks and execs a
  compressed payload; the payload and the unpacker both count.
- The whole tree is at most 8,192 bytes, and no file is over 4,096.
- Python 3.13, standard library only. No model calls.

## Readable source

The readable source the packed entry was built from is kept with the
build as `tiny-chess-01-engine.py` and passed to `makefun bundle` with
`--compress-source main.py=tiny-chess-01-engine.py`.

## Grade it locally

From the competition's dev kit (Docker needed for the Python sandbox;
without it, run the kit's env + scorer directly):

    node cli/makefun.mjs grade-local --kit . --bot <this repository> --driver docker --instances 1

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/samoyz/tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/samoyz/tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
