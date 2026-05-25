# 9. ROE Analysis — Single Ratio vs DuPont Decomposition

## Naive Prompt

```
Company A has ROE of 22%. Company B has ROE of 22%. Which company
has the stronger business?

Company A: Net income $11M, Revenue $100M, Assets $80M, Equity $50M
Company B: Net income $11M, Revenue $200M, Assets $110M, Equity $50M
```

## Claude's Response (without instructions)

> Both companies have identical ROE of 22% ($11M / $50M), so on that
> metric alone they are equal.
>
> However, looking at the other data:
>
> - Company A has higher net margin: $11M / $100M = **11%** vs
>   Company B's $11M / $200M = **5.5%**
> - Company B has higher revenue, suggesting more scale but lower
>   profitability per dollar of sales
> - Company A appears more asset-efficient relative to its revenue size
>
> Without more context (industry, growth rate, debt levels), it's
> difficult to say which is "stronger." They have reached the same
> ROE through different means.

---

## Structured Prompt (with analyst skill)

```
Analyse this using the DuPont decomposition. Do not compare ROE
as a single number.

DuPont breaks ROE into three drivers:
ROE = Net Profit Margin × Asset Turnover × Equity Multiplier

Where:
- Net Profit Margin = Net Income / Revenue (profitability)
- Asset Turnover = Revenue / Total Assets (efficiency)
- Equity Multiplier = Total Assets / Equity (leverage)

Calculate all three components for each company and identify
which driver is responsible for each company's ROE. This reveals
whether ROE is driven by genuine profitability, operational
efficiency, or financial leverage.

Company A: Net income $11M, Revenue $100M, Assets $80M, Equity $50M
Company B: Net income $11M, Revenue $200M, Assets $110M, Equity $50M
```

## Claude's Response (with instructions)

> **DuPont Decomposition**
>
> | Component | Formula | Company A | Company B |
> |-----------|---------|-----------|-----------|
> | Net Profit Margin | Net Income / Revenue | 11% | 5.5% |
> | Asset Turnover | Revenue / Assets | 1.25x | 1.82x |
> | Equity Multiplier | Assets / Equity | 1.60x | 2.20x |
> | **ROE** | Margin × Turnover × Multiplier | **22%** | **22%** |
>
> **What this reveals:**
>
> Company A reaches 22% ROE through **high margins** (11%) with
> moderate efficiency and low leverage. This is a premium, asset-light
> business model — think high-margin SaaS or branded consumer goods.
>
> Company B reaches the same 22% ROE through **high asset turnover**
> (1.82x) and **higher leverage** (2.20x), but thin margins (5.5%).
> This looks like a high-volume, low-margin business — think retail
> or distribution — using leverage to boost returns.
>
> Same ROE, completely different risk profiles. Company A's ROE is
> more sustainable; Company B's depends on maintaining volume and
> managing debt.

---

## Why the Instructions Made the Difference

Without instructions, Claude noticed that the two companies had different margins and hinted at the difference, but stopped short of a structured analysis. It gave qualitative observations without a framework, and could not definitively explain why the ROEs were identical despite the companies being so different.

The structured prompt taught Claude the DuPont decomposition — a three-factor formula that breaks ROE into profitability (margin), efficiency (asset turnover), and leverage (equity multiplier). This is a skill Claude did not apply on its own. With it injected, Claude produced a complete table showing exactly which driver accounts for each company's return, and drew a sharp conclusion: Company A's ROE is margin-driven and more sustainable, while Company B's relies on leverage and volume. Two companies with identical ROE turn out to have fundamentally different business models and risk profiles — a conclusion that is only reachable by teaching Claude the decomposition formula.
