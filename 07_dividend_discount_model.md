# 7. Stock Valuation — Market Multiples vs Dividend Discount Model

## Naive Prompt

```
A stock pays a dividend of $3 per share. Dividends are expected to
grow at 5% per year. Investors require a 9% return. What is the
stock worth?
```

## Claude's Response (without instructions)

> Without knowing the current share price, I can offer a few ways to
> think about this:
>
> **Based on dividend yield:** If you expect a certain price, the
> dividend yield = $3 / Price. A typical yield for a stable dividend
> stock might be 2-4%, which would imply a price of $75-$150.
>
> **Based on growth:** With 5% annual dividend growth and a 9% required
> return, you're looking for income plus growth to sum to around 9%.
> That suggests a current yield of roughly 4%, implying a price near $75.
>
> Could you share the current market price? That would let me calculate
> whether the stock looks overvalued or undervalued.

---

## Structured Prompt (with analyst skill)

```
Value this stock using the Gordon Growth Model (Dividend Discount Model):

P = D1 / (r − g)

Where:
- D1 = next year's expected dividend = D0 × (1 + g)
- r = required rate of return
- g = constant dividend growth rate

This gives the intrinsic value of a stock based purely on its
future dividend stream discounted at the required return. Do not
use market multiples or ask for the current price.

A stock pays a dividend of $3 per share. Dividends are expected to
grow at 5% per year. Investors require a 9% return. What is the
stock worth?
```

## Claude's Response (with instructions)

> **Gordon Growth Model (DDM):**
>
> D1 = D0 × (1 + g) = $3.00 × 1.05 = **$3.15**
>
> P = D1 / (r − g) = $3.15 / (9% − 5%) = $3.15 / 0.04 = **$78.75**
>
> The intrinsic value of this stock is **$78.75 per share**.
>
> If the stock is trading above $78.75, it is overvalued relative to
> its dividend stream. Below $78.75, it is undervalued.

---

## Why the Instructions Made the Difference

Without instructions, Claude did not know to apply the Gordon Growth Model. All the inputs needed to calculate a precise intrinsic value were present in the prompt — current dividend, growth rate, required return — but Claude instead gave a qualitative range and asked for the market price. It defaulted to a yield-based heuristic rather than recognising this as a DDM problem.

The structured prompt taught Claude the formula explicitly: P = D1 / (r − g). With that skill injected, Claude used the dividend, grew it by one period to get D1, applied the discount spread, and arrived at a precise intrinsic value of $78.75 — a number that can be directly compared to the market price to determine whether the stock is cheap or expensive. This is a foundational equity valuation skill used daily in investment analysis, and it required the prompt to supply both the formula and the instruction to use it. The data was always there; the method was not.
