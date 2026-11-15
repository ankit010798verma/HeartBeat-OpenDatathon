# Women's Heart Risk Starts Later, Then Climbs Faster

**In records from nearly 69,000 adults, women were less likely than men to have heart disease in their 40s but caught up by about age 57. High blood pressure stood out as the clearest warning sign at every age.**

By Masoumah Haidari, Aryana Hou, Sara Sultani and Patrick Verma (Team HeartBeat) · OpenBio 2026 Datathon, Track 2: Cardiovascular Health in Women

> This article describes a student data analysis. It is not medical advice, a diagnostic tool or clinical guidance.

![Line chart of the share of people with cardiovascular disease by age, for women and men. Both lines rise with age. The women's line starts below the men's, crosses it at about age 57, and ends above it.](../figures/headline.png)

*Figure 1. The share of people with cardiovascular disease at each age, for women (green) and men (grey). Lines come from a statistical model, and the shaded bands show its uncertainty (95% confidence intervals). Dots are the observed share in each age group. Women start lower, but their line climbs more steeply and crosses the men's at about age 57. (Source: our analysis of the Cardiovascular Disease Dataset, n = 68,557.)*

## Introduction

Cardiovascular disease, or CVD, covers diseases of the heart and blood vessels, including heart attacks and strokes. It is the leading cause of death for women, yet it is still often thought of as a man's problem, and women remain under-studied. A [2025 review of more than 1,000 heart trials](https://www.cedars-sinai.org/newsroom/few-women-participate-in-studies-for-common-cardiac-conditions/) found that women made up only about 41% of participants, and fewer than their share of patients in trials of coronary heart disease and stroke.

The years leading up to menopause are a time of rising heart disease risk for women, as hormones, body fat, cholesterol and blood vessels all change. If women's risk really does accelerate in midlife, then *when* women get attention for heart health matters as much as whether they do.

So we asked the question, **does the chance of having CVD rise more steeply with age in women than in men, and does that difference remain once we account for blood pressure, cholesterol, blood sugar, body size and lifestyle?** Along the way we looked at which risk factors matter most for women of the same age, whether those factors carry the same weight before and after 55, and how women's heart disease differs between rich and poor countries.

## The Data and Our Methods

