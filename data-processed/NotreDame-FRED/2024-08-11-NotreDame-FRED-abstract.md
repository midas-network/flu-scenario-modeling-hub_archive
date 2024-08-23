# Summary of Results
We provided results for all states and national-level hospitalizations and deaths. The model results suggest that scenarios dominated by H3N2 peak a bit earlier (in November/December) and at a higher magnitude than scenarios dominated by H1N1. Vaccination coverage has a modest but noticeable impact on hospitalizations and deaths in most states and at the national level.

# General Model Description
FRED is an agent-based model developed for influenza. We have calibrated the model parameters (transmissibility/R_eff and age-specific hospitalization rates) to reproduce previous influenza seasons, using targets for hospitalizations, deaths, and infection attack rate. To update for round 2024/25, we specifically calibrated the model to the 2017-2018 and 2019-2020 reference seasons for the H3N2 and H1N1 scenarios respectively. The starting susceptible fraction of the population was estimated for these two years using a simple regression model that fit the yearly S_maximum values from Yang et al. (2015) to previous years ILI total and the % change in H1 strain dominance.

# Explanation of observed dynamics given model assumptions
The model was fit to the hospitalization and attack rate data for the respective H1N1 and H3N2 representative years. Given that there is significant amount of data, the differences between the models are not as large as those observed in round #1. Changes in immunity showed a more marked difference given that it increased the amount of susceptible individuals. 

# Model Calibration
We used the cumulative hospitalization rates by age group from Fluserve and the cumulative infection attack rate from 2017-18 and 2019-20 to calibrate the model parameters related to transmission. New for this round we estimated state-level imported infections in August and September of 2024 based on hospitalizations in August/September of 2023.  

# Model Assumptions
## Immunity assumptions

### Number/type of immune classes considered
Individuals were immune due to previous infection or due to vaccination.

### Initial proportion of population with residual immunity from previous infections and previous seasonal vaccinations (by age, if available)
We assumed that the residual immunity at the start of the 2024/25 season would be drawn from a Unif(0.33,0.355) distribution for H1N1 and Unif(0.32,0.345) for H3N2.

### Waning immunity throughout the season (yes, no, differs for vaccination and natural infection)
Waning of vaccine protection based on Ferdinands et al. (2017). 

## Details on Influenza Strain(s)
### Number of strains/subtypes included in model
We modeled one strain.

### Strain(s) specifications (immune escape, transmissibility)
Transmissibility was adjusted in the calibration step. Immune escape was not considered. 

### Are interactions between strains/subtypes implicitly modeled?
Not included in the model. 

## Seasonality implementation
We implemented changes in contact based on a timeseries of indoor activity from Susswein et al (2022): <https://github.com/bansallab/indoor_outdoor>

## Initial Conditions
### Details on circulating strains at the start of the projection period
The circulating strain was seeded in the model proportional to influenza hospitalization data from 2023 (assuming that all infections are due to dominant strain per scenario).

## Non-pharmaceutical interventions (NPIs)
Not implemented.

## Age Group Variability
### No of age groups
Age is explicitly included in the model. 
### Age-stratification differences (susceptibility, vaccine effectiveness, waning)
Vaccine efficacy by age was stratified based on the Scenario directions. 

## State-level Variability
### State-stratification details (prior immunity, vaccine coverage)
Used provided state-specific vaccine coverages. Assumed that prior immunity did not vary geographically.

## Vaccine Effectiveness
### VE against infection (by age, if relevant)
Assumed to be 21% for everyone (Mellis et al.), not age or strain dependent.

### VE against mortality (by age, if relevant)
Same as hospitalization

### VE against transmission (by age, if relevant)
Not included

## Other Model Assumptions
Trajectories are paired by horizon, age_group, and vaccination scenario (A/C/E paired and B/D/F paired).
