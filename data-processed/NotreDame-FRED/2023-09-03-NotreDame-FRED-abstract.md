# Summary of Results
We provided results for the State of Indiana. The model results suggest that scenarios with pessimistic assumptions of immunity result in the highest burden in terms of infections, hospitalizations, and deaths. A smaller difference was found between the scenarios of high (0.5) and low (0.3) vaccine efficacy. 

# General Model Description
FRED is an agent-based model developed for influenza. We have calibrated the model parameters to reproduce previous influenza seasons, using targets for hospitalizations, deaths, and infection attack rate. To update for round 3, we used data available for the current incidence of hospitalizations to fit the model. 

# Explanation of observed dynamics given model assumptions
The model was fit to the data for each scenario. Given that there is significant amount of data, the differences between the models are not as large as those observed in round #1. Changes in immunity showed a more marked difference given that it increased the amount of susceptible individuals. 

# Model Calibration
We sued the current available data on hospitalizations to calibrate the model parameters related to transmission and imports. 

# Model Assumptions
## Immunity assumptions

### Number/type of immune classes considered
Individuals were immune due to previous infection or due to vaccination.

### Initial proportion of population with residual immunity from previous infections and previous seasonal vaccinations (by age, if available)
This was set to the scenario description 

### Waning immunity throughout the season (yes, no, differs for vaccination and natural infection)
No waning throughout the season. 

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
The circulating strain was seeded in the model as 50 cases per week starting in September.

## Non-pharmaceutical interventions (NPIs)
Not implemented.

## Age Group Variability
### No of age groups
Age is explicitly included in the model. 
### Age-stratification differences (susceptibility, vaccine effectiveness, waning)
Vaccine efficacy by age was stratified based on the Scenario directions. 

## State-level Variability
### State-stratification details (prior immunity, vaccine coverage)
Only one state

## Vaccine Effectiveness
### VE against infection (by age, if relevant)
Assumed as 2/3 of VE against hospitalization

### VE against mortality (by age, if relevant)
Same as hospitalization

### VE against transmission (by age, if relevant)
Not included

## Other Model Assumptions

