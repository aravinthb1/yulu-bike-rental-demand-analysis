# Yulu Bike Rental Demand Analysis

Hypothesis testing and exploratory analysis of Yulu shared electric-cycle rental data. The project examines whether rental demand varies with season, weather, and working-day status, and turns the observed patterns into operational recommendations.

## Business Objective

Yulu wants to understand factors associated with rental demand amid a reported revenue decline. This analysis studies hourly rental counts alongside calendar and weather conditions to identify demand patterns and test selected relationships.

## Business Questions

- Does average rental demand differ between working and non-working days?
- Does rental demand vary across seasons?
- Does rental demand vary across weather conditions?
- Are weather conditions distributed independently of season?
- Which conditions align with the highest and lowest observed rental counts?

## Dataset

`yulu.csv` contains **10,886 hourly observations** and 12 columns. It includes date and time, season, holiday and working-day flags, weather category, temperature, humidity, wind speed, casual and registered rentals, and total rental count. The dataset has no missing values or duplicate rows.

The notebook maps seasons to four categories and weather to four categories. Weather category 4 appears only once, so comparisons involving that category are especially uncertain. The analysis retains potential outliers as potentially genuine demand variation.

## Key Findings

- **Season:** Average hourly rental count was lowest in Spring (116.34) and highest in Fall (234.42). Summer averaged 215.25 and Winter 198.99. The notebook reports statistically significant season differences using ANOVA and Kruskal–Wallis tests.
- **Weather:** Average rental count was highest in clear conditions (205.24) and lower in mist/cloudy conditions (178.96) and light rain/snow (118.85). Weather category 4 averaged 164, but has only one observation. The notebook reports significant differences across weather groups, including when category 4 is excluded.
- **Working day:** The notebook's two-sample t-test found no statistically significant difference in mean rental count between working and non-working days (p = 0.2264).
- **Weather and season:** A chi-square test found an association between weather and season after excluding the one-observation weather category (p = 2.83 × 10⁻⁸).
- **Other patterns:** Registered-user rentals are higher on average than casual-user rentals. Temperature and feeling temperature are strongly correlated (0.98); humidity has a moderate negative correlation with total count (-0.32).

The analysis identifies associations in this dataset; it does not establish that weather or season caused the revenue decline. Several hypothesis-test assumptions are violated or limited: rental counts are non-normal, season/weather groups have unequal variances, and the observations are hourly and may be temporally dependent. Statistical significance should therefore be interpreted with care.

## Recommendations from the Analysis

- Plan seasonal promotions to help address the lower demand observed in Spring.
- Pilot weather-responsive incentives during poorer weather, measuring whether they improve rides without eroding revenue.
- Align fleet availability with higher-demand seasons, while validating capacity needs with additional operational data.
- Do not focus marketing narrowly on working-day commuters based only on this analysis; working-day status was not significant in the tested comparison.
- Gather more observations for rare weather conditions before making decisions based on those categories.

## Methods and Tools

- Python with Pandas and NumPy
- Matplotlib and Seaborn for exploratory visualizations
- Descriptive statistics and correlation analysis
- Two-sample t-test for working-day comparison
- One-way ANOVA and Kruskal–Wallis tests for season and weather comparisons
- Levene's test for variance checks and Shapiro–Wilk tests for normality checks
- Chi-square test of independence for weather and season

## Repository Structure

```text
yulu-bike-rental-demand-analysis/
├── README.md
├── Yulu.ipynb
└── yulu.csv
```

The notebook contains the analysis, visualizations, statistical tests, and recommendations. It reads `yulu.csv` as its input dataset.

## How to Review

1. Read this README for the business questions and main results.
2. Open `Yulu.ipynb` to review the analysis and visualizations.
3. Use `yulu.csv` as the notebook's input data.

## Author

**Aravinth Baskar**
