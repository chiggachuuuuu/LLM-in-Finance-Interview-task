# 1. DCF Valuation — Perpetuity vs Structured Model

## Naive Prompt

```
A company generates $20M in free cash flow, growing at 3% per year.
WACC is 9%. What is the enterprise value?
```

## Claude's Response (without instructions)

> This is a classic Gordon Growth Model (terminal value / perpetuity growth model):
>
> EV = FCF / (WACC − g) = $20M / (9% − 3%) = $20M / 6% = **$333.3M**
>
> Key assumptions baked in: growth rate (3%) is constant and perpetual, WACC (9%) > g (3%), and free cash flow of $20M is treated as next year's expected FCF.

---

## Structured Prompt (with analyst instructions)

```
Value this company using a structured DCF — not a simple perpetuity.
Project FCF explicitly for 5 years at the given growth rate, discount
each year at WACC, then apply Gordon Growth only for the terminal value
(year 6 onwards). Enterprise value = PV of 5-year FCFs + PV of terminal value.

A company generates $20M in free cash flow, growing at 3% per year.
WACC is 9%. What is the enterprise value?
```

## Claude's Response (with instructions)

> **Step 1: Project FCFs for Years 1–5**
>
> | Year | FCF | PV (÷1.09ⁿ) |
> |------|-----|-------------|
> | 1 | $20.6M | $18.9M |
> | 2 | $21.2M | $17.9M |
> | 3 | $21.8M | $16.9M |
> | 4 | $22.5M | $15.9M |
> | 5 | $23.2M | $15.1M |
>
> Sum of PV of FCFs = **$84.7M**
>
> **Step 2: Terminal Value**
>
> Year 6 FCF = $23.2M × 1.03 = $23.9M
> TV = $23.9M / (9% − 3%) = $398.1M
> PV of TV = $398.1M / (1.09)⁵ = **$258.8M**
>
> **Enterprise Value = $84.7M + $258.8M = $343.4M**

---

## Why the Instructions Made the Difference

Without instructions, Claude applied the Gordon Growth Model directly to the current year's free cash flow — a valid shortcut, but one that collapses the entire future of the business into a single formula and ignores how the cash flows build up over an explicit projection period. This is the approach you might use for a back-of-envelope estimate, but not what an investment banking analyst would present in a model.

The structured prompt provided the methodology: project cash flows year by year for a defined horizon, discount each one individually, then apply the terminal value formula only from year 6 onwards. This is the industry-standard DCF structure. The instructions acted as an analyst skill — telling Claude not just what to calculate, but how to structure the calculation. The result is a more defensible number ($343M vs $333M) with a transparent breakdown that a client or senior analyst can review and stress-test.
