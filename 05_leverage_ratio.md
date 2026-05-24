# 5. Leverage Ratio — Debt-to-Equity vs Debt-to-Assets

## Naive Prompt

```
A company has total assets of $1,000,000, total debt of $400,000,
and equity of $600,000. What is its leverage ratio?
```

## Claude's Response (without instructions)

> The most common leverage ratios for this company:
>
> **Debt-to-Equity: 0.67x** — $400K ÷ $600K. For every dollar of equity, the company carries $0.67 of debt. Generally, below 1x is considered conservative.
>
> **Debt-to-Assets: 0.40** — $400K ÷ $1M. 40% of assets are financed by debt, 60% by equity. A solid, majority-equity-funded structure.
>
> **Equity Multiplier: 1.67x** — $1M ÷ $600K. Assets are 1.67x the equity base, a common input in DuPont analysis.
>
> What this tells you: this is a moderately conservative capital structure. Whether this is "good" depends heavily on the industry — capital-intensive sectors like real estate or utilities typically run much higher leverage, while software or services companies often run lower.

---

## Structured Prompt (with analyst instructions)

```
When reporting leverage, always use the debt-to-assets ratio, not
debt-to-equity. Debt-to-assets = Total Debt / Total Assets.
This shows what fraction of assets are financed by debt.

A company has total assets of $1,000,000, total debt of $400,000,
and equity of $600,000. What is its leverage ratio?
```

## Claude's Response (with instructions)

> **Debt-to-Assets ratio: 0.40**
>
> $400,000 ÷ $1,000,000 = **0.40**, meaning 40% of the company's assets are financed by debt and 60% by equity.
>
> This reflects a conservative capital structure with a majority equity-funded asset base.

---

## Why the Instructions Made the Difference

Without instructions, Claude gave three different leverage ratios — debt-to-equity (0.67x), debt-to-assets (0.40), and the equity multiplier (1.67x) — all calculated correctly, along with commentary on what each means. This is thorough and technically accurate, but it is not useful in a professional context where a specific metric is required. A credit analyst, a risk team, and a regulatory report may each require a different ratio, and returning all three without a recommendation creates ambiguity rather than clarity.

The structured prompt specified the house methodology: always use debt-to-assets, not debt-to-equity. With that instruction, Claude returned a single, precise answer — 0.40 — with a clean one-line interpretation. This is the difference between a general assistant and a finance co-pilot. The co-pilot knows which metric the firm uses, applies it consistently, and does not present alternatives that could introduce confusion. The instruction encoded that professional standard directly into the prompt, ensuring the same methodology is applied every time the question is asked, regardless of who is asking or what parameters are used.
