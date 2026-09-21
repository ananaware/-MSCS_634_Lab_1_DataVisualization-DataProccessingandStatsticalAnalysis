# MSCS 634 - Lab 1: Data Visualization, Data Preprocessing, and Statistical Analysis

## Purpose

This lab applies core data mining preparation techniques using Python in a Jupyter Notebook. The goal was to load a real dataset, explore it visually, clean and preprocess it, and calculate descriptive statistics to better understand its structure before any deeper analysis or modeling would take place.

## Dataset

The **tips dataset** was used — a real-world restaurant transaction dataset containing 244 records with columns for `total_bill`, `tip`, `sex`, `smoker`, `day`, `time`, and `size` (party size). It was chosen because it represents genuine sales/transaction data, includes a mix of numeric and categorical columns, and contains natural outliers in `total_bill`, making it well-suited for practicing the full range of preprocessing techniques covered in this lab.

## Key Insights

**Visualization:**
- `total_bill` and `tip` show a moderately strong positive correlation (~0.68 before cleaning), meaning tip amounts generally scale with bill size.
- Weekend transactions (Saturday and Sunday) have higher average bills and tips than weekday transactions, along with more extreme outliers.
- The distribution of `total_bill` is right-skewed, with most transactions falling between $10 and $20.

**Preprocessing:**
- Missing values were deliberately introduced (since the original dataset has none) to practice handling techniques: mean imputation for `total_bill`, forward fill for `tip`, and mode imputation for `size`.
- The IQR method flagged 10 transactions as outliers (all bills above ~$40), which were removed to produce a cleaner working dataset of 234 rows.
- Data reduction was demonstrated through both row sampling (70% and a fixed 100-row sample) and column elimination (dropping the `sex` column).
- Three scaling methods (Min-Max, Z-score, Decimal Scaling) were applied to `total_bill`, and the column was also discretized into Low/Medium/High spending categories.

**Statistical Analysis:**
- After outlier removal, `total_bill` has a mean of $18.75 and median of $17.49, showing a still slightly right-skewed distribution.
- The correlation between `total_bill` and `tip` dropped slightly to 0.618 after outlier removal, showing the original outliers had been inflating that relationship somewhat.

## Challenges and Decisions

- The original tips dataset contains no missing values, so missing data was intentionally injected (with a fixed random seed for reproducibility) to meaningfully practice and demonstrate missing-value handling techniques.
- A pandas version compatibility issue came up: `fillna(method="ffill")` is deprecated in newer pandas releases and was replaced with the direct `.ffill()` method.
- Outlier removal was applied only using `total_bill`, since it was the clearest and most meaningfully skewed numeric column in this dataset.
- The bin edges for discretizing `total_bill` into Low/Medium/High (0–15, 15–25, 25+) were chosen based on the observed quartiles of the data rather than arbitrary round numbers.

## Files in This Repository

- `MSCS_634_Lab_1.ipynb` — the full Jupyter Notebook with all code, outputs, and markdown explanations
- `tips.csv` — the original dataset used
- `/screenshots` — required screenshots for each lab step
- `report.pdf` — report on everything done in the file
