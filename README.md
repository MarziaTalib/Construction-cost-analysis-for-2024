# Construction-cost-analysis-for-2024

## Overview

This report documents the data analysis performed on unit prices extracted from the 2024-Weighted-Average-Item-Price-Report and analyzed in the Unit Prices sheet. The goal was to extract, organize, and calculate weighted average prices while ensuring proper logic for cost assignment based on specific conditions.

In this project, Microsoft Excel was leveraged to efficiently analyze and extract meaningful insights from the 2024-Weighted-Average-Item-Price-Report.

## Data Sources

### Sheet 1: 2024-Weighted-Average-Item-Price-Report

Original dataset containing historical pricing data by item, region, and quarter.

#### Columns included: 
Item #, Item Description, Units, Region, Calendar Qtr, Num Of Conts, Average Qty, Total Qty, Total Dollars, Avg Award Price, Avg Low 3 Bidders.

### Sheet 2: Unit Prices

Custom sheet designed to extract, analyze, and finalize unit prices.

#### Includes two tabs:

##### Tab 1: Contains formulas for data processing.

##### Tab 2: Stores final values without formulas for reporting.

## Data Extraction & Formulas Used

Extracting Unique Items

=UNIQUE('[2024-Weighted-Average-Item-Price-Report (2).xlsx]Sheet1'!$B:$B)

Retrieves unique item names from the report.

Extracting Related Data (Item Description, Unit, Region, Quarter)

=VLOOKUP(A4,'[2024-Weighted-Average-Item-Price-Report (2).xlsx]Sheet1'!$B:$C, 2, FALSE)
=VLOOKUP(A4,'[2024-Weighted-Average-Item-Price-Report (2).xlsx]Sheet1'!$B:$D, 3, FALSE)
=VLOOKUP(A4,'[2024-Weighted-Average-Item-Price-Report (2).xlsx]Sheet1'!$B:$E, 4, FALSE)

Fetches relevant details such as item description, unit, and other attributes.

Cost Logic Implementation

=IF(AND(ISNUMBER(SEARCH("02", C4)), OR(D4="2024Q4", D4="2024Q3")), "Same Cost", AVERAGEIF('[2024-Weighted-Average-Item-Price-Report (2).xlsx]Sheet1'!$B:$B, A4, '[2024-Weighted-Average-Item-Price-Report (2).xlsx]Sheet1'!$J:$J))

If Region = "02" and Quarter is 2024Q3 or 2024Q4, assign "Same Cost".

Otherwise, calculate the average cost.

Averaging Costs When Required

=AVERAGEIF('[2024-Weighted-Average-Item-Price-Report (2).xlsx]Sheet1'!$B:$B, A4, '[2024-Weighted-Average-Item-Price-Report (2).xlsx]Sheet1'!$J:$J)

Computes the average price for each item.

Extracting "Same Cost" from the Report

=IF(E4="Same Cost", VLOOKUP(A4,'[2024-Weighted-Average-Item-Price-Report (2).xlsx]Sheet1'!$B:$J, 9, FALSE), "NA")

If the cost logic resulted in "Same Cost", fetches the exact cost.

Final Cost Selection

=IF(ISNUMBER(E4), E4, G4)

Ensures that only one final cost appears for each item.

Final Output (Tab 2: Unit Prices - Values Only) includes columns like ITEM #, ITEM DESCRIPTION, UNIT, UNIT COST

This tab removes formulas and retains only final computed values.

Ready for export or further analysis.

## Conclusion & Summary

Extracted and organized pricing data efficiently.

Applied logic to determine whether an item should retain the same cost or be averaged.

Finalized a clean unit price report for construction items.

Ensured structured and automated cost calculations using formulas.


This analysis helps streamline pricing decisions for procurement and bidding processes in construction projects.
