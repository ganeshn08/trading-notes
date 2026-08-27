---
title: Moving Averages
aliases:
  - MA
  - EMA
tags:
  - technical-analysis
  - indicator
---

The mean closing price over a lookback window. The simplest possible smoothing of
price, and still the most used.

## Simple vs exponential

$$\text{SMA}_n = \frac{1}{n}\sum_{i=0}^{n-1} P_{t-i}$$

$$\text{EMA}_t = \alpha P_t + (1-\alpha)\,\text{EMA}_{t-1}, \qquad \alpha = \frac{2}{n+1}$$

SMA weights every bar equally; EMA decays geometrically, so it turns sooner. The
choice matters less than people argue — the lookback dominates both.

## What they're actually for

**Not** signals. A moving average is a **regime filter**. Price above a rising
200-period average is a different environment from price below a falling one, and
that distinction changes which setups are worth taking at all.

> [!warning] Crossovers are a trap
> The golden cross / death cross is the most-published, least-useful signal in
> the field. It's two lagging averages agreeing about something price told you
> long ago. Every backtest I've run on crossovers alone gives a positive
> expectancy that vanishes once costs are included — see [[backtesting]].

## The lag problem

An $n$-period average lags price by roughly $n/2$ bars. That's not a flaw to be
engineered away; it's the definition. Smoothing *is* delay. Every "zero-lag"
variant buys responsiveness with false signals.

## Sensible use

- As a [[market-structure|structural]] filter: only take longs above the 200
- As a dynamic [[support-and-resistance|support level]] in an established trend
- As a trailing exit — mechanical, unemotional, gives back a fixed fraction

Pairs badly with [[rsi|RSI]], which is also derived from the same closes. Two
lagging transforms of one series is one signal wearing a disguise.
