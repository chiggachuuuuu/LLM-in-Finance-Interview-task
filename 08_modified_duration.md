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

Claude already knows the Modified Duration formula — the same number ($36.75) appears in both responses. What changes is the method used to arrive at it. Without instructions, Claude applied a verbal rule of thumb: duration in years roughly equals percentage price sensitivity. This shorthand works for small, round yield changes but breaks down for larger moves or non-standard scenarios, and it cannot be systematically applied or audited in a professional model.

The structured prompt specified the assumption: always use the explicit formula ΔP ≈ −D × Δy × P, not the percentage shorthand. With that instruction, Claude substituted values step by step and produced a verifiable, formula-driven calculation. This is assumption correction — Claude knew both approaches, but defaulted to the informal one. The analyst instruction enforced the professional standard, ensuring the method generalises correctly to any duration, yield change, or price rather than relying on a heuristic that happens to work in simple cases.
