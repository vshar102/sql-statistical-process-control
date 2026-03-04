# SQL Statistical Process Control for Manufacturing

## Project Overview
This project implements Statistical Process Control (SPC) using SQL to monitor and control a manufacturing process. By analyzing historical manufacturing data, it calculates acceptable statistical bounds—known as Upper and Lower Control Limits (UCL and LCL)—for the height of manufactured parts. It then identifies any points in the process that fall outside of this acceptable range. This methodical approach helps ensure products are consistently manufactured with high quality by indicating exactly when a machine process needs adjustment.

## Codebase Content
- **`notebook.ipynb`**: A Jupyter Notebook containing the core SQL analysis. The queries utilize advanced SQL window functions (such as `ROW_NUMBER()`, `AVG()`, `STDDEV()`) combined with sliding window frames (`ROWS BETWEEN 4 PRECEDING AND CURRENT ROW`) to calculate a 5-part moving average and moving standard deviation for part heights, partitioned by the machine `operator`. It computes the dynamically shifting UCL and LCL and uses nested subqueries alongside `CASE` statements to flag parts whose height violates these limits.
- **`parts.csv`**: The primary dataset comprising 500 manufacturing records. It contains the fields: `item_no`, `length`, `width`, `height`, and `operator`. The `height` and `operator` columns are the focal points of the statistical process control analysis.
- **`manufacturing.jpg`**: A supplementary image used within the notebook to visually introduce the manufacturing context.

## Key Statistical Formulas Used
The acceptable range is defined by an upper control limit (UCL) and a lower control limit (LCL). Based on a rolling window of 5 parts:
- **Upper Control Limit (UCL)**: `avg_height + 3 * (stddev_height / sqrt(5))`
- **Lower Control Limit (LCL)**: `avg_height - 3 * (stddev_height / sqrt(5))`

*Ideally, measurements should fall between these two limits. If they hit outside the limits, it triggers a boolean alert.*

## Skills Demonstrated
- Advanced SQL (Window Functions & Sliding Window Frames)
- Data Quality Monitoring & Statistical Process Control (SPC) Methodology
- Nested Subqueries / Derived Tables
- Conditional Logic (`CASE WHEN` statements)
