# City Budget Variance Analysis (Excel)

An Excel variance tracker built on a public city budget dataset. It rolls 1,533 budget lines up to divisions and departments, flags unusual changes using a two-test rule (% and $), and ranks the biggest line-level changes.

I built it as a learning project to practice variance analysis, the routine of comparing planned and actual spend, flagging what's unusual, and asking why.

## Dataset

- **Source:** "City Budget Summary and Recommendations" on Kaggle
- **Author:** thedevastator
- **Link:** https://www.kaggle.com/datasets/thedevastator/city-budget-summary-and-recommendations
- **File used:** `fy2022-proposed-city-budget-book-1.csv` (1,533 rows, one fund: City General)

Columns used: Fund, Account Type, Division, Department, Summary Account, GL Account, 2019 Actual, 2020 Actual, 2021 Budget, 2022 Recommend, 2023 Forecast.

This is public data. No employer or confidential data is used.

## What's in the workbook

File: `city_budget_variance_analysis.xlsx`

| Sheet | What it does |
|---|---|
| Overview | Change the % and $ thresholds, see fund totals by year, flag counts, limitations and colour legend |
| Division Summary | 18 divisions: variances, flags, two charts, and a notes column for drivers and actions |
| Department Summary | The same view for 72 departments |
| Top Variances | The 15 largest expense changes, ranked automatically |
| Data | All 1,533 source rows plus the variance formulas |

## Method

- **Variance** = later amount − earlier amount. **Variance %** = variance ÷ the starting amount.
- Two comparisons are made: **2021 Budget vs 2020 Actual**, and **2022 Recommend vs 2021 Budget**.
- **Flag rule:** a line is marked REVIEW only when the change is at least **10%** AND at least **$250,000**. This stops tiny accounts with huge percentage swings from hiding the real signal. If the starting amount is zero, the $ test alone decides.
- Both thresholds are input cells on the Overview sheet. Change them and every flag updates.
- Analysis covers **expenses only**. Revenues are stored as negatives in the source file.

## Key findings

- Budgeted spend rises 5.8% from the 2020 actual ($483.0M) to the 2021 budget ($510.9M), then 5.7% to the 2022 recommendation ($539.9M).
- Public Safety rises 20.6% (+$31.5M) from 2020 actual to 2021 budget, more than the whole net increase.
- Police salaries go from $19.0M to $36.5M (+92%) and Fire salaries from $17.7M to $31.5M (+78%). Separate vacation and sick-leave lines show spending in 2020 but zero in the budget. This may be a reclassification into salaries, but the data does not mention it.
- Debt service lines (PPBA rental payments) swing sharply between years.
- The 2021 and 2022 budgets balance exactly, but the 2023 forecast shows expenses about $12.2M above revenue.
- 52 of 1,339 expense lines are flagged for 2021B vs 2020A, and 20 for 2022R vs 2021B.

## Limitations

- **This is not a true same-year budget vs actual.** The file has actuals for 2019 and 2020 and budget, recommended and forecast figures for 2021 to 2023, but no 2021 actuals. The comparisons are a budget against the last actual year, and a proposal against the current budget.
- Large line-level changes can come from account reclassification rather than real spending changes. Treat flags as questions to investigate, not findings.
- The source does not explain any change. Interpretations in the workbook and in this README are mine and are unconfirmed.

## How to use

1. Download `city_budget_variance_analysis.xlsx`.
2. Open the **Overview** sheet and adjust the yellow threshold cells if you want.
3. Review **Division Summary**, **Department Summary** and **Top Variances**.

## Credits

Data: "City Budget Summary and Recommendations" by thedevastator on Kaggle.
