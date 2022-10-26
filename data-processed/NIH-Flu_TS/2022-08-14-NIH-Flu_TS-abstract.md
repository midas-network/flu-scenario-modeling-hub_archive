# Summary of Results
Our time series model of national hospitalizations projects epidemics of increasing size, from scenario A (optimistic immunity and high vaccination coverage) to scenario B (pessimistic immunity and high vaccination coverage) to scenario C (optimistic immunity and low vaccination coverage) to scenario D (pessimistic immunity and low vaccination coverage). All scenarios project that the peak number of hospitalizations will occur during the first week of January 2023 (median peak timing). Similar to the 2010-2011 season, Scenario A has a median peak of 5,635 admissions, with 88,234 median cumulative hospitalizations. Similar to the 2012-2013 season, Scenario B has a median peak of 16,112 admissions, with 149,121 median cumulative hospitalizations. Similar to the 2018-2019 season, Scenario C has a median peak of 14,156 admissions, with 225,144 median cumulative hospitalizations. Scenario D has a median peak of 40,850 admissions, with median cumulative hospitalizations 378,084. Scenario D's peak and cumulative hospitalizations exceed those observed during the two most severe flu seasons since the 2009 H1N1 pandemic (2014-2015 and 2017-218). 

# General Model Description
We use a dynamic harmonic regression model with ARMA errors and exogenous covariates for seasonal cumulative vaccination coverage, seasonal vaccine effectiveness, weekly A/H3N2 circulation, and weekly influenza infections. The model is trained on weekly national-level hospitalizations during the five seasons prior to the COVID-19 pandemic (2015-2016 to 2019-2020) and projects hospitalizations for the upcoming season (2022-2023) without considering flu hospitalizations observed during the 2020-2021 and 2021-2022 seasons. 

For each projection scenario (A-D), we include 2 to 3 sub-scenarios based on the epidemic sizes and timing of A/H3N2 dominant seasons during the post-2009 A/H1N1 pandemic period.

* Scenarios A and C (optimistic prior immunity) include "early","late", and "small" categories, with the early category averaging weekly infections and weekly A/H3N2 percent positive values from seasons 2012-2013 and 2014-2015, the late category averaging weekly infections and weekly A/H3N2 percent positive values from seasons 2016-2017 and 2017-2018, and the small category using weekly infections and weekly A/H3N2 percent positive values from the 2011-2012 season.

* Scenarios B and D (pessimistic prior immunity) include "early" and "late" categories, using weekly infections and weekly A/H3N2 percent positive values from the 2014-2015 and 2017-2018 seasons, respectively.

For model projections, vaccine coverage and effectiveness values were dictated by the hub. Methods for inferring weekly infections and information about initial susceptibility, historical vaccine effectiveness, and historical vaccine coverage are provided in later sections.

For each projection scenario (A-D), we provide an aggregate projection for each target (simulations from all sub-scenarios combined).

# Explanation of observed dynamics given model assumptions
The averaging of sub-scenarios leads to potentially unrealistic epidemic trajectories: high initial peak then long decline (B and D) or a long plateau after the initial peak (A and C). The inclusion of both "late" and "small" subscenarios for A and C and only "early" and "late" subscenarios for B and D likely contributes to the more prolonged epidemics observed for A and C. The inclusion of an "early" epidemic in all scenarios likely contributes to the same peak timing across A-D. More realistic epidemic shapes, sizes, and timing could be obtained by disaggregating projections by subscenario, if/when it is possible to include sub-scenario information in submission files. Or, we could limit the number of sub-scenarios or proceed with a single subscenario, if there is another round later in the flu season. Though we anticipated that prior immunity would be more impactful than vaccination, we found little difference in peak size between scenarios B and C, and C had higher cumulative hospitalizations. The high vaccination scenarios (A and B) may be overly optimistic, leading to an artificially high impact of vaccination on hospitalizations. Though the high vaccination scenarios dictate 60% VE, VE for all influenza types/subtypes combined has been less than 40% in recent flu seasons, with A/H3N2 VE typically lower than values observed for influenza B and A/H1N1. 

# Model Calibration
We used historical data on influenza hospitalizations (incidence, epidemic size, and timing), influenza-like illness rates, influenza A subtype circulation, and vaccine coverage and effectiveness to calibrate our model. We used out-of-season projections for historical seasons prior to 2020-2021 to determine the optimal training period and the number of Fourier terms to include in the model.

