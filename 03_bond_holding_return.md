# 3. Bond Return — Current Yield vs Holding Period Return

## Naive Prompt

```
A bond has a coupon rate of 5%, face value $1,000, currently trading
at $950. What return will I earn?
```

## Claude's Response (without instructions)

> Yield to Maturity requires knowing the maturity date — without it, here's what we can calculate:
>
> **1. Current Yield** = Annual Coupon / Price = $50 / $950 = **5.26%**
>
> This is the simplest measure — your cash income return on what you actually paid.
>
> **2. Approximate YTM** (needs maturity, shown illustratively):
>
> | Maturity | Approx. YTM |
> |----------|-------------|
> | 5 years | 6.02% |
> | 10 years | 5.58% |
> | 20 years | 5.34% |
> | 30 years | 5.27% |
>
> What's the maturity date? With that I can give you the exact YTM.

---

## Structured Prompt (with analyst instructions)

```
Calculate the holding period return for a one-year hold, not YTM.
Use: HPR = (Coupon + Ending Price - Beginning Price) / Beginning Price
The bond will be priced at $960 after one year.

A bond has a coupon rate of 5%, face value $1,000, currently trading
at $950. What return will I earn?
```

## Claude's Response (with instructions)

> **Straightforward one-year HPR:**
>
> HPR = (Coupon + Ending Price − Beginning Price) / Beginning Price
>
> HPR = ($50 + $960 − $950) / $950
>
> HPR = $60 / $950
>
> **HPR = 6.32%**
>
> Breaking down the $60 total return:
>
> | Component | Amount | Contribution |
> |-----------|--------|--------------|
> | Coupon income | $50 | 5.26% |
> | Capital gain ($960 − $950) | $10 | 1.05% |
> | **Total** | **$60** | **6.32%** |

---

## Why the Instructions Made the Difference

Without instructions, Claude gave the current yield (5.26%) and a table of approximate YTM figures across different maturities, then asked for the maturity date to go further. This is a reasonable response from a general assistant — current yield is the simplest bond return metric and YTM is the standard long-run measure. But neither answers the actual question a portfolio manager would ask when evaluating a short-term trade: what will I actually earn if I hold this bond for one year and sell it?

The structured prompt provided the analyst instruction: use holding period return, apply the specific formula, and assume an ending price of $960. With that instruction, Claude calculated 6.32% — a number that accounts for both the coupon income and the price appreciation over the holding period. This is the correct metric for a one-year investment decision, and it produces a materially different answer from the 5.26% current yield the naive prompt returned. The instruction did not change the question or the data; it specified the professional methodology appropriate for the context.
