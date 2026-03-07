# Notes. 1d multi method dataset

## File
- data/1d-multi-method-data.csv

## What the data represents
The dataset contains repeated AUC-ROC measurements for multiple methods. Each row corresponds to one sample measured using one method.

## Columns and types
- method: categorical label identifying the method (Proposed, Baseline 1..Baseline 9)
- value: numeric AUC-ROC measurement, expected range [0, 1]

## Key checks I will enforce in formatting
- AUC-ROC must be within [0, 1]
- method labels must be consistent (trim whitespace, consistent casing)
- no missing values in method or value

## Visualization strategy and why it is non-misleading
I will visualize each method using a distribution-based plot (boxplot plus individual points). This preserves spread and outliers, avoiding misleading mean-only summaries. The AUC-ROC axis will be fixed to [0, 1] because the metric is bounded.

## Highlight strategy (preattentive encoding)
I will highlight Proposed using high-contrast hue and thicker marks, while rendering baselines in neutral gray. Proposed will appear at the top and its median will be annotated for rapid comparison.

## AI usage
AI helped draft the workflow and propose visualization alternatives. I verified the dataset schema, enforced bounded axes, and ensured the highlight does not distort comparisons.