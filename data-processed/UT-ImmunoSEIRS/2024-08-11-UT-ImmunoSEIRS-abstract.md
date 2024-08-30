# Summary of Results
The results show the development of a flu wave whose timing and magnitude is different depending on the location. In all projections, assumptions considered in scenario E (low vaccination coverage and H3N2 dominant season) caused to the highest level of hospitalizations. Scenario B (high vaccination coverage and H1N1 dominant season) was the one that caused least hospitalizations at the national level and almost all states. This suggests that the effect of previous immunity respective to the strain dominant infections, transmission and severity respective to strain dominant is significantly impacting the hospitalization levels along with vaccination coverage. 

# General Model Description
We develop a new two viruses model that explicitly tracks the immunity caused by natural infections and vaccination and its impact on the average chances of infection, hospitalization and death. The model is stratified according to six age groups and considers that the hospitalization and mortality rate depends on each group susceptibility to severe disease with flu. In this mode, we consider that one virus corresponds to the circulating influenza strains in the season 2023-2024 while the other virus represents the strains that is imported starting from August 2024. For each type of immune exposure (i.e., infection with a specific subtype or receipt of vaccine), the model uses two state variables to track the resulting population-level average protection against infection and severe disease. These variables increase as individuals recover from infections and receive vaccines and they decrease according to waning (half-life) parameters, specific to each exposure type. Immunity state variables modify overall rates of infection and risk of hospitalization/death with efficacies that can vary depending on currently circulating virus subtypes and the age group of the exposed individual. Infection upregulates population immunity depending on the relative frequency of each subtype among active infections. The administration of vaccine increases vaccine-derived immunity, represented. 

# Explanation of observed dynamics given model assumptions
The results can be explained by the higher baseline protection that previous infections offers in comparison to the protection offered by vaccines. In addition, immunity provided by vaccines wanes significantly faster than immunity gained through natural infections.

# Model calibration
We firs calibrated the model manually by ensuring that the peak number and timing of US hospitalizations is similar to the 2017-2018 and 2019-20 season to cater to the scenarios. Doing so the infection hospitalization rates and in-hospital mortality rates specific to age were calibrated and fixed for each of these seasons. 

# Model Assumptions
## Immunity assumptions
### Number/type of immune classes considered
The model tracks the population-immunity levels in a continuous way. We consider three state variables corresponding to immunity gained from infection with strains circulating in 2023-2024, new strains imported starting from August 2022 and from vaccination.

### Initial proportion of population with residual immunity from previous infections and previous seasonal vaccinations (by age, if available)
According to the scenario assumptions, we consider that 33% have prior immunity from previous infections. We calculate this average across age groups by considering that the most susceptible age groups have higher immunity than the less susceptible ones. Age-specific immunity from vaccination is also considered according to the data provided on vaccination coverage 

### Waning immunity throughout the season (yes, no, differs for vaccination and natural infection)
We consider that the half-life time of immune waning is 8 months following natural infection and 3 after vaccination.

## Details on Influenza Strain(s)
### Number of strains/subtypes included in model
We consider two viruses, one corresponds to the circulating strains during the 2023-2024 season and the other represents the strains imported starting from August 2024.

### Strain(s) specifications (immune escape, transmissibility)
We consider the transmissility and severity to be higher for the 2017-2018 based scenario compared to 2019-2020 season scenario considering the calibrated infection hospitalization rates and in-hospital mortality rates. The initial immunities are estimated by fitting the model to 2023-2024 season hospital data. 

### Are interactions between strains/subtypes implicitly modeled?
Yes.

## Seasonality implementation
Yes. We incorporated seaonality by means of specific humidity specific to national and state levels. Additionally, school and work calendar along with contact matrices cater to human forced phenomenon. 

## Initial Conditions
### Details on circulating strains at the start of the projection period
Current observation of H3N2 in 2024-2025 flu season

## Non-pharmaceutical interventions (NPIs)
We don't consider any NPIs.

## Age Group Variability
### No of age groups
Six.

### Age-stratification differences (susceptibility, vaccine effectiveness, waning)
We consider that age groups determine the chances of developing severe disease against infection. They also determine initial levels of immunity from infection and vaccination.

## State-level Variability
### State-stratification details (prior immunity, vaccine coverage)
Each state calibrated their own prior immunity, with their own previous vaccine acquired immunity.

## Vaccine Effectiveness
### VE against infection (by age, if relevant)
20% in all the scenarios. 40% against hospitalization which gives 25% against hospitalization given infection.

### VE against mortality (by age, if relevant)
N/A

### VE against transmission (by age, if relevant)
N/A

## Other Model Assumptions
N/A
