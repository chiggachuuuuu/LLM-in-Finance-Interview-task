# Finance Prompt Co-pilot

This repo demonstrates how structured prompts — containing analyst instructions, agent skills, and methodological guardrails — change the answer Claude gives to finance questions.

The core insight is not about vague vs. clear wording. The question and data are identical in both prompts. What changes is the second prompt adds a layer of professional instruction that guides Claude toward the methodology a trained analyst would use. Without it, Claude picks a valid but incomplete or contextually wrong approach. With it, Claude follows the correct one.

This pattern is repeatable across different parameter values, dates, and scenarios — making it a reliable demonstration of how co-pilot prompting works in practice.

---

## The Problems

There are two categories of examples in this repo.

### Category A — Assumption Correction
Claude knows the methodology but picks the wrong one without guidance. The right answer comes from specifying which assumption to apply.

| # | Problem | Without instructions | With instructions |
|---|---------|---------------------|-------------------|
| [1](01_dcf_valuation.md) | DCF valuation | $333M (simple perpetuity) | $343M (structured 5-year DCF) |
| [2](02_breakeven_analysis.md) | Project breakeven | 6.25 years (simple payback) | ~9 years (discounted payback) |
| [4](04_portfolio_return.md) | Portfolio return | 14.33% (equal-weight assumed) | 11.30% (value-weighted) |
| [5](05_leverage_ratio.md) | Leverage ratio | 0.67x (debt-to-equity) | 0.40 (debt-to-assets) |

### Category B — Skill Injection
Claude genuinely does not know to use the method. The structured prompt teaches it a formula or framework it would never reach on its own.

| # | Problem | Without instructions | With instructions |
|---|---------|---------------------|-------------------|
| [3](03_bond_holding_return.md) | Bond return | 5.26% current yield | 6.32% holding period return (HPR) |
| [6](06_treynor_ratio.md) | Fund manager performance | CAPM alpha only | Treynor Ratio = 8.33 vs market 6.00 |
| [7](07_dividend_discount_model.md) | Stock valuation | Qualitative yield range | DDM intrinsic value = $78.75 |
| [8](08_modified_duration.md) | Bond price sensitivity | Rule of thumb estimate | Modified Duration formula → −$36.75 |
| [9](09_dupont_decomposition.md) | ROE analysis | Qualitative observations | DuPont: margin × turnover × leverage |

---

## How to Reproduce

Each prompt file contains the exact prompts used. Copy the naive prompt into a new Claude chat, note the response, then copy the structured prompt and compare.

The numbers in each prompt are fixed, but the error pattern repeats with any values — the methodology gap is structural, not data-dependent.

---

## Key Takeaway

There are two ways structured prompts improve Claude's finance answers.

The first is assumption correction — Claude knows multiple valid methods and picks the wrong one by default. Specifying the methodology resolves the ambiguity and produces the professionally correct answer.

The second, and more powerful, is skill injection — Claude does not know to use a particular formula at all. The structured prompt teaches it the method explicitly: the Treynor Ratio, the Gordon Growth Model, Modified Duration, DuPont decomposition. Without the instruction, Claude gives a qualitative answer or uses a cruder approximation. With it, Claude applies the exact professional-grade formula and produces a precise, auditable result.

This is what a finance co-pilot needs to do: not just answer questions, but answer them using the right method for the context — even when that method has to be taught.
