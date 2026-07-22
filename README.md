# Data access and reconstruction

The large source and tract-level analytic files are not committed to this GitHub repository. They can be reconstructed by running the notebooks in order.

## Source datasets

1. **CDC PLACES 2025 release**  
   Census-tract estimates of diagnosed diabetes prevalence and relevant geographic fields.

2. **2023 Census Local Air Conditioning Estimates**  
   Tract-level estimates of occupied housing units without air conditioning, incorporated into the cleaned PLACES–LACE input file used by this project.

3. **2023 American Community Survey 5-year estimates**  
   Population, poverty, median household income, renter occupancy, no-vehicle access, and age 65 years or older.

4. **Daymet V4**  
   Daily maximum temperature for 2019–2023, processed through Google Earth Engine to calculate mean annual tract-level days at or above 90°F and 95°F.

## Files generated locally

Running the notebooks creates files such as:

```text
data_raw/national_places_lace_clean.csv
data_raw/acs_2023_raw.csv
data_raw/tract_heat_daymet_2019_2023.csv
data_clean/acs_2023_clean.csv
data_clean/national_analysis_merged.csv
data_clean/national_analysis_ready.csv
```

These files are excluded through `.gitignore` because they are large and/or derived from external sources. A versioned archive can be deposited in Zenodo or another research repository, subject to the source datasets' redistribution terms.

## Census API key

A Census API key is optional in the provided notebook. Press Enter at the prompt to use unauthenticated requests. A key is helpful for reliability when making many requests.

## Privacy

All data are aggregate census-tract estimates. No individual-level or protected health information is included.
