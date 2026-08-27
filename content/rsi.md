---
title: RSI
aliases:
  - Relative Strength Index
tags:
  - technical-analysis
  - indicator
  - momentum
---

Wilder's momentum oscillator. Bounded 0–100, measuring the ratio of average gains
to average losses over a lookback.

$$RSI = 100 - \frac{100}{1 + RS}, \qquad RS = \frac{\overline{\text{gain}}_n}{\overline{\text{loss}}_n}$$

Default $n = 14$.

## The misreading everyone starts with

> RSI above 70 is overbought, sell it.

This loses money reliably, and the reason is structural. In a strong
[[market-structure|uptrend]] RSI *lives* above 70 — that's what a strong trend
looks like in this transform. Shorting overbought readings means systematically
fading the strongest instruments in the market.

**Overbought means the trend is strong, not that it's ending.** The oscillator
has no way to distinguish exhaustion from strength; both produce a high reading.

## What it's actually good for

**Divergence.** Price makes a higher high, RSI makes a lower high — momentum is
decaying while price still advances. That's information price alone doesn't
present clearly.

Caveats worth stating plainly:

- Divergence can persist for a very long time before resolving
- It's only worth acting on at a meaningful [[support-and-resistance|level]]
- It resolves as often by going sideways as by reversing

> [!note] Range-bound is a different regime
> Mean-reversion on RSI extremes does work in a genuine range — the same reading
> that's a trap in a trend. The indicator didn't change; the regime did. Use
> [[moving-averages|a moving average]] to decide which regime you're in before
> deciding how to read RSI at all.

Anything built on this needs [[backtesting]] before it gets capital, and sizing
per [[position-sizing|position sizing]] regardless of conviction.