The HHS target dataset begins in November 2020, and hospitals were not required to report influenza hospitalizations until February 2021. We found that national [FluSurv-NET hospitalization rates](https://www.cdc.gov/flu/weekly/influenza-hospitalization-surveillance.htm) were similar to those of the HHS dataset during the season in which both datasets are available (2021-2022). Therefore, we converted weekly Flu-SurvNet rates to counts (using annual US population estimates) to serve as a historical hospitalizations dataset.

As a proxy for immunity, we included weekly influenza infections as a covariate in our model. For seasons 2010-2011 to 2019-2020, we estimated weekly influenza-like illness x percent positive values (for any flu type/subtype) using influenza syndromic and virological surveillance data provided by the [CDC FluView portal](https://www.cdc.gov/flu/weekly/fluviewinteractive.htm). To estimate weekly infections, we fit a [semi-mechanistic Bayesian epidemiological model](https://imperialcollegelondon.github.io/epidemia/) to observed ILI x % positive rates during each season, assuming a case ascertainment rate of 0.3.

Information about historical and projected vaccine effectiveness and vaccine coverage are in the "Vaccine Effectiveness" and "Other Model Assumptions" sections.

# Model Assumptions
## Immunity assumptions
### Number/type of immune classes considered
N/A

### Initial proportion of population with residual immunity from previous infections and previous seasonal vaccinations (by age, if available)
In each historical season and for optimistic immunity scenarios (A and C), the initial proportion susceptible is assumed to be 0.65 ([Yang et al. 2015](https://doi.org/10.1073/pnas.1415012112)). 

When estimating infections for pessimistic scenarios seasons (B and D), we assumed an initial susceptibility of 0.85, as dictated by the hub. We also applied a multiplier to weekly ILI x % positive cases observed in 2014-2015 and 2017-2018 to achieve a final attack rate of approximately 30%. We used the resultant amplified weekly infections as our immunity covariate in B and D scenario projections.

### Waning immunity throughout the season (yes, no, differs for vaccination and natural infection)
N/A

## Details on Influenza Strain(s)
### Number of strains/subtypes included in model
We do not train models on estimated strain or subtype-specific hospitalizations or project strain or subtype-specific hospitalizations. However, we include the proportion of samples testing positive for A/H3N2 as an exogenous covariate in model training and projections. We chose to focus on percent positive for A/H3N2 because the upcoming influenza season is expected to be A/H3N2 dominant, and A/H3N2 dominant seasons tend to be more severe than A/H1N1 dominant seasons. 

### Strain(s) specifications (immune escape, transmissibility)
N/A

### Are interactions between strains/subtypes implicitly modeled?
N/A

## Seasonality implementation
Seasonality is modeled using Fourier terms. The optimal number of Fourier terms was determined by 1) training models on historical weekly hospitalizations up to the 2019-2020 season and comparing AICc values across models with different orders of Fourier terms, and 2) conducting out-of-season projections for recent seasons prior to COVID-19 (2016-17, 2017-18, 2018-19, and 2019-20) and ranking the median out-of-season accuracy (RMSE and CRPS) of models with different orders of Fourier terms. Our final model includes 10 Fourier terms.

## Initial Conditions
### Details on circulating strains at the start of the projection period
The initial proportion of samples positive for A/H3N2 is the weekly value observed at the start of historical seasons assigned to optimistic and pessimistic immunity sub-scenarios. Observed weekly A/H3N2 percent positive values from historical seasons are used as a covariate in model projections, with the particular season(s) used depending on the sub-scenario.

## Non-pharmaceutical interventions (NPIs)
N/A. Models are trained on historical data up to the 2019-2020 season, thus we do not consider the COVID-19 pandemic period and associated NPIs. 

## Age Group Variability
### No of age groups
N/A

### Age-stratification differences (susceptibility, vaccine effectiveness, waning)
N/A

## State-level Variability
### State-stratification details (prior immunity, vaccine coverage)
N/A

## Vaccine Effectiveness
We obtained adjusted vaccine effectiveness estimates from published observational studies, the majority of which were test-negative case control design and focused on general populations or healthy adult populations in North America or Europe. See [Perofsky et al. 2020](https://elifesciences.org/articles/62955) for 1997-1998 to 2018-2019 estimates and the [CDC's influenza VE page](https://www.cdc.gov/flu/vaccines-work/past-seasons-estimates.html) for estimates from more recent seasons. 

If more than one VE study was available for a particular historical season, we calculated a seasonal weighted mean VE, with individual VE values weighted by the inverse of their 95% confidence intervals. One VE value per season was used as an exogenous covariate in model training and projections. Projections used vaccine effectiveness values dictated by the hub (0.6 for high vaccination and 0.3 for low vaccination).

### VE against infection (by age, if relevant)
N/A

### VE against mortality (by age, if relevant)
N/A

### VE against transmission (by age, if relevant)
N/A

## Other Model Assumptions
We obtained monthly vaccination coverage estimates for individuals aged 6+ months during seasons 2010-2011 to 2020-2021, from the [National Center for Immunization and Respiratory Diseases](https://data.cdc.gov/Flu-Vaccinations/Influenza-Vaccination-Coverage-for-All-Ages-6-Mont/vh55-3he6). For each historical season in the model training dataset, we use the final cumulative vaccine coverage as our vaccine coverage covariate. For projection scenarios, we use the vaccine coverage value dictated by the hub (low vaccination: 10% lower than 2020-2021, high vaccination: 10% higher than 2020-2021).
