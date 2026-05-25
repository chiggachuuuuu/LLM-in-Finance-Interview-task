# 6. Fund Manager Performance — CAPM Alpha vs Treynor Ratio

## Naive Prompt

```
A fund returned 14% this year. The market returned 10%, the risk-free
rate is 4%, and the fund's beta is 1.2. How well did the manager perform?
```

## Claude's Response (without instructions)

> **Performance Analysis using CAPM**
>
> Expected Return (CAPM):
> = Risk-Free Rate + Beta × (Market Return − Risk-Free Rate)
> = 4% + 1.2 × (10% − 4%) = 4% + 7.2% = **11.2%**
>
> **Alpha (Manager Performance):**
> Alpha = Actual Return − Expected Return = 14% − 11.2% = **+2.8%**
>
> The manager added real value beyond what market risk exposure alone
> would predict. A +2.8% alpha is a solid result.

---

## Structured Prompt (with analyst skill)

```
Evaluate this fund using the Treynor Ratio, not CAPM alpha.

The Treynor Ratio measures return earned per unit of market risk (beta):
Treynor Ratio = (Portfolio Return − Risk-Free Rate) / Beta

A higher Treynor Ratio means more return per unit of systematic risk taken.
To benchmark, also calculate the market's Treynor Ratio:
Market Treynor = (Market Return − Risk-Free Rate) / 1.0

If the fund's Treynor exceeds the market's, the manager outperformed
on a risk-adjusted basis.

A fund returned 14% this year. The market returned 10%, the risk-free
rate is 4%, and the fund's beta is 1.2. How well did the manager perform?
```

## Claude's Response (with instructions)

> **Treynor Ratio — Fund vs Market**
>
> Fund Treynor = (14% − 4%) / 1.2 = 10% / 1.2 = **8.33**
>
> Market Treynor = (10% − 4%) / 1.0 = **6.00**
>
> The fund's Treynor Ratio of 8.33 exceeds the market's 6.00, meaning
> the fund generated more excess return per unit of systematic risk than
> the market itself. The manager outperformed on a risk-adjusted basis.

---

## Why the Instructions Made the Difference

Without instructions, Claude evaluated the manager using CAPM alpha — calculating the expected return based on beta and measuring the gap. This is a valid and widely used approach. But alpha only tells you how much excess return was produced; it does not tell you how efficiently that return was earned relative to the systematic risk taken on.

The structured prompt introduced the Treynor Ratio — a metric Claude would not reach on its own because the naive question does not hint at it. The Treynor Ratio divides excess return by beta, producing a single number that can be directly compared to the market benchmark. A fund with a Treynor of 8.33 vs the market's 6.00 is unambiguously more efficient per unit of risk, regardless of its absolute return. This is the metric a risk-adjusted performance analyst would use, and it required explicit instruction to surface. The skill was injected through the prompt.
