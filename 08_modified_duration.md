# 8. Bond Price Sensitivity — Qualitative Guess vs Modified Duration

## Naive Prompt

```
A bond has a modified duration of 7 years and a current price of
$1,050. If interest rates rise by 0.5%, how much will the bond
price change?
```

## Claude's Response (without instructions)

> With a modified duration of 7 years, this bond is moderately sensitive
> to interest rate changes.
>
> A rough rule of thumb: for every 1% rise in rates, the bond price
> falls by approximately its duration in percentage terms.
>
> So for a 0.5% rate rise:
> Approximate price change ≈ −7 × 0.5% = −3.5%
>
> On a $1,050 bond: −3.5% × $1,050 ≈ **−$36.75**
>
> The bond would fall to approximately $1,013. Note this is an
> approximation — the actual change also depends on convexity.

---

## Structured Prompt (with analyst skill)

```
Use the Modified Duration formula to calculate the exact dollar
price change:

ΔP ≈ −Modified Duration × Δy × P

Where:
- Modified Duration = sensitivity of price to yield changes
- Δy = change in yield (as a decimal)
- P = current bond price

This gives the dollar price change directly. Apply it precisely
— do not use percentage approximations or rules of thumb.
Show the formula with values substituted in.

A bond has a modified duration of 7 years and a current price of
$1,050. If interest rates rise by 0.5%, how much will the bond
price change?
```

## Claude's Response (with instructions)

> **Modified Duration Formula:**
>
> ΔP ≈ −Modified Duration × Δy × P
>
> ΔP ≈ −7 × 0.005 × $1,050
>
> ΔP ≈ −7 × $5.25
>
> **ΔP ≈ −$36.75**
>
> The bond price falls by **$36.75**, from $1,050.00 to $1,013.25.
> The negative sign confirms the inverse relationship between yields
> and bond prices.

---

## Why the Instructions Made the Difference

Without instructions, Claude gave a correct answer using a verbal "rule of thumb" — duration in years roughly equals percentage price sensitivity. It arrived at the same number ($36.75) but via an informal heuristic rather than the actual formula. In a professional context, this matters: the rule of thumb breaks down for larger yield moves or non-standard durations, and it cannot be systematically applied or audited.

The structured prompt taught Claude the Modified Duration formula explicitly: ΔP ≈ −D × Δy × P. With that skill in place, Claude substituted the values precisely, showed each step, and produced a verifiable calculation. The formula is the professional standard for fixed income risk — it is what a bond trader, a risk manager, or a portfolio attribution system would use. The naive prompt produced the right number by accident; the structured prompt produced it by method. Teaching the formula ensures the approach generalises correctly to any duration, yield change, or price — not just the specific case where the shortcut happens to work.
