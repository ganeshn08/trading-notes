---
title: Position Sizing
tags:
  - process
  - risk
---

How much to buy. Downstream of [[risk-management|risk management]], and the place
where its rules become an actual number.

## Fixed fractional

Risk a constant fraction of equity per trade:

$$Q = \frac{E \times r}{|P_{\text{entry}} - P_{\text{stop}}|}$$

- $E$ — account equity
- $r$ — fraction risked, typically 0.005–0.02
- Denominator — the per-unit loss if the stop is hit

Worked example: ₹500,000 equity, 1% risk, entry ₹1,240, stop ₹1,198.

$$Q = \frac{500000 \times 0.01}{1240 - 1198} = \frac{5000}{42} \approx 119 \text{ shares}$$

The stop distance sets the size. **A wider stop is not more risk — it's a smaller
position.** Most people invert this and take the same quantity regardless, which
means their actual risk varies with volatility in exactly the wrong direction.

## Volatility normalisation

Using ATR instead of a fixed distance makes risk comparable across instruments:

$$Q = \frac{E \times r}{k \times ATR_n}$$

A ₹50 stock and a ₹5,000 stock then contribute equally to portfolio variance,
which is usually what you intended.

> [!warning] Kelly is not a position sizer
> Full Kelly maximises long-run growth *given exact knowledge of your edge* — which
> you don't have. Estimation error is punished asymmetrically, and Kelly drawdowns
> are unbearable in practice. Half-Kelly is a common compromise; a flat 1% is
> better than a badly estimated Kelly.

## The compounding question

- **Percent of current equity** — sizes down after losses, slows the bleed
- **Percent of peak equity** — recovers faster, digs deeper holes

The first is right for most people, because it's the one that's still solvent.

Whatever you choose, test it in [[backtesting]] — sizing rules change the equity
curve more than entry rules do.
