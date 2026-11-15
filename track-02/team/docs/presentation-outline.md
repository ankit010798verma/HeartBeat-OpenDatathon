# Presentation Outline

Five minutes at most. Every team member appears or speaks at least once. Upload the recording to YouTube as an unlisted video and paste the link into the team README.

Numbers below come from `notebooks/02_analysis.ipynb`. Figures are in `figures/`.

## Introduction (0:00 to 0:45)

- **Research question:** Among about 68,000 adults aged about 40 to 65, does the chance of having cardiovascular disease (CVD) rise more steeply with age in women than in men, and does that difference remain after accounting for blood pressure, cholesterol, glucose, BMI and lifestyle?
- **Why it matters for women's cardiovascular health:** CVD is the leading cause of death for women, but it is often seen as a man's disease and women are under-represented in heart trials. If women's risk speeds up in midlife, *when* they get attention for heart health matters.
- **Datasets used:** Dataset 1 (Cardiovascular Disease Dataset, 70,000 exam records) for the main analysis. Dataset 3 (Global Burden of Disease tables S1 and S2, 204 countries) for global context. Dataset 2 (synthetic) was checked and not used, because no model could predict its outcome better than chance.

## Methodology (0:45 to 1:45)

- **Cleaning decisions** (`docs/cleaning_log.md`): kept women and men so men are the comparison group. Removed 24 double entries and physically impossible values: systolic outside 70 to 250, diastolic outside 40 to 150, height outside 120 to 220 cm, weight outside 30 to 200 kg, systolic not above diastolic, BMI outside 14 to 60. That removed 1,443 of 70,000 rows (2.1%), leaving 68,557.
- **Variables used or created, and how they were encoded:** age per 10 years (centred at 50), systolic blood pressure per 10 mmHg (centred at 120), BMI per 5 units (centred at 25), cholesterol and glucose as "above normal" and "well above normal" indicators against normal, and smoking, alcohol and activity as yes/no.
- **Method and why we chose it:** logistic regression for a yes/no outcome, with a sex × age interaction. The ratio of women's to men's odds ratio per decade is the main effect size. Smooth spline curves give the regression graph and the crossover age, with bootstrap confidence intervals.
- **How we checked our work:** 5-fold cross-validated AUC, a calibration plot, a flexible-age test and nine sensitivity versions (stricter and looser cleaning, rescuing typos, adding diastolic pressure, flexible blood pressure, every factor differing by sex, ages 40 and over).

## Results (1:45 to 3:45)

- **Sample size after cleaning:** 68,557 adults (44,648 women and 23,909 men), almost all aged 39 to 65.
- **Key summary statistics:** About half have CVD (49% of women, 50% of men). Under 45: 28% of women vs 32% of men. At 60 to 65: 68% of women vs 65% of men. Very few women report smoking (1.8%) or drinking (2.5%).
- **Regression graph:** `figures/regression_curve.png`. The age curves for women and men cross at about age 57 (95% CI 56 to 59).
- **Effect sizes with 95% confidence intervals:**
  - Odds of CVD per 10 years of age: women OR 1.73 (1.67 to 1.79), men OR 1.54 (1.48 to 1.61), adjusted for risk factors.
  - Ratio of those odds ratios (women ÷ men): 1.12 (1.06 to 1.18) adjusted, 1.21 (1.15 to 1.27) unadjusted.
  - Among women of the same age, systolic 140 mmHg or more goes with about 7.5 times the odds of CVD (7.1 to 7.9).
  - Sensitivity: the ratio stays between 1.12 and 1.21, with every CI above 1, in all nine versions (`figures/sensitivity.png`).
- **Model metrics:** cross-validated AUC 0.79 for women. Age and blood pressure alone reach 0.78.
- **Headline visual:** `figures/headline.png`. Women start lower and catch up in their late 50s.
- **Global context** (`figures/global_context.png`): development level does not predict how often women develop CVD (R² = 0.00) but does predict the trend: a 0.15 point larger yearly decline per 0.1 SDI (R² = 0.27). Deaths per new case in 2019: about 0.43 in low-SDI regions vs 0.19 in high-SDI regions.

## Discussion (3:45 to 5:00)

- **What the findings mean for women's cardiovascular health:** Averaged over all ages, women and men look the same. That hides a midlife shift, where women's risk climbs faster and overtakes men's around 57. Blood pressure is the clearest warning sign at every age, and it can be measured and treated.
- **Limitations:**
  - These are associations measured at a single visit, not causes.
  - The age pattern compares different people of different ages, not the same women followed over time.
  - The sample is not random, since about half have CVD.
  - There is no menopause or hormone data, so the menopause link is speculation.
  - Smoking and drinking are self-reported, and few women report them.
  - Glucose looks "protective" only because it overlaps with cholesterol.
  - The cleaning removed a slightly higher-risk group, though the sensitivity checks give the same answer.
  - Sex is recorded as binary.
  - Dataset 3 describes countries, not individuals.
- **What we would do with more time or resources:**
  - Use long-term data that follow the same women and record menopause, hormones and medication.
  - Include people over 65 and a population with known origins.
  - Estimate absolute risk over time.
  - Link country trends to blood pressure control.
- **Not-medical-advice statement:** "This is a student data analysis. It is not medical advice, a diagnostic tool or clinical guidance."

## Final Slide

- Team HeartBeat: Masoumah Haidari, Aryana Hou, Sara Sultani, Patrick Verma
- Data: Cardiovascular Disease Dataset (Kaggle, sulianova); Li et al., *Medicine* (2025), Supplementary Tables S1 and S2 (Global Burden of Disease)
- Repository: https://github.com/ankit010798verma/HeartBeat-OpenDatathon
