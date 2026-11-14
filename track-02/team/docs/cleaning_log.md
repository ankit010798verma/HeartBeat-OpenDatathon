# Cleaning Log

Written by `01_cleaning.ipynb`. Rerun the notebook to update it.

| Dataset | Rule | Reason | Records before | Records after | Records affected |
|---|---|---|---|---|---|
| D1 | Drop duplicate ids | Each patient should appear once | 70,000 | 70,000 | 0 |
| D1 | Keep women only | Track focus on women | 70,000 | 45,530 | 24,470 |
| D1 | Keep ap_hi between 70 and 250 | Exclude implausible systolic blood pressure values while retaining severe hypertension. | 45,530 | 45,379 | 151 |
| D1 | Keep ap_lo between 40 and 150 | Exclude implausible diastolic blood pressure values while retaining severe hypertension. | 45,379 | 44,775 | 604 |
| D1 | Keep height between 120 and 210 | Exclude extreme adult heights likely to reflect measurement or entry errors. | 44,775 | 44,741 | 34 |
| D1 | Keep weight between 30 and 250 | Exclude extremely low body weights while retaining high weights. | 44,741 | 44,738 | 3 |
| D1 | Keep rows where systolic > diastolic | Systolic is always higher than diastolic | 44,738 | 44,690 | 48 |
