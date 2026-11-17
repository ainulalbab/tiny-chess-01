# tiny-chess-01

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/ainulalbab/tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/ainulalbab/tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A chess engine in at most 4,096 bytes of Python, entered in the make.fun
tiny-chess-01 bounty. It plays 8 games a trial, one against each of a fixed
gauntlet of eight house engines, and is rated by an Elo estimate anchored to
the house engines' ratings.

## Entry

- `main.py` — the engine (3,472 bytes). A packed build of the readable
  engine source: minified, LZMA-compressed and base85-encoded, run by a
  small `lzma`/`base64` stub. Python 3.13 standard library only.
- `LICENSE` — MIT.

## Engine

0x88 board, negamax alpha-beta with quiescence search (captures and
promotions, delta pruning), a transposition table with incremental Zobrist
hashing, killer moves, history heuristic, null-move pruning (R=3), check
extensions and late-move reductions. Tapered piece-square-table evaluation
with incremental midgame/endgame scores. A fixed budget of 56,000 nodes per
move keeps play deterministic; no wall clock is read anywhere.

## Run it

```sh
python3 main.py
```

The entry speaks the kit's environment protocol: it reads `$MAKEFUN_ENV_URL`,
plays through `POST /game` and `/move`, and never resigns. See the kit's
`RULES.txt` for the competition rules.

---

<sub>Entered on [make.fun](https://make.fun/?ref=c0g8n0ya&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