Our main source is the [Cardiovascular Disease Dataset](https://www.kaggle.com/datasets/sulianova/cardiovascular-disease-dataset), 70,000 medical exam records with age, sex, height, weight, blood pressure, cholesterol and glucose levels, self-reported smoking, drinking and exercise, and whether the person has CVD. We removed 1,443 records (2%): 24 double entries and the rest with physically impossible values, such as a blood pressure of 11,000, and documented every rule in our [cleaning log](cleaning_log.md). We used **logistic regression**, a standard method for estimating how the chance of a yes-or-no outcome changes with each factor, and checked our main result nine different ways. Three limits were noted throughout. About half of the people in this dataset have CVD, far more than in the general population, and the source does not say where or how they were chosen, so percentages describe this group, not all adults. Every measurement was taken at a single visit, so we can see associations but not which came first. And the data cover ages 39 to 65 and record sex only as female or male. For the global picture we used published country-level tables from [Li et al. (2025)](https://pmc.ncbi.nlm.nih.gov/articles/PMC12237364/), based on Global Burden of Disease estimates. A third, computer-generated dataset was also provided; we tested it and found that no model could predict its outcome better than chance, so we did not use it.

## What We Found

### Women start lower, then catch up

In their early 40s, about 28% of women in the data had CVD, compared with about 32% of men. In the late 40s the gap was similar: 41% against 46%. Then it closed. In the 55 to 59 age group the two were level at about 56%, and among people aged 60 to 65, women were *more* likely than men to have CVD, at about 68% against 65%. Our model places the crossover at about age 57, and we are 95% confident it falls between 56 and 59 (Figure 1).

To put a number on how fast risk climbs, we use **odds**: the chance something is true divided by the chance it is not. An **odds ratio** compares two odds. An odds ratio of 1 means no difference; 1.5 means the odds are 50% higher. Each odds ratio comes with a **95% confidence interval**, the range of values consistent with the data. If that range does not include 1, the data rule out "no difference" with reasonable confidence.

For each additional decade of age, women's odds of having CVD rose by about 73% (odds ratio 1.73, 95% confidence interval 1.67 to 1.79), compared with about 54% for men (1.54, 1.48 to 1.61). These numbers already account for blood pressure, cholesterol, glucose, body mass index (BMI, a measure of weight relative to height), smoking, drinking and exercise. Put differently, women's odds climbed about 12% faster per decade than men's (95% confidence interval 6% to 18%).

**Each decade of age was linked to a 73% rise in women's odds of having heart disease, compared with 54% for men.**

### Blood pressure and cholesterol rise faster in women, too

Part of the story shows up in the risk factors themselves (Figure 2). From the early 40s to the early 60s, women's average systolic blood pressure (the top number in a reading) rose by about 12 points, compared with about 8 for men, so by their 60s women had nearly caught up. The share of women with high cholesterol rose by about 18 percentage points, against about 14 for men.

![Two line charts by age for women and men. Left: average systolic blood pressure rises with age, starting lower for women and nearly meeting men's by the early 60s. Right: the share with above-normal cholesterol rises with age, faster for women.](../figures/risk_factors_by_age.png)

*Figure 2. Average systolic blood pressure (left) and the share with above-normal cholesterol (right) at each age, with 95% confidence intervals. Both rise faster in women than in men. (Source: our analysis of the Cardiovascular Disease Dataset.)*

Before accounting for any risk factors, women's odds rose about 21% faster per decade than men's. After accounting for them, the gap shrank to about 12%, but it did not disappear. Measured risk factors explain some of women's steeper climb, not all of it. We think menopause may be part of the reason. The [American Heart Association](https://www.ahajournals.org/doi/10.1161/CIR.0000000000000912) identifies the years around the final menstrual period as a time when cardiovascular risk factors can accelerate. In the [Study of Women's Health Across the Nation](https://pmc.ncbi.nlm.nih.gov/articles/PMC2727246/), cholesterol levels rose most in late perimenopause and early postmenopause (the last years before periods stop and the first years after), even after accounting for age. Another study following the same group of women found that [fat gain sped up and lean muscle declined](https://doi.org/10.1172/jci.insight.124865) around the transition, even though the rate of weight gain did not change. A third found that [arterial stiffness increased particularly rapidly](https://pmc.ncbi.nlm.nih.gov/articles/PMC7101253/) near the final menstrual period. These changes offer a plausible explanation for some of the midlife pattern we see. But our records do not say who had reached menopause or measure hormones, so we cannot show that menopause caused our crossover at about 57. The AHA also notes that increases in blood pressure are more closely tied to aging than to menopause itself.

When we adjusted for the fact that women and men in the data have slightly different age mixes (age standardization), the overall share with CVD was nearly identical at about 49% of women and 50% of men. Women's lower rates when younger and higher rates when older simply cancel out. The same age-standardized comparison showed clear differences in risk factors. Women were less likely than men to have blood pressure of 140 or above (26% against 29%), but more likely to have high cholesterol (26% against 23%) and much more likely to have obesity (30% against 20%).

**Averaged over all ages, women and men look the same but differ in when the risk arrives.**

### What matters most for women of the same age

Because older people have both more disease and higher readings, a factor can look important just because it is more common with age. To avoid that, we compared women only with other women of the same age.

High blood pressure stood out. Among women in the same five-year age group, those with systolic pressure of 140 or more had about 7.5 times the odds of having CVD as women with lower readings. High cholesterol came next (about 2.4 times the odds), followed by obesity (about 1.9) and high glucose (about 1.6). Women who reported being physically active had somewhat lower odds (about 14% lower). Smoking and drinking showed no link either way, which most likely reflects how few women reported them (about 2%) and the possibility that people quit after a diagnosis.

Figure 3 shows a lesson in how adjustment can change a result. Hollow dots compare women of the same age only; solid dots also account for every other factor at once.

![Chart of odds ratios for nine risk factors in women, each shown twice: adjusted for age only (hollow) and adjusted for all factors (solid). Most solid dots sit a little closer to 1. High glucose moves from above 1 to below 1.](../figures/age_adjusted_vs_full.png)

*Figure 3. Odds ratios for CVD in women, adjusted for age only (hollow dots) and for age plus all other factors (solid dots), with 95% confidence intervals on a log scale. Dots to the right of the dashed line mean higher odds. Blood pressure barely changes; glucose flips. (Source: our analysis of the Cardiovascular Disease Dataset.)*

With only age taken into account, very high glucose was linked to about 1.6 times the odds of CVD. Once cholesterol was added, it appeared to lower the odds. However, that does not mean high blood sugar protects the heart. In this data, high glucose and high cholesterol often occur together, so once one is in the model, the two compete to explain the same people. Blood pressure, by contrast, barely changed (about 1.9 times the odds per 10 points of pressure with age alone, 1.8 with everything), meaning its link to CVD does not depend on the other factors.

Blood pressure also carried most of the predictive power. We measured this with the AUC, the chance that a model ranks a randomly chosen woman with CVD above one without it (0.5 is a coin flip, 1 is perfect), always testing on women the model had not seen. Age and blood pressure alone scored 0.78; adding everything else only nudged it to 0.79.

### Do risk factors matter less after 55?

At first glance, yes (Figure 4). For women under 55, each 10-point rise in systolic pressure went with about 2.1 times the odds of CVD; for women 55 and over, about 1.6 times. Cholesterol and BMI weakened in the same way.

![Chart comparing odds ratios for nine risk factors in women under 55 (orange) and women 55 and over (green). Blood pressure and cholesterol have smaller odds ratios in the older group.](../figures/women_before_after_55.png)

*Figure 4. Odds ratios for CVD in women under 55 (orange) and 55 and over (green), with 95% confidence intervals on a log scale. Blood pressure and cholesterol have weaker links in older women. (Source: our analysis of the Cardiovascular Disease Dataset.)*

Men showed exactly the same weakening, and a formal test found no difference between the sexes, so this is a general pattern of aging, not something specific to women. Additionally, it reflects a rising baseline instead of blood pressure becoming harmless. Among women recorded at a high reading of 140, about 82% had CVD in both age groups. What changed was the comparison group. Among women at a normal reading of 120, about 28% of younger women had CVD, compared with about 49% of older women. When more women with normal readings already have the disease, the relative difference shrinks, even though high blood pressure is linked to an equally high absolute rate.

**Among women with a blood pressure reading of 140, about 8 in 10 had heart disease, whether they were under 55 or over.**

### Checking our work

Every analysis involves judgment calls, such as where to draw the line between a real blood pressure reading and a typing error. To make sure our main result did not depend on those calls, we reran it nine different ways (Figure 5) using stricter and looser cleaning rules, correcting obvious typos instead of removing them, letting blood pressure and age affect risk along curves instead of straight lines, accounting for the bottom blood pressure number, allowing every factor to differ by sex, and leaving out the youngest group.

![Chart showing the main result under nine versions of the analysis. Every estimate falls between about 1.12 and 1.21, and every confidence interval stays to the right of 1.](../figures/sensitivity.png)

*Figure 5. How much faster women's odds of CVD rise per decade compared with men's (a ratio of odds ratios, where 1 would mean no difference), under nine versions of the analysis, with 95% confidence intervals. The result holds in every version. (Source: our analysis of the Cardiovascular Disease Dataset.)*

In every version, women's odds rose faster with age than men's, with estimates between 12% and 21% faster per decade. The caveat is that the 2% of records we removed were more likely to belong to people with CVD (about 74%, against 50% of those kept), mostly because they were mistyped high blood pressure readings. The version that corrects those typos instead of removing them gives the same answer.

### The global picture

Our individual-level data come from one unknown population, so we also looked at country-level estimates for 204 countries and territories. 

We compared each country's socio-demographic index (SDI), a score from 0 to 1 combining income, education and birth rates, with how often women there develop CVD, adjusted for differences in age mix. A country's development level told us almost nothing about how *often* women developed CVD in 2019. The **R²** value, which describes the share of the differences between countries that development explains, was close to zero. But development level did predict the trend (Figure 6, left). From 1990 to 2019, women's CVD rate fell in about three in four countries (150 of 204) and rose in 35, and the declines were steepest in the most developed countries (R² = 0.27).

![Two charts. Left: scatter plot of 204 countries, with development level on the horizontal axis and yearly change in women's CVD rate on the vertical axis; a downward-sloping line shows that more developed countries saw bigger declines. Right: deaths per new CVD case in women for five development levels in 1990 and 2019; all fell, and the high-development group is far lower than the rest.](../figures/global_context.png)

*Figure 6. Left: each dot is a country, comparing its 2019 development level with the average yearly change in women's CVD rate from 1990 to 2019, with a fitted line and 95% confidence band. Right: deaths per new case of CVD in women, by development level, in 1990 (grey) and 2019 (green). (Source: our analysis of tables from [Li et al., 2025](https://pmc.ncbi.nlm.nih.gov/articles/PMC12237364/), based on Global Burden of Disease estimates.)*

Once CVD occurs, it is also deadlier for women in less developed regions (Figure 6, right). In 2019 there were about 0.43 deaths for every new case in the lowest-development regions, against about 0.19 in the highest. Every group improved since 1990, but the gap between the top and bottom grew wider. One possible explanation is access to the kind of measurement and treatment our individual-level results point to, like blood pressure, the strongest warning sign in our data.

## Unanswered Questions

The biggest open question is why women's risk climbs faster. The timing points toward menopause, but without data on menopause, hormones or medication, we cannot test that, and measured risk factors explain only part of the pattern. We also cannot say what happens after 65, where the data stop, or whether the crossover would appear in a more representative group, since we do not know where these patients came from or why half of them have CVD. Because everything was measured at one visit, we cannot tell whether high blood pressure came before the disease or after it, or whether treatment changed people's readings. Finally, the global trends tell us where women's heart health is improving but not why, and the data say nothing about people outside the two recorded sex categories.

## Conclusions, Limitations and Next Steps

In this dataset, women were less likely than men to have heart disease in their 40s, but their risk rose faster with every decade, drawing level by about age 57 and pulling ahead after that. The pattern held after accounting for the usual risk factors and survived every check we ran. Among women of the same age, high blood pressure stood out as the strongest warning sign, and it was linked to an equally high rate of disease before and after 55. Averaged across all ages, women and men looked the same, which is exactly how a midlife shift in women's risk could be overlooked.

These findings come with real limits. They are associations from a single visit, not proof of cause. Because each person was seen once, "risk rising with age" really compares different people of different ages; it does not follow the same women as they grow older, and people born in different decades may differ in other ways. The people in the data are not a random sample, so the percentages apply to this group only. Self-reported habits, especially smoking and drinking among women, are unreliable here. And the global results describe countries, not individual women.

With more time, we would look for data that follows the same women over many years and records menopause, medication use and hormone levels, to test whether the menopause transition explains the crossover. We would also extend the analysis beyond age 65, repeat it in a population with known origins, and estimate absolute risk (the chance of developing CVD over a period of time), which is more useful to patients than odds ratios. At the global level, linking country trends to measures of blood pressure control could show whether better access to care helps explain why women's heart disease fell faster in some places than others.

## Data and Code

- Repository, with notebooks that reproduce every number and figure: [github.com/ankit010798verma/HeartBeat-OpenDatathon](https://github.com/ankit010798verma/HeartBeat-OpenDatathon/tree/main/track-02/team)
- [Cardiovascular Disease Dataset](https://www.kaggle.com/datasets/sulianova/cardiovascular-disease-dataset) (Kaggle)
- Li et al., *Medicine* (2025), Supplementary Tables S1 and S2: [article on PubMed Central](https://pmc.ncbi.nlm.nih.gov/articles/PMC12237364/)
- [Heart Attack Risk Prediction Dataset](https://www.kaggle.com/datasets/iamsouravbanerjee/heart-attack-prediction-dataset) (Kaggle; synthetic, checked but not used)
- Full cleaning rules and record counts: [cleaning_log.md](cleaning_log.md)

## Acknowledgements

We thank the organizers and mentors of the Harvard Undergraduate OpenBio 2026 Datathon for preparing the data and guides, and the Harvard Undergraduate Data Project for the article guidelines this piece follows.

---

*This project is a student data analysis for the OpenBio 2026 Datathon. It is not medical advice, a diagnostic tool or clinical guidance. Country-level findings do not describe individual people.*
