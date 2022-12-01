# Summary of Results
The results show the development of a flu wave whose timing and magnitude is different depending on the location. In all projections, assumptions considered in scenario D (pessimistic immunity and low vaccination coverage) caused to the highest level of hospitalizations. Scenario B was the one that caused most hospitalizations after D in most states. This suggests that the effect of pessimistic previous immunity is more significant that the impact of vaccination coverage. 

# General Model Description
We develop a new two viruses model that explicitly tracks the immunity caused by natural infections and vaccination and its impact on the average chances of infection, hospitalization and death. The model is stratified according to six age groups and considers that the hospitalization and mortality rate depends on each group susceptibility to severe disease with flu. In this mode, we consider that one virus corresponds to the circulating influenza strains in the season 2021-2022 while the other virus represents the strains that is imported starting from September 2022. Immune escape in scenarios B and D is captured by considering that immunity provided from infections with strains circulating druing the 2021-2022 season offers has only half the protection against infection with the imported strains on September 2022.

# Explanation of observed dynamics given model assumptions
The results can be explained by the higher baseline protection that previous infections offers in comparison to the protection offered by vaccines. In addition, immunity provided by vaccines wanes significantly faster than immunity gained through natural infections.

# Model calibration
We calibrated the model manually by ensuring that the peak number and timing of US hospitalizations is similar to the 2019-2020 season.

# Model Assumptions
## Immunity assumptions
### Number/type of immune classes considered
The model tracks the population-immunity levels in a continuous way. We consider three state variables corresponding to immunity gained from infection with strains circulating in 2021-2022, new strains imported starting from September 2022 and from vaccination.

### Initial proportion of population with residual immunity from previous infections and previous seasonal vaccinations (by age, if available)
According to the scenario assumptions, we consider that 33% have prior immunity from previous infections in the optimistic immunity scenarios and 16.5% have immunity in the pessimistic immunity ones. We calculate this average across age groups by considering that the most susceptible age groups have higher immunity than the less susceptible ones. Age-specific immunity from vaccination is also considered according to the data provided on vaccination coverage 

### Waning immunity throughout the season (yes, no, differs for vaccination and natural infection)
We consider that the half-life time of immune waning is 8 months following natural infection and 3 after vaccination.

## Details on Influenza Strain(s)
### Number of strains/subtypes included in model
We consider two viruses, one corresponds to the circulating strains during the 2021-2022 season and the other represents the strains imported starting from September 2022.

### Strain(s) specifications (immune escape, transmissibility)
In the pessimistic immunity scenarios (B and D), we consider that the strains imported starting from September 2022 have 50% immune escape to immunity acquired from infection with the strains circulating before September 2022.

### Are interactions between strains/subtypes implicitly modeled?
Yes.

## Seasonality implementation
We consider a 25% increase in the transmission rates during the winter season.

## Initial Conditions
### Details on circulating strains at the start of the projection period
Initially, only the virus corresponding to the strains circulating during the 2021-2022 season are present in the model.

## Non-pharmaceutical interventions (NPIs)
We don't consider any NPIs.

## Age Group Variability
### No of age groups
Six.

### Age-stratification differences (susceptibility, vaccine effectiveness, waning)
We consider that age groups determine the chances of developing severe disease against infection. They also determine initial levels of immunity from infection and vaccination.

## State-level Variability
### State-stratification details (prior immunity, vaccine coverage)
We do not consider any specific changes for each state. However, we did a pre-processing on the fitting data used for some states where we changed the values 0 with 2.

## Vaccine Effectiveness
### VE against infection (by age, if relevant)
30% in the low coverage scenarios and 60% in the high coverage scenarios.

### VE against mortality (by age, if relevant)
51% in the low coverage scenarios and 80% in the high coverage scenarios.

### VE against transmission (by age, if relevant)
N/A

## Other Model Assumptions
To calibrate the model with historic data, we increased the importation of cases from 50 cases per week to 2000.
