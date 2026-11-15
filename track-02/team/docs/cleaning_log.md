# Cleaning Log

Written by `01_cleaning.ipynb`. Rerun the notebook to update it.

| Dataset | Rule | Reason | Records before | Records after | Records affected |
|---|---|---|---|---|---|
| D1 | Drop duplicate ids | Each patient should appear once | 70,000 | 70,000 | 0 |
| D1 | Drop rows identical to an earlier row in every column except id | A match on age to the day and every measurement is very unlikely by chance, so these look like double entries (first copy kept) | 70,000 | 69,976 | 24 |
| D1 | Keep ap_hi between 70 and 250 | Systolic below 70 mmHg is shock-level and above 250 is beyond recorded clinical extremes; values like 16,020 or -150 are entry errors | 69,976 | 69,747 | 229 |
| D1 | Keep ap_lo between 40 and 150 | Diastolic outside 40-150 mmHg is not compatible with an outpatient reading; values like 1,000 look like an extra zero | 69,747 | 68,730 | 1,017 |
| D1 | Keep height between 120 and 220 | Adult heights outside 120-220 cm are extremely rare; values like 55 cm are entry errors | 68,730 | 68,680 | 50 |
| D1 | Keep weight between 30 and 200 | Under 30 kg is implausible for an adult at a check-up; 200 kg is the file maximum and physically possible | 68,680 | 68,674 | 6 |
| D1 | Keep rows where systolic > diastolic | Systolic is always higher than diastolic | 68,674 | 68,586 | 88 |
| D1 | Keep BMI between 14 and 60 | Height and weight can each look plausible but combine into an impossible body; BMI under 14 or over 60 is treated as an entry error | 68,586 | 68,557 | 29 |
| D2 | Drop duplicate patient ids | Each record should appear once | 8,763 | 8,763 | 0 |
| D2 | Drop rows where blood pressure is not in 'number/number' form | Cannot be split | 8,763 | 8,763 | 0 |
| S1 | Move label rows into a section column | Section headings and footnotes are not data rows | 30 | 27 | 3 |
