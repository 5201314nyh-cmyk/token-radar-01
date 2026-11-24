# Token Radar — Pre-Token Protocol Radar

[![make.fun · token-radar-01](https://make.fun/badge/token-radar-01.svg)](https://make.fun/bounty/token-radar-01?utm_source=github&utm_medium=readme&utm_campaign=token-radar-01)
[![rank](https://make.fun/badge/token-radar-01/5201314nyh-cmyk/token-radar-01/rank.svg)](https://make.fun/bounty/token-radar-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=token-radar-01)
[![reward](https://make.fun/badge/token-radar-01/5201314nyh-cmyk/token-radar-01/reward.svg)](https://make.fun/bounty/token-radar-01?utm_source=github&utm_medium=readme&utm_campaign=token-radar-01)

A dashboard that reads a sealed snapshot of every protocol DefiLlama tracks, works out which ones have no token yet (and are not a wrapped or staked product of one that trades), and ranks them by what their launch would be worth — so you can see the next token launches before they happen.

Built for the [token-radar-01 bounty on make.fun](https://make.fun/bounty/token-radar-01).

## What it does

- **Board:** 198 ranked rows — all 40 watchlist protocols plus 158 early protocols the watchlist leaves out, including the biggest pre-token names by TVL.
- **Model (radar-2):** instead of a flat multiple, each category's implied-value multiple is the median FDV/TVL of that category's live-token protocols in the snapshot itself, shrunk toward the market-wide median and clamped to [0.02, 1.5]. Implied value = TVL × category multiple × growth (7d change) × maturity (age since listing).
- **Detail view:** every row recomputes its score and shows why it ranks where it does, plus a 7-step farm plan with cost and time.
- **Live set-aside:** 24 live-token protocols are shown separately with their market caps, so the pre-token board stays clean.

## Run it

```bash
MAKEFUN_OUTPUT_DIR=out node main.ts --input <snapshot.json>
```

Node 22. Writes `board.json`, `data.js`, `dashboard/` and `screenshots/` into the output dir, plus `dossier.json`. Deterministic: two runs produce byte-identical output.

## Files

- `main.ts` — entrypoint: reads the snapshot, writes the board, dashboard and dossier.
- `lib/model.ts` — the radar-2 scoring model.
- `vendor/makefun-board.ts` — vendored kit library (byte-for-byte from the kit).
- `dashboard/` — the radar dashboard (index.html, app.css, app.js).
- `screenshots/` — board, detail and filtered views (1440×900).

## Referral

Made with [make.fun](https://make.fun/?ref=75k23xv8) — referral code `75k23xv8`.
