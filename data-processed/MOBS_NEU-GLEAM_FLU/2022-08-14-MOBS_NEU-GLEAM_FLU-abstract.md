# Summary of Results
The impact of the flu season varies considerably across scenarios. In all cases the number of hospitalizations is consistently higher than in the last season. We see from a three-fold to a 20-fold increase of the peak  hospitalization at the national level. Given a specific Reff, the residual immunity and the vaccine coverage and efficacy are determining the impact of the flu season. The timing of the peak is also depending on the scenarios and vaccine coverage and efficacy appear to be important in avoiding an early peak. Confidence interval are very wide as it is not yet possible to calibrate the model on early seasonal data ato narrow down the priors of several key parameters. 

# General Model Description
We use a stochastic, data-driven metapopulation model with mobility and introductions of infected/exposed individuals. The model is age structured, and works at the resolution of roughly 400 subpopulations that are aggregated in order to provide state level results. We use a natural history of the disease with infectious and asymptomatic individuals, and a specific compartmentalization for vaccinated individuals. 

# Explanation of observed dynamics given model assumptions
We find that prior immunity and vaccine coverage/VE are determining the observed dynamics according to expectations, ordering scenarios A,B, C, D as expected in terms of season burden. 

# Model Calibration
We use historical data and parameters for the model’s priors. We use the current hospitalizations data to generate an offset baseline hospitalization and death baseline level.

# Model Assumptions
## Immunity assumptions
According to the Hub guidance

### Number/type of immune classes considered
Two immune classes (with without vaccine)

### Initial proportion of population with residual immunity from previous infections and previous seasonal vaccinations (by age, if available)
According to the Hub directions for the four scenarios.

### Waning immunity throughout the season (yes, no, differs for vaccination and natural infection)
The model does not consider waning in this version.

## Details on Influenza Strain(s)
### Number of strains/subtypes included in model
One strain.

### Strain(s) specifications (immune escape, transmissibility)
We assume full cross-immunity from prior infection. Transmissibility explores a prior according to https://bmcinfectdis.biomedcentral.com/articles/10.1186/1471-2334-14-480

### Are interactions between strains/subtypes implicitly modeled?
NA

## Seasonality implementation
We use seasonal modulation of transmissibility. School calendars are also included in the model.

## Initial Conditions
### Details on circulating strains at the start of the projection period
We assume the introduction of the new strain according to the Hub Directions (seeding into the US with 50 infections per week for 16 weeks starting August 14, 2022)

## Non-pharmaceutical interventions (NPIs)
We do not consider changes to the status quo.

## Age Group Variability
### No of age groups
We consider age groups according to the Hub directions and the model is age stratified (0-4, 5-17, 18-49, 50-64, and 65+)

### Age-stratification differences (susceptibility, vaccine effectiveness, waning)
This version of the model does consider differences in the recovery time, hospitalization rates across ages.

## State-level Variability
### State-stratification details (prior immunity, vaccine coverage)
Contact matrices and age stratification is state dependent (https://www.nature.com/articles/s41467-020-20544-y )

## Vaccine Effectiveness
### VE against infection (by age, if relevant)
We assume it is ⅔ of the effectiveness versus hospitalization.

### VE against mortality (by age, if relevant)
According to the Hub directions

### VE against transmission (by age, if relevant)
Not considered explicitly

## Other Model Assumptions
We include asymptomatic individuals, different levels of mobility/traveling for infectious individuals. 
