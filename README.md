# Finance Prompt Co-pilot

This repo demonstrates how structured prompts — containing analyst instructions, agent skills, and methodological guardrails — change the answer Claude gives to finance questions.

The core insight is not about vague vs. clear wording. The question and data are identical in both prompts. What changes is the second prompt adds a layer of professional instruction that guides Claude toward the methodology a trained analyst would use. Without it, Claude picks a valid but incomplete or contextually wrong approach. With it, Claude follows the correct one.

This pattern is repeatable across different parameter values, dates, and scenarios — making it a reliable demonstration of how co-pilot prompting works in practice.

---

## The 5 Problems

| # | Problem | Without instructions | With instructions |
|---|---------|---------------------|-------------------|
| [1](01_dcf_valuation.md) | DCF valuation | $333M (simple perpetuity) | $343M (structured 5-year DCF) |
| [2](02_breakeven_analysis.md) | Project breakeven | 6.25 years (simple payback) | ~9 years (discounted payback) |
| [3](03_bond_holding_return.md) | Bond return | 5.26% current yield | 6.32% holding period return |
| [4](04_portfolio_return.md) | Portfolio return | 14.33% (equal-weight assumed) | 11.30% (value-weighted) |
| [5](05_leverage_ratio.md) | Leverage ratio | 0.67x (debt-to-equity) | 0.40 (debt-to-assets) |

---

## How to Reproduce

Each prompt file contains the exact prompts used. Copy the naive prompt into a new Claude chat, note the response, then copy the structured prompt and compare.

The numbers in each prompt are fixed, but the error pattern repeats with any values — the methodology gap is structural, not data-dependent.

---

## Key Takeaway

Claude is not making calculation errors. It is making methodology choices — defaulting to the most common or most obvious approach when no instruction is given. The structured prompt supplies the missing context: which formula to use, which metric matters, and what professional standard applies. That is what a finance co-pilot needs to do.
