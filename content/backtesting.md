---
title: Backtesting
tags:
  - process
  - research
---

Running a rule over history to estimate whether it has an edge. Mostly an
exercise in not fooling yourself.

## Minimum viable test

```python
import pandas as pd

def backtest(px: pd.Series, fast: int = 20, slow: int = 100, cost_bps: float = 10):
    """Long when fast MA > slow MA. Deliberately naive — the point is the costs."""
    fast_ma = px.rolling(fast).mean()
    slow_ma = px.rolling(slow).mean()

    # shift(1): decide on today's close, trade tomorrow. Without this you are
    # trading on information you did not have. This single line is the most
    # common source of a backtest that "works".
    signal = (fast_ma > slow_ma).astype(int).shift(1).fillna(0)

    returns = px.pct_change().fillna(0)
    turnover = signal.diff().abs().fillna(0)
    costs = turnover * (cost_bps / 10_000)

    strategy = signal * returns - costs
    equity = (1 + strategy).cumprod()

    return pd.DataFrame({"equity": equity, "returns": strategy})
```

## The four ways it lies

**Lookahead bias.** Using data unavailable at decision time. The `.shift(1)` above
is the guard. Subtler versions hide in resampling and in restated fundamentals.

**Survivorship bias.** Testing on today's index constituents means testing on the
companies that survived. Delisted names are where the losses were.

**Overfitting.** Enough parameters will fit any history. A strategy with six
tunables and a beautiful curve has learned the noise. Fewer parameters, wider
plateaus in the parameter surface, out-of-sample validation.

**Costs.** Spread, slippage, impact, taxes, borrow. Most published edges are
smaller than their costs — see the crossover results in
[[moving-averages|moving averages]].

> [!warning] The one that gets everyone
> Testing many variants and reporting the best is not research, it's selection.
> Twenty random strategies produce one that looks significant at p<0.05 by
> construction. Decide the rule first, then test it once.

## What a passing result means

That the rule wasn't obviously broken on that data. Nothing more. It doesn't
transfer to a different regime, and it says nothing about whether you can execute
it — that's [[risk-management|risk management]] and
[[position-sizing|position sizing]], neither of which a backtest models honestly.

Patterns like [[head-and-shoulders|head and shoulders]] are hard to test at all,
because specifying them in code is most of the work — and the version you can
specify is rarely the version you meant.
