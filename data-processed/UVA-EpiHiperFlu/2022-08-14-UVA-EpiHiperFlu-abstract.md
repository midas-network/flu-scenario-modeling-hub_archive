# Summary of Results
We provide influenza hospitalization projections for all states and the US. We find that in the pessimistic immunity scenarios (B and D), incidence hospitalizations peak earlier and higher than in the optimistic immunity scenarios (A and C). The total hospitalizations are much more in scenarios B and D than in A and C. Under either proior immunity level, hospitalizations are much more with low vaccine protection. The prior immunity axis has a larger impact than the vaccine protection axis.

The exact timing and magnitude of the peak and the start and end of the season vary across different states. But in most states, the hospitalization incidence peaks around the end of 2022 to the beginning of 2023 in scenarios A and C, and around early to middle December 2022 in scenarios B and D.

Note that the projections have larger values than that we submitted previously as a separate model (UVA-EpiHiper), but the findings about peak timing and comparison between scenarios are consistent.

# General Model Description
Our model simulates an age-stratified influenza disease in synthetic networks of the states. Simulations are calibrated and run separately for each state. We combine the outcomes of all states to get results for all of US. The simulations produce daily infection and hospitalization incidences; and each simulation runs for multiple replicates. We aggregate daily data to get weekly data and compute estimates for each target (including seasonal targets) from the multiple replicates.

Our single-strain disease model is stratified by age group, and includes symptomatic and asymptomatic states but not immune waning. We calibrate the disease model using a "typical influenza season" setting which is between scenarios A and C. For hospitalization calibration, we use pre-pandemic (seasons from 2010 to 2019) flu burden data from CDC estimates.

# Explanation of observed dynamics given model assumptions
It is expected that hospitalizations are higher with lower prior immunity and with lower vaccine protection. Since our model does not consider waning immunity, the difference in prior immunity (33% vs. 16.5% of the population) is more significant, especially in the early months of the season when current season vaccination is still low. With lower prior immunity (16.5%) the social contact network is still well-connected and the disease can spread fast before vaccination catches up. When vaccination coverage reaches a certain level, infections as well as hospitalizations start to quickly decrease, due to lack of waning.

# Model Calibration
We calibrate the disease model using a "typical influenza season" setting which is between scenarios A and C. For hospitalization calibration, we use pre-pandemic (seasons from 2010 to 2019) flu burden data from CDC estimates.

# Model Assumptions
## Immunity assumptions
### Number/type of immune classes considered
We have implemented susceptible (no immunity), vaccinated (partial immunity), and recovered (full immunity) states.

### Initial proportion of population with residual immunity from previous infections and previous seasonal vaccinations (by age, if available)
We assume that at the beginning of the projection period, either 33% or 16.5% (in either pessimistic or optimistic immunity scenarios) of the whole population have immunity from previous season.

### Waning immunity throughout the season (yes, no, differs for vaccination and natural infection)
We do not consider waning immunity.

## Details on Influenza Strain(s)
### Number of strains/subtypes included in model
We use a single strain model.

### Strain(s) specifications (immune escape, transmissibility)
Our disease model has a single strain and its transmissibility is calibrated separately for each state against final attack rate of 8% to 25%.

### Are interactions between strains/subtypes implicitly modeled?
No.

## Seasonality implementation
We implement a cosine function (Kissler et al. 2020, Science) for seasonality for the whole US, which reaches maximum around mid-January. We use it to scale transmissibility in our disease model over time.

## Initial Conditions
### Details on circulating strains at the start of the projection period
We use a single strain disease model.

## Non-pharmaceutical interventions (NPIs)
We do not consider NPIs.

## Age Group Variability
### No of age groups
Five age groups: 0-4, 5-17, 18-49, 50-64, and 65+.

### Age-stratification differences (susceptibility, vaccine effectiveness, waning)
We have different connectivities in the contact network for individuals of different age groups. We have an age group stratified disease model where hospitalization rate is different among age groups. We assume the same vaccine efficacy for all age groups.

## State-level Variability
### State-stratification details (prior immunity, vaccine coverage)
In our model, different states have different contact network structures, and are calibrated separately. The vaccine coverage is taken from the provided data so is different between states. We assume the same prior immunity in all states.

## Vaccine Effectiveness
### VE against infection (by age, if relevant)
Same as VE against illnesses and hospitalizations: 60% in high vaccine protection scenarios, 30% in low vaccine protection scenarios.

### VE against mortality (by age, if relevant)
Same as VE against illnesses and hospitalizations.

### VE against transmission (by age, if relevant)
N/A.

## Other Model Assumptions
In our disease model, for each age group we consider that an age-dependent fraction of individuals have a higher risk of hospitalization.
