# Team HeartBeat: Women's Heart Disease Risk Catches Up With Age

OpenBio 2026 Datathon, Track 2: Cardiovascular Health in Women

> This project is a student data analysis. It is not medical advice, a diagnostic tool or clinical guidance. Country-level findings from Dataset 3 do not describe individual people.

## Team HeartBeat

- Masoumah Haidari
- Aryana Hou
- Sara Sultani
- Patrick Verma

## Research Question

Among about 68,000 adults aged about 40 to 65 in Dataset 1, does the chance of having cardiovascular disease rise more steeply with age in women than in men, and does that difference remain after accounting for blood pressure, cholesterol, glucose, BMI and lifestyle?

## Datasets Used

- [x] Dataset 1: Cardiovascular Disease Dataset (main analysis)
- [ ] Dataset 2: Heart Attack Risk Prediction Dataset (synthetic). Checked but not used: no model predicts its outcome better than chance (02, appendix)
- [x] Dataset 3: Global CVD in Women, Tables S1 and S2 (country-level context)

## How to Run

1. Clone the repository: `git clone https://github.com/ankit010798verma/HeartBeat-OpenDatathon.git`. The raw files are already in `track-02/data/`. On Google Colab, the first cell of each notebook clones the repository for you, so there is nothing to upload.
2. Install packages (from `track-02/team/`): `pip install -r requirements.txt`
3. Run `notebooks/01_cleaning.ipynb`, then `notebooks/02_analysis.ipynb`, top to bottom. Random seeds are fixed, so every run gives the same numbers. Notebook 02 takes about a minute because of the bootstrap confidence intervals. Last run end to end with Python 3.14, pandas 3.1, statsmodels 0.15, scikit-learn 1.9 and matplotlib 3.11.

## Files

| Path | Contents |
|---|---|
| `notebooks/01_cleaning.ipynb` | Loads and cleans all three datasets, writes the cleaning log |
| `notebooks/02_analysis.ipynb` | Summary statistics, models, checks, sensitivity analyses and the headline visual |
| `figures/headline.png` | Headline visual: CVD by age for women and men |
| `figures/regression_curve.png` | Logistic regression curves by sex (regression graph) |
| `figures/observed_by_age_band.png` | Observed CVD rate by age group and sex |
| `figures/risk_factors_by_age.png` | Blood pressure and cholesterol by age and sex |
| `figures/forest_plot.png` | Odds ratios for each risk factor, women and men side by side |
| `figures/age_adjusted_vs_full.png` | Risk factors in women: adjusted for age only vs fully adjusted |
| `figures/women_before_after_55.png` | Risk factors in women under 55 vs 55 and over |
| `figures/model_checks.png` | ROC curve and calibration plot |
| `figures/sensitivity.png` | Main result under nine versions of the analysis |
| `figures/global_context.png` | Dataset 3: incidence trend vs development level, and deaths per new case by SDI |
| `data_clean/` | Cleaned datasets written by `01_cleaning.ipynb` (read by `02_analysis.ipynb`) |
| `docs/cleaning_log.md` | Each cleaning rule and the records affected |
| `docs/presentation-outline.md` | Script outline for the five-minute video, with every number used |
| `docs/article.md` | Science communication article, following the [HUDP article guide](https://github.com/Harvard-Undergraduate-OpenBio/openbio-datathon-2026/blob/main/docs/article-guide.md) |
| `requirements.txt` | Python packages |

## Key Findings

- **Women's odds of CVD rise faster with age than men's.** Each additional 10 years of age was associated with 73% higher odds of CVD in women (OR 1.73, 95% CI 1.67 to 1.79) and 54% higher odds in men (OR 1.54, 95% CI 1.48 to 1.61), after accounting for blood pressure, cholesterol, glucose, BMI and lifestyle. The ratio of these odds ratios was 1.12 (95% CI 1.06 to 1.18), or 1.21 (1.15 to 1.27) without adjustment.
- **Women start lower and catch up in their late 50s.** At age 50 women had lower odds of CVD than men (OR 0.89, 95% CI 0.86 to 0.92; 0.93, 0.89 to 0.97 after adjusting for risk factors). The rates cross at about age 57 (95% CI 56 to 59), and at 60-65 women's rate is higher (68% vs 65%).
- **The result is robust.** It held in all nine versions of the analysis (stricter and looser cleaning, rescuing typos, flexible blood pressure and age curves, and more), with ratios from 1.12 to 1.21. Cross-validated AUC was 0.79 for women; age and blood pressure alone reach 0.78.
- **Globally (country level),** development level was unrelated to women's CVD incidence in 2019 (R² = 0.00) but related to its trend: each 0.1 higher SDI went with a 0.15 percentage point larger yearly decline from 1990 to 2019 (95% CI 0.12 to 0.19, R² = 0.27).

## Limitations

- **Association, not causation.** Dataset 1 records risk factors and CVD at the same visit, so we cannot tell which came first. This likely explains why smoking, alcohol and very high glucose look "protective".
- **Not a random sample.** About half of the people in Dataset 1 have CVD, far more than in the general population, and the source does not say how or where they were chosen. Percentages describe this dataset only.
- **No menopause data.** The crossover age fits the timing of menopause, but Dataset 1 cannot test that link.
- **Cleaning removed a slightly higher-risk group.** The 2% of rows we removed had more CVD (74%) than those kept (50%). Sensitivity analyses that rescue or keep these rows give the same result.
- **Self-reported lifestyle and few female smokers or drinkers** (under 3% of women), so those estimates are uncertain.
- **Sex is recorded as binary**, so findings do not extend to people outside those categories.
- **Ages 39 to 65 only** (just 4 people are younger).
- **Dataset 3 is country-level** and cannot be linked to individuals (the ecological fallacy).

## Presentation

Video link: [add your unlisted YouTube link]
