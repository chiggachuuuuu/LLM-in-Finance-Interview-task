# 2. Project Breakeven — Simple Payback vs Discounted Payback

## Naive Prompt

```
A project costs $500,000 upfront and generates $80,000 per year.
When does it break even?
```

## Claude's Response (without instructions)

> **Simple Payback Period = $500,000 / $80,000 = 6.25 years**
>
> That's the straightforward answer — but it ignores the time value of money. Here's the discounted breakeven at a few common hurdle rates:
>
> | Method | Breakeven |
> |--------|-----------|
> | Simple payback | 6.25 years |
> | Discounted @8% | ~9 years |
> | Discounted @10% | ~10.8 years |

---

## Structured Prompt (with analyst instructions)

```
Calculate the discounted payback period, not simple payback.
Discount each year's cash flow at 8% before accumulating.
Find the year when cumulative discounted cash flows recover the
$500,000 investment.

A project costs $500,000 upfront and generates $80,000 per year.
When does it break even?
```

## Claude's Response (with instructions)

> **Discounted Payback @ 8% — Year by Year**
>
> | Year | PV of $80K @8% | Cumulative PV | Remaining |
> |------|---------------|---------------|-----------|
> | 1 | $74,074 | $74,074 | $425,926 |
> | 2 | $68,587 | $142,661 | $357,339 |
> | 3 | $63,507 | $206,168 | $293,832 |
> | 4 | $58,803 | $264,971 | $235,029 |
> | 5 | $54,447 | $319,418 | $180,582 |
> | 6 | $50,414 | $369,832 | $130,168 |
> | 7 | $46,680 | $416,512 | $83,488 |
> | 8 | $43,222 | $459,734 | $40,266 |
> | 9 | $40,020 | $499,754 | $246 |
>
> **Breakeven occurs at just under 9 years** at an 8% discount rate.

---

## Why the Instructions Made the Difference

Without instructions, Claude defaulted to simple payback — $500,000 divided by $80,000 equals 6.25 years. This is the fastest calculation and the most commonly taught version of the metric. It is also the one that overstates how quickly an investor truly recovers their money, because it treats a dollar received in year 6 as worth the same as a dollar today.

The structured prompt supplied the analyst instruction: use discounted payback, apply an 8% discount rate, and accumulate year by year until the investment is recovered in present value terms. With that instruction in place, Claude performed the correct calculation and arrived at approximately 9 years — nearly three years longer than the naive answer. This gap is not a rounding difference; it represents a fundamentally different view of project risk and return. In capital budgeting, the choice between these two methods can determine whether a project is approved or rejected, which is exactly why the analyst instruction matters.
