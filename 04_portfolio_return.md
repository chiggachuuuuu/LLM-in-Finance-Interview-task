# 4. Portfolio Return — Equal-Weight Assumption vs Value-Weighted

## Naive Prompt

```
My portfolio holds three stocks:
Stock A returned 20% this year
Stock B returned 8% this year
Stock C returned 15% this year
What was my portfolio return?
```

## Claude's Response (without instructions)

> Portfolio return requires knowing the weights — without them, the best I can offer is:
>
> **Simple average (equal-weighted assumption):**
> = (20% + 8% + 15%) / 3 = **14.33%**
>
> This is only correct if you have exactly the same dollar amount in each stock.
>
> | Scenario | W_A | W_B | W_C | Portfolio Return |
> |----------|-----|-----|-----|-----------------|
> | Equal weight | 33.3% | 33.3% | 33.3% | 14.33% |
> | Heavy in A | 60% | 20% | 20% | 15.8% |
> | Heavy in B | 20% | 60% | 20% | 12.6% |
> | Heavy in C | 20% | 20% | 60% | 14.2% |
>
> What were your dollar amounts in each stock? With those I can give you the exact weighted return.

---

## Structured Prompt (with analyst instructions)

```
Calculate portfolio return as a value-weighted average.
Portfolio return = Σ (weight × return) for each position.
Never assume equal weights.

My portfolio holds three stocks:
Stock A: 20% return, 10% of portfolio
Stock B: 8% return, 60% of portfolio
Stock C: 15% return, 30% of portfolio
What was my portfolio return?
```

## Claude's Response (with instructions)

> **Portfolio Return = Σ (Weight × Return)**
>
> | Stock | Weight | Return | Contribution |
> |-------|--------|--------|--------------|
> | A | 10% | 20% | 2.00% |
> | B | 60% | 8% | 4.80% |
> | C | 30% | 15% | 4.50% |
> | **Total** | **100%** | — | **11.30%** |
>
> **Portfolio Return = 11.30%**
>
> Stock B dominates — 60% of your capital but only an 8% return, contributing 4.80%. It's the single biggest drag on performance. A simple average would have given 14.33% — nearly 3 points higher than your actual 11.30%, entirely because your largest position was your weakest performer. Weights matter.

---

## Why the Instructions Made the Difference

Without position size information, Claude assumed equal weights and returned 14.33% — a simple arithmetic average of the three stock returns. This is the only calculation possible given the data provided, and Claude correctly flagged that it only holds if all positions are equal. But in practice, portfolios are almost never equal-weighted, and reporting 14.33% to a client when the actual return was 11.30% would be a significant error.

The structured prompt did two things: it supplied the missing position weights, and it included the analyst instruction to always use value-weighted averaging and never assume equal weights. With that instruction and data in place, Claude calculated the correct 11.30% return, breaking down each stock's contribution and explicitly noting that the simple average would have overstated performance by nearly 3 percentage points. This is precisely the kind of error that analyst instructions prevent — not a formula mistake, but a methodology assumption that produces a materially wrong answer when applied to a real portfolio.
