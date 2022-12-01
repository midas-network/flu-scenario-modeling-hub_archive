# Summary of Results
Hospitalization and death projections are provided for national and state level across five age groups. We observe that depending on the scenario, the national weekly hospitalizations could peak at around 20000 (scenario A) to nearly 8 times that magnitude (scenario D). In general, scenarios with lower prior immunity take off earlier, and result in a peak around mid December 2022. Scenarios with typical prior immunity peak around mid to late January 2023. There is significant variability in peak timing across the states. While reduction in prior immunity alone (A->B) leads to slightly higher cumulative counts than under lower vaccination coverage (A->C), for deaths and state level hospitalizations, the difference is not statistically significant. 

# General Model Description
The model is based on a synthetic contact network at state level, aggregated to county level and five age groups. Individual states are run separately at a daily resolution, and combined to create national output. Outcomes (hospitalizations and deaths) are obtained by using age specific risk ratios from historical burden estimates. The model does not include waning, and is a single-strain simulation. 

# Explanation of observed dynamics given model assumptions
Early peaks under lower prior immunity are caused by higher Rt for the same seasonal forcing schedule. Vaccine impact is also significant under such a setting due to rollout timing coinciding with the surge (around November). Peaks for scenario A are much flatter compared to scenario D due to limited availability of susceptible population from the beginning (and further accentuated by vaccine rollout).

# Model Calibration
For each region, the initial active infections are assumed to be 0.01% and distributed among exposed & infectious disease states equally. Common seasonal forcing schedule is assumed across all states. Baseline transmissibility is calibrated per state to achieve overall attack rate in the range of 8-25%. 

# Model Assumptions
## Immunity assumptions
### Number/type of immune classes considered
The model contains one fully susceptible class, and two fully immune classes (V and R). The vaccine is implemented as an all-or-nothing vaccine. 

### Initial proportion of population with residual immunity from previous infections and previous seasonal vaccinations (by age, if available)
Initial immunity is set at 33% for the optimistic immunity scenarios (A and C), and 16.5% for the pessimistic scenarios (B and D). No age stratification is assumed. 

### Waning immunity throughout the season (yes, no, differs for vaccination and natural infection)
No waning immunity is considered

## Details on Influenza Strain(s)
### Number of strains/subtypes included in model
The model assumes single-strain dynamics.

### Strain(s) specifications (immune escape, transmissibility)
N/A (see Model calibration for transmissibility)

### Are interactions between strains/subtypes implicitly modeled?
N/A

## Seasonality implementation
Seasonal forcing timing is common across all states, and uses a cosine function with 50% increase at peak compared to baseline transmissibility. Peak timing is set to first week of January, with winter effects playing out from late October to late March. 

## Initial Conditions
### Details on circulating strains at the start of the projection period
Single strain model. No specific strain/subtype (A(H1/H3),B) assumed. 

## Non-pharmaceutical interventions (NPIs)
No NPIs considered. 

## Age Group Variability
### No of age groups
Five age groups: 0-4, 5-17, 18-49, 50-64, and 65-130.

### Age-stratification differences (susceptibility, vaccine effectiveness, waning)
Each age group has varying outcome risk ratios based on past burden estimates. Further the vaccine update is heterogeneous, as suggested by the schedules. No stratification in vaccine effectiveness or baseline susceptibility is assumed. 

## State-level Variability
### State-stratification details (prior immunity, vaccine coverage)
No state level variability in prior immunity or seasonal forcing. Vaccine coverage heterogeneity, as suggested by the schedules. Age profiles and contact patterns are heterogeneous since they are obtained by agggregating a realistic synthetic population.  

## Vaccine Effectiveness
### VE against infection (by age, if relevant)
Same VE as against symptomatic illness and hospitalization. No age stratification assumed. 

### VE against mortality (by age, if relevant)
Same VE as against symptomatic illness and hospitalization. No age stratification assumed. 

### VE against transmission (by age, if relevant)
N/A

## Other Model Assumptions
Since the outcomes are based on burden estimates, to get reported hospitalizations, an age-stratified multiplier is used to 'undo' the under-detection correction as part of the burden pyramid model. 