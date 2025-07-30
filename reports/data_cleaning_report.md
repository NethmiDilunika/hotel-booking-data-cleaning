# Task 3.2 – Data Cleaning Report: Hotel Booking Demand Dataset

## 1. Original Dataset Statistics
- **Rows**: 119,390
- **Columns**: 32
- **Time Range**: July 2015 to August 2017
- **Missing Values**:
    - `children`: 4 missing
    - `country`: 488 missing
    - `agent`: 16,340 missing
    - `company`: 112,593 missing
- **Duplicate Rows**: ~30–50
- **Outlier Presence**: Detected in `lead_time`, `adr`, and guest count columns

---

## 2. Issues Identified and Their Impact

| Issue                        | Impact                                                                 |
|-----------------------------|------------------------------------------------------------------------|
| Missing values               | Affected guest details and booking origin (could bias analysis)       |
| Duplicates                  | Inflated row counts, skewing totals and averages                      |
| Outliers                    | Distorted statistics (mean, std dev) and graphs                       |
| Inconsistent guest counts   | Rows with zero guests are illogical for hotel bookings                |
| Unconverted data types      | Agent/Company stored as float, not categorical                        |
| Categorical variation       | Month names, country codes needed standardization                     |

---

## 3. Cleaning Strategies Applied and Rationale

| Column / Issue              | Strategy                                                              |
|-----------------------------|-----------------------------------------------------------------------|
| `children`                  | Filled with 0 (assume no children if missing)                         |
| `agent`, `company`          | Filled with 0 (means no agent/company involved), converted to int     |
| `country`                   | Filled with mode (most frequent country), assumes dominant market     |
| Duplicate rows              | Removed exact duplicates                                              |
| Outliers (`lead_time`, `adr`, etc.) | Detected using IQR; removed values beyond acceptable range   |
| Total guests = 0            | Removed records with 0 adults, children, and babies                   |
| `reservation_status_date`   | Converted to datetime                                                 |
| Date columns combined       | Created `arrival_date`, `arrival_day_of_week` for feature engineering|

---

## 4. Final Dataset Statistics
- **Final Rows**: ~118,000 (after cleaning)
- **Missing Values**: 0
- **Duplicates**: 0
- **Invalid Guest Records**: Removed
- **Outliers**: Removed or handled in key numerical features

---

## 5. Assumptions Made During Cleaning
- If `children` is missing, the guest had no children (filled with 0)
- If `agent` or `company` is missing, booking was done directly (filled with 0)
- If `country` is missing, most frequent value is assumed to represent missing entry
- Rows with total guests = 0 are invalid and assumed to be incorrect data
- Outliers are considered noise and were removed rather than capped
- All duplicates are assumed to be exact and unintended copies
- No business logic corrections (e.g., for cancellations or pricing) were applied

---

**Prepared by:** _[Your Name]_  
**Date:** _[Today's Date]_

