# Extreme Heat, Residential Air Conditioning, and Diabetes Prevalence

This repository contains the reproducible analysis materials for a national census-tract ecological study examining whether residential air-conditioning access modifies the association between extreme heat exposure and diagnosed diabetes prevalence in the contiguous United States and the District of Columbia.

## Study overview

- **Design:** National census-tract ecological analysis
- **Health outcome:** Diagnosed diabetes prevalence from the CDC PLACES 2025 release
- **Cooling exposure:** Percentage of occupied housing units without air conditioning from the 2023 Census Local Air Conditioning Estimates
- **Heat exposure:** Mean annual days with maximum temperature at or above 90°F, calculated from Daymet V4 for 2019–2023
- **Covariates:** 2023 American Community Survey 5-year tract estimates
- **Primary model:** Ordinary least squares regression with HC3 robust standard errors and state fixed effects
- **Primary sample:** 77,125 census tracts

The analysis is ecological. Results describe tract-level associations and should not be interpreted as individual-level causal effects.

## Repository structure

```text
notebooks/   Data cleaning and complete national analysis notebooks
figures/     Publication figures
models/      Plain-text regression summaries
metadata/    Analysis settings and provenance
manuscript/  Editable manuscript draft
tables/      CSV and Excel result tables
data/        Data-access and reconstruction instructions
```

## Reproducing the analysis

The notebooks are designed for Google Colab and should be run in order:

1. `notebooks/01_create_national_places_lace_clean.ipynb`
   - Upload the raw CDC PLACES census-tract file.
   - Identify and standardize tract identifiers, state/county fields, population, diabetes prevalence, and lack-of-air-conditioning estimates.
   - Export `national_places_lace_clean.csv`.

2. `notebooks/02_diabetes_heat_ac_national_analysis.ipynb`
   - Upload the cleaned PLACES–LACE file.
   - Download ACS covariates. A Census API key is optional; unauthenticated requests may be slower or rate-limited.
   - Create tract-level heat exposure using Google Earth Engine and Daymet V4.
   - Fit national, state-fixed-effects, Tennessee, Shelby County, and sensitivity models.
   - Export all figures, tables, model summaries, and the final project package.

## Data availability

Large raw and tract-level analytic datasets are intentionally excluded from GitHub. See [`data/README.md`](data/README.md) for source information and reconstruction steps. The small, publication-ready result tables are included.

## Key outputs

- `tables/national_regression_results.csv`
- `tables/sensitivity_analysis_results.csv`
- `tables/table1_descriptive_statistics.csv`
- `figures/figure1_no_ac_diabetes.png`
- `figures/figure2_heat_diabetes.png`
- `figures/figure3_heat_ac_interaction.png`
- `models/model4_state_fixed_effects.txt`

## Software

Core dependencies are listed in `requirements.txt`. Google Colab already includes several of them. Earth Engine use requires a Google account with Earth Engine access and interactive authentication.

## Citation

Citation metadata are available in `CITATION.cff`. Please cite the associated manuscript and archived release when a DOI becomes available.

## License

Code is released under the MIT License. Source datasets remain subject to the terms of their respective providers.
