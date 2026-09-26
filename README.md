# MIS399_DATA
# MIS399_DATA — BGIS Workforce Optimisation Project

Data cleaning, standardisation, and linkage pipeline for Group BW1's MIS399 Applied
Business Project with BGIS. This repo holds the cleaned datasets, the merge
methodology, and the audit outputs used to produce the project's findings and
final report — not the raw client data, which stays in the team's shared
Google Drive.

## Contents

- **`Cleaned Data/`** — five cleaned source tables, each with raw values preserved
  alongside standardised fields (see methodology below):
  - `Astea_Utilisation_Data_CLEANED.xlsx` — central activity table (~434k rows)
  - `Financial_Demands_CLEANED.xlsx` — cost/price at the demand-person level
  - `Cleaned_Employee Pay Report_V3.xlsx` — Active and Inactive employee sheets
  - `Technician_Type_Costing_CLEANED.xlsx` — standard cost reference table
  - `Cleaned-Price-Book-Data.xlsx` — candidate pricing reference table
  - `MIS399_master_merged_audit.csv.gz` — the five tables joined into a single
    activity-row-level audit file (gzipped; ~200MB uncompressed, ~15MB
    compressed — read directly with `pd.read_csv(..., compression="gzip")`
    or `gunzip` first)

- **`Data_Cleaning_and_Merge_Guide.ipynb`** — the full cleaning and linkage
  notebook: standardisation functions, per-dataset cleaning steps, join key
  validation, and match-rate reporting.

## Methodology

Cleaning follows a three-stage **Detect → Standardise → Validate** approach
aligned to ISO/IEC 25012, with a **flag-don't-fix** rule: anomalies are logged
for client confirmation rather than silently corrected. Raw values are always
kept alongside standardised ones so any cleaned value can be traced back to
its source.

## Join architecture
