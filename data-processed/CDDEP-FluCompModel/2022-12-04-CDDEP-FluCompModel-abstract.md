# Summary of Results
Our results show the impact of VE depends on prior immunity. In case of the optimistic prior immunity, a lower VE did not have a significant impact on hospitalizations (scenarios A (highVE_optImm) and C (lowVE_optImm)); however, when prior immunity was assumed to be low, VE could have a significant impact (scenarios B (highVE_pesImm) and D (lowVE_pesImm)).

The timing of the peak hospitalization varies across different scenarios and age groups, from as  early as late November to January 2023. Except for scenario D, in all other scenarios, the peak for the 0-17 age group was earlier than those in other age groups.

# General Model Description
We developed an age-stratified compartmental model of influenza transmission to evaluate the potential impact of increased VE (VE defined as increased protection against either infection or only hospitalization) and prior immunity on hospitalizations and mortality in the United States. Two levels of disease severity were considered: mild infection, and severe infection which could lead to hospitalization. Correspondingly, two levels of vaccine-induced immunity were considered, namely, immunity against infection or full immunity and immunity against severe disease only (i.e., hospitalization) or partial immunity. However, due to scenario specifications, we did not consider partial immunity from vaccination. Those recover from infections (either severe or mild) gain natural immunity and are assumed to be protected for the duration of the influenza season, i.e., no possibility of reinfection during a season, while vaccine-induced immunity could wane.

# Explanation of observed dynamics given model assumptions
As we considered vaccine-induced immunity waning and given the early start of the season (before vaccination could cover as many as in the prior seasons), a sharp increase in cases followed by a slow decrease was expected. In addition, as the scenarios assume no extra protection from hospitalization from the vaccines, particularly in the 65+ age group, we expected the high VE scenarios to have marginal impacts, while a lower prior immunity (16.5% vs 33%) was expected to cause higher hospitalization rates.

# Model Calibration
We used weekly reported cases, hospitalizations, and mortality data from CDC for model calibration. We used Markov Chain Monte Carlo (MCMC) for parameter estimation. The numpyro package (python) was used for MCMC implementation.

# Model Assumptions
## Immunity assumptions
### Number/type of immune classes considered
Two types of immunity were considered: natural immunity and vaccine-induced immunity

### Initial proportion of population with residual immunity from previous infections and previous seasonal vaccinations (by age, if available)
For the pessimistic scenarios, we assumed 16.5% prior immunity in all age groups, and 33% for the optimistic scenarios.

### Waning immunity throughout the season (yes, no, differs for vaccination and natural infection)
No waning for natural immunity, and 50% drop in protection in 6 months for the vaccine-induced immunity.

## Details on Influenza Strain(s)
### Number of strains/subtypes included in model
We considered a single strain.

### Strain(s) specifications (immune escape, transmissibility)
The single strain was not particularly assumed to be able to evade immunity. Its transmissibility was estimated through the model calibrattion process.

### Are interactions between strains/subtypes implicitly modeled?
No.

## Seasonality implementation
Seasonality was not implemented in the model.

## Initial Conditions
### Details on circulating strains at the start of the projection period
Single strain.

## Non-pharmaceutical interventions (NPIs)
Not implemented.

## Age Group Variability
### No of age groups
Three age groups: 0-17, 18-64, and 65+

### Age-stratification differences (susceptibility, vaccine effectiveness, waning)
susceptibility, recovery, hospitalization rate, mortality rate, vaccination rate, vaccine coverage

## State-level Variability
### State-stratification details (prior immunity, vaccine coverage)
N/A

## Vaccine Effectiveness
### VE against infection (by age, if relevant)
Similar across age groups and as specified by the scenarios

### VE against mortality (by age, if relevant)
Same values as effectiveness against infection

### VE against transmission (by age, if relevant)
Same values as effectiveness against infection

## Other Model Assumptions
Our model accounts for wasted vaccine doses (administered to asymptomatically infected or recovered individuals). 
