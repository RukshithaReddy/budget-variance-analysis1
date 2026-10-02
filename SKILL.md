---
name: budget-variance-analysis
description: Compare budget vs. actual figures, identify favourable and adverse variances, highlight significant deviations, and provide concise management commentary on key drivers and required actions.
---

# Budget vs Actual Variance Analysis

This skill turns a table of budget and actual figures into a short, accurate commentary that a finance manager can read in under a minute.

## Inputs

Each line item has:
- a name (for example "Marketing")
- a type: `revenue` or `expense`
- a budget amount
- an actual amount

The user may also give a review threshold in percent. If none is given, use 10%.

## Calculations (must be exact)

For every line:
1. Variance = Actual - Budget
2. Variance % = Variance / Budget x 100 (if Budget is 0, variance % is "not defined"; say so, do not calculate it)
3. Favourable or adverse:
   - Expense: actual below budget is favourable, actual above budget is adverse
   - Revenue: actual above budget is favourable, actual below budget is adverse
   - Variance of zero is "on budget"
4. Flag the line for review if its variance % is beyond the threshold in either direction, or if Budget is 0 and Actual is not 0.

Totals:
- Net = Total revenue - Total expenses, for both budget and actual
- Net variance = Actual net - Budget net

When figures are supplied already calculated (for example by an application), use them exactly as given. Never recalculate, round differently, or change a number.

## Writing the commentary

Keep it under 150 words, in plain text (no tables, no markdown symbols), in this order:
1. One headline sentence on the overall result (net variance, favourable or adverse).
2. One sentence per flagged line, stating the line, the variance in rupees and percent, and whether it is favourable or adverse.
3. A short "Check next" list of at most three hyphen-led items. Each is a question or item to verify, such as "Confirm whether the marketing overspend was a one-off campaign".

## Rules that must not be broken

- Use only the numbers provided. Do not invent figures, totals or percentages.
- Do not state a cause as fact. The data shows what changed, not why. Suggest possible causes only as items to check.
- Do not give investment, tax or legal advice.
- If a line is not flagged, do not comment on it individually.
- If the input is incomplete, unclear or contradictory, say exactly what is missing instead of guessing.
- Use Indian rupee formatting (for example Rs 1,25,000) unless the user specifies another currency.
- Tone: neutral, specific and professional, written for a CFO or finance manager.

## Worked example

Input (threshold 10%):
- Revenue, budget 500000, actual 540000
- Marketing (expense), budget 100000, actual 118000
- Rent (expense), budget 60000, actual 60000

Expected commentary:
Net result is favourable by Rs 22,000 (budget Rs 3,40,000, actual Rs 3,62,000). Marketing is Rs 18,000 (18.0%) over budget, an adverse variance beyond the 10% threshold. Revenue (8.0% above budget) and Rent (on budget) are within the threshold and are not flagged.
Check next:
- Confirm whether the marketing overspend was planned or a one-off campaign
- Check whether the extra marketing spend contributed to the higher revenue

## Self-check before answering

- Does every number in the commentary appear in the input or calculations?
- Are favourable and adverse correctly assigned for revenue vs expense lines?
- Is every flagged line mentioned, and no unflagged line?
- Is the commentary under 150 words with no invented causes?

