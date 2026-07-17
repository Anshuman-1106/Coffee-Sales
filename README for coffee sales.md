# Coffee Sales Dataset

## Overview

This dataset contains individual transaction records from a coffee vending/shop
machine, covering **3,636 sales** from **March 1, 2024 to March 23, 2025**
(roughly one year of trading). Each row represents a single drink purchase.

- **File:** `Coffe_sales.xlsx`
- **Sheet:** `index_1`
- **Rows:** 3,636
- **Columns:** 12

## Column Reference

| Column | Type | Description |
|---|---|---|
| `date` | date | Calendar date of the transaction (no time component) |
| `datetime` | datetime | Full timestamp of the transaction, to the millisecond |
| `hour_of_day` | integer | Hour the transaction occurred (0–23), derived from `datetime` |
| `cash_type` | text | Payment method: `card` or `cash` |
| `card` | text | Anonymized card ID (e.g. `ANON-0000-0000-0001`); **empty when `cash_type` is `cash`** |
| `money` | decimal | Transaction amount paid |
| `coffee_name` | text | Drink purchased — one of: Latte, Hot Chocolate, Americano, Americano with Milk, Cocoa, Cortado, Espresso, Cappuccino |
| `Time_of_Day` | text | Bucketed period of the sale: `Morning`, `Afternoon`, or `Night` |
| `Weekday` | text | Abbreviated day of week (`Mon`–`Sun`) |
| `Month_name` | text | Abbreviated month (`Jan`–`Dec`) |
| `Weekdaysort` | integer | Numeric sort key for `Weekday` (1 = Monday … 7 = Sunday) |
| `Monthsort` | integer | Numeric sort key for `Month_name` (1 = January … 12 = December) |

## Data Notes

- **Missing values:** `card` is blank for the 89 transactions paid in cash — this
  is expected, not missing data, since cash purchases have no card ID.
- **Payment split:** the majority of transactions are paid by `card`; `cash`
  is a smaller subset.
- **Price range:** transaction amounts (`money`) range from **18.12 to 40.00**,
  with an average of **~31.75** per transaction. Prices vary primarily by drink
  type rather than being fixed per product.
- **Derived columns:** `hour_of_day`, `Time_of_Day`, `Weekday`, `Month_name`,
  `Weekdaysort`, and `Monthsort` all appear to be derived from `datetime`, and
  are included as convenience fields for filtering/grouping without needing to
  re-parse the timestamp.
- **Currency:** the currency unit is not labeled in the file — confirm with the
  data source before using amounts in financial reporting.

## Suggested Uses

- Sales trends over time (daily, weekly, monthly, seasonal)
- Best-selling drinks by volume or revenue
- Peak trading hours / time-of-day demand patterns
- Cash vs. card payment behavior
- Weekday vs. weekend sales comparisons

## Suggested Citation / Attribution

If this dataset originated from a public source (e.g. Kaggle), credit the
original publisher when sharing derived analysis.
