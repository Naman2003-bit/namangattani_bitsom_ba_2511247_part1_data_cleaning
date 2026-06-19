# Part 1: Business Data Cleaning, Validation & Excel Reporting

## Problem Summary

The goal of this project was to clean, validate, and prepare a retail sales dataset for business analysis purposes. The original raw dataset had numerous data quality problems such as missing values, inconsistent text formatting, duplicate entries, invalid discount values, date-related issues, and order status discrepancies. The end objective was to produce an analysis-ready dataset along with data quality reports and pivot-based business summaries.

---

## Dataset Description

The dataset holds order-level retail transaction records covering:

* Order Information
* Customer Information
* Region and Location Details
* Product Details
* Sales and Profit Data
* Shipping Information
* Payment and Order Status

Raw Dataset File:

* raw_orders.xlsx

Cleaned Dataset File:

* cleaned_orders.xlsx

---

## Tools Used

* Microsoft Excel
* Pivot Tables
* Excel Formulas
* Data Validation Techniques

Key Excel Functions Used:

* TRIM
* PROPER
* SUBSTITUTE
* IF
* COUNTIF
* YEAR
* TEXT
* Date Formatting
* Pivot Tables

---

## Cleaning Steps Performed

### Text Cleaning

The fields below were standardized:

* Customer Name
* Segment
* Region
* State
* City
* Category
* Sub Category
* Ship Mode
* Payment Status
* Order Status

Actions carried out:

* Removed leading, trailing, and extra spaces
* Applied uniform capitalization
* Fixed inconsistent naming conventions
* Eliminated unwanted formatting artifacts

---

### Date Cleaning

The following date columns were processed:

* Order Date
* Ship Date

Actions carried out:

* Unified date formats across records
* Converted text-based dates into valid Excel date values
* Derived shipping delay in days
* Validated shipping date sequences

---

### Duplicate Handling

Duplicate analysis produced the following results:

* Exact Duplicate Rows: 20
* Duplicate Order IDs: 31

All duplicate records were flagged for review and documented accordingly.

---

### Calculated Columns Created

The following derived fields were added to the dataset:

* cleaned_discount
* calculated_sales
* calculated_profit
* profit_margin
* shipping_delay_days
* order_month
* order_year
* data_quality_flag

---

## Business Rules Applied

### Missing Region

* Blank values were filled with "Unknown"

### Missing Ship Mode

* Blank values were filled with "Unknown"

### Missing Discount

* Missing entries were replaced with 0 where supporting fields were valid

### Negative Discount

* Records with negative discount values were flagged as invalid

### Invalid Shipping Records

* Any record where Ship Date preceded Order Date was flagged as invalid

### Cancelled Orders

* Excluded from completed sales reporting

### Failed Payments

* Excluded from completed sales reporting

### Refunded Orders

* Tracked separately for further business review

---

## Data Quality Issues Found

| Issue                    | Count |
| ------------------------ | ----- |
| Missing Region           | 26    |
| Missing Ship Mode        | 22    |
| Missing Discount         | 18    |
| Negative Discount        | 16    |
| Exact Duplicate Rows     | 20    |
| Duplicate Order IDs      | 31    |
| Invalid Shipping Records | 453   |
| Cancelled Orders         | 146   |
| Returned Orders          | 164   |
| Failed Payments          | 69    |
| Refunded Payments        | 72    |

---

## Pivot Reports Created

The following pivot summaries were developed:

1. Sales and Profit by Region
2. Sales and Profit by Category and Sub Category
3. Order Count by Ship Mode
4. Profit Margin by Customer Segment
5. Cancelled Orders by Region
6. Monthly Sales Trend

---

## Key Business Insights

### Regional Performance

* South region recorded the highest overall sales figures.
* Records with unknown regions accounted for a small share of total sales.

### Category Performance

* Technology led all categories in both sales and profit.
* Furniture and Office Supplies also made notable contributions to overall revenue.

### Shipping Analysis

* Standard Class was the most commonly used shipping method across orders.
* Unknown shipping modes were limited in volume but flagged for review.

### Customer Segment Analysis

* Small Business customers delivered the highest average profit margin.
* The Consumer segment recorded the lowest profit margin among major segments.

### Order Quality

* A significant number of invalid shipping records were detected and flagged.
* Negative discount entries were successfully isolated from business calculations.

---

## Assumptions and Limitations

### Assumptions

* Missing Region values were categorized as Unknown.
* Missing Ship Mode values were categorized as Unknown.
* Missing Discount values were set to 0 where related fields were valid.
* Duplicate Order IDs were retained as they may represent legitimate business transactions.

### Limitations

* Duplicate Order IDs still require manual business review for final resolution.
* Invalid shipping records may stem from date entry errors in the source system.
* Sales and profit mismatch analysis is dependent on the source system's calculation logic.
* Data quality checks were restricted to the fields present in the available dataset.

---

## Screenshots Included

The repository includes:

* raw_data_preview.png
* cleaned_data_preview.png
* pivot_summary_1.png
* pivot_summary_2.png

---

## Final Outcome

The raw dataset was successfully cleaned, validated, and converted into an analysis-ready format. Data quality reports and pivot-based business summaries were produced to support informed business review and decision-making.
