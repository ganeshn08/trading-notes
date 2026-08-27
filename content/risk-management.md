---
title: Risk Management
tags:
  - process
  - risk
---

The only part of this notebook that reliably decides outcomes. Everything in
[[technical-analysis|technical analysis]] adjusts your edge at the margin; this
determines whether you're still trading in a year.

## The asymmetry that governs everything

Losses compound against you harder than gains compound for you:

| Drawdown | Gain needed to recover |
|---|---|
| 10% | 11% |
| 25% | 33% |
| 50% | **100%** |
| 75% | **300%** |

Down 50%, a merely good year doesn't get you back. This is arithmetic, not
psychology, and it's why survival dominates optimisation.

## Expectancy

$$E = (W \times \overline{\text{win}}) - (L \times \overline{\text{loss}})$$

Where $W$ and $L$ are win and loss rates. Two consequences people resist:

- **A 40% win rate is fine** at 3:1 reward-to-risk
- **A 70% win rate loses money** if the losers are large enough

Win rate on its own is not information. Systems are sold on it precisely because
it's the number that feels best and means least.

> [!tip] Define the loss before the entry
> The exit price on the losing side is the only variable you fully control at the
> moment you enter. Decide it first, then compute size from it — see
> [[position-sizing|position sizing]]. Deciding entry first and stop second is
> backwards, and it's how a 1% risk quietly becomes 6%.

## Rules worth keeping

- Fixed fractional risk per position, never a fixed lot
- A daily loss limit that ends the session, not a "one more trade"
- Correlated positions are **one** position — three bank stocks is a bank bet
- Nothing gets capital until it survives [[backtesting]] with costs included

## What this doesn't fix

Sizing correctly around a negative-expectancy system just loses money more slowly.
Risk management buys time for an edge to work; it doesn't create one.
