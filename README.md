# Trading Notes

A digital garden for market notes — evergreen writing on price action, risk and
process, published as a static site.

Notes are linked rather than dated. Concepts reference each other directly, so
the site builds backlinks, a tag index and a navigable graph from the writing
itself rather than from a folder structure.

## Structure

```
content/
├── index.md                  entry point
├── technical-analysis.md     overview, links out to everything
├── market-structure.md       trend, ranges, break of structure
├── support-and-resistance.md levels, and why they decay
├── moving-averages.md        regime filters, not signals
├── rsi.md                    momentum, divergence, regime dependence
├── head-and-shoulders.md     pattern, stripped back to structure
├── risk-management.md        drawdown maths and expectancy
├── position-sizing.md        fixed fractional and volatility-normalised
├── backtesting.md            method, and the four ways it lies
└── journal/                  dated entries, kept unedited
```

Evergreen notes get rewritten as understanding changes. Journal entries don't —
they're snapshots of what was believed at the time, which is the only way to see
later how wrong it was.

## Running locally

Requires Node >= 22.

```bash
npm install
npx quartz build --serve
```

Serves at `http://localhost:8080`, rebuilding as `content/` changes.

To build the static site without serving:

```bash
npx quartz build
```

Output lands in `public/`.

## Built with

[Quartz v5](https://quartz.jzhao.xyz/) by [jackyzha0](https://github.com/jackyzha0),
MIT licensed — see `LICENSE.txt`.
