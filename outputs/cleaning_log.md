# Cleaning Log

## Project
Business Data Cleaning, Validation & Excel Reporting

## Issues Found
The raw dataset had several data quality problems, including:

* Blank values in the Region, Ship Mode, and Discount columns
* Inconsistent text casing and formatting across customer, location, category, and status fields
* Mixed and non-uniform date formats in the Order Date and Ship Date columns
* Fully duplicate rows
* Repeated Order IDs
* Discount values entered as negative numbers
* Shipping records where the Ship Date preceded the Order Date
* Transactions marked as Cancelled, Returned, Failed, or Refunded that needed special treatment
* Discrepancies in Sales and Profit calculations

---

## Cleaning Actions Performed

### Text Standardization
The following fields were cleaned and brought to a consistent format:

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

Techniques applied:

* TRIM
* PROPER
* SUBSTITUTE
* Find and Replace
* Standardized naming conventions

### Date Cleaning
Both Order Date and Ship Date columns were processed as follows:

* Reformatted to a uniform date structure
* Reviewed for readability and consistency
* Used to derive the Shipping Delay Days metric

Additional checks carried out:

* Detection of missing dates
* Detection of invalid dates
* Calculation of shipping delay duration
* Identification of cases where Ship Date came before Order Date

### Duplicate Handling
Duplicates were analyzed through:

* Full row-level comparison
* COUNTIF-based analysis on Order IDs

Findings:

* Exact Duplicate Rows Identified: 20
* Duplicate Order IDs Identified: 31

No records were automatically deleted from the cleaned dataset.
Duplicate Order IDs have been marked for manual review.

---

## Business Rules Applied

**Missing Region**
* Records with missing Region: 26
* Action: Replaced with "Unknown"

**Missing Ship Mode**
* Records with missing Ship Mode: 22
* Action: Replaced with "Unknown"

**Missing Discount**
* Records with missing Discount: 18
* Action: Set to 0 where other sales data was present and valid

**Negative Discount**
* Records with negative Discount values: 16
* Action: Flagged as Invalid

**Invalid Shipping Records**
* Ship Date before Order Date: 453
* Action: Flagged as Invalid Shipping Records

**Order Status Handling**
* Cancelled Orders: 146
* Returned Orders: 164

**Payment Status Handling**
* Failed Payments: 69
* Refunded Payments: 72

Cancelled and Failed transactions have been excluded from completed sales reporting.
Refunded transactions are tracked separately for business review purposes.

---

## Calculated Columns Created
The following new fields were added to the dataset:

* cleaned_discount
* calculated_sales
* calculated_profit
* profit_margin
* shipping_delay_days
* order_month
* order_year
* data_quality_flag

---

## Records Flagged
Records were marked for the following reasons:

* Negative discount values
* Invalid shipping date sequences
* Missing region information
* Missing ship mode information
* Duplicate Order IDs
* Mismatches between calculated and recorded Sales/Profit values

---

## Assumptions Made

* Records without a Region value were categorized as Unknown
* Records without a Ship Mode value were categorized as Unknown
* Missing Discount values were treated as 0 when relevant sales data was available
* Negative discount values were considered data errors
* Duplicate Order IDs were not auto-deleted, as they may reflect legitimate business scenarios

---

## Limitations

* Duplicate Order IDs need manual business review before any final decisions
* Invalid shipping records may be the result of data entry errors in the source system
* Sales and profit mismatch analysis depends on the calculation logic used in the source system
* Data quality checks were limited to the fields available in the dataset

---

## Final Outcome
The dataset was fully cleaned, validated, standardized, and enhanced with derived fields to support business analysis and reporting. The resulting cleaned dataset was used to produce data quality summaries and pivot-based business reports.

