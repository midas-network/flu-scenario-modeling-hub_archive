
# Summary of Results

Hospitalization and death projections were generated for both national and state levels across five age groups. The model estimates varying peak hospitalization and death rates based on scenario-specific vaccine uptake and effectiveness and strain dominance assumptions. Our findings suggest that hospitalization peaks could occur between mid-to-late December, with scenario-dependent variability. States with higher proportions of older adults, exhibit higher relative hospitalization burdens due to age-specific risks and vaccine efficacies. Our model highlights the influence of vaccination coverage and seasonal forcing on influenza dynamics.

# General Model Description

Our model employs a two-step process: (1) underlying biological processes are modeled at the state-level with an ODE, and (2) new hospitalizations at each timestep from the ODE are multiplied by age-group-weighted hospitalization and death rates to find age-stratified hospitalizations and deaths.

The ODE uses a *Susceptible-Exposed-Infectious-Hospitalized-Recovered (SEIHR)* compartmental framework to simulate influenza transmission and burden. It accounts for age- and geography-specific vaccination rates, vaccine efficacies, and historical influenza burden. The model includes seasonal forcing, with fitted parameters optimized to minimize deviation from historical hospitalization data.

The hospitalization outputs from the ODE (H<sub>geography, all_ages)</sub> are then multiplied by weighted hospitalization and death terms. The age-group-specific hospitalization risk term is taken from the CDC's end-of-season estimate for each exemplar season, and it is weighted by each state's relative population within each age group: H<sub>geography, age_group)</sub>. The sum of all  H<sub>geography, age_group)</sub> within a state equals the total ODE-predicted hospitalizations (H<sub>geography, all_ages)</sub>) at that time step. Age-stratified death rates are calculated similarly, but as a ratio of deaths/hospitalizations. To correct for the discrepancy between end-of-season estimates and real-time NHSN reporting, we included a scaling term in the age-stratified, weighted death rates to approximate NHSN reports. Only deaths are scaled in this way, because hospitalizations are a direct output of the ODE, and are therefore already calibrated to the NHSN reporting.

# Explanation of observed dynamics given model assumptions

The SEIHR model captures the interaction between vaccination rates, age-specific risks, and seasonal forcing. States with higher proportions of elderly individuals, who have increased risk of severe outcomes, experience higher relative hospitalization burdens. The model calibration process ensures that fitted transmissibility adjusts dynamically to align with observed hospitalization trends by exemplar season. 

# Model Calibration

The ODE is calibrated using historical hospitalization data (2017-2018 and 2019-2020 seasons) from an augmented NHSN hospitalization dataset previously described [here](https://www.medrxiv.org/content/10.1101/2024.07.31.24311314v1). Weekly hospitalizations are fitted to minimize the squared deviation from observed hospitalizations. Baseline transmissibility, seasonal forcing parameters, initial states, and hospitalization rates are optimized per state and exemplar season, using "business as usual" vaccine uptake during parameterization. Therefore, when running the model, the same parameters are used for geography X for scenarios A, C, and E, with the exception of vaccine efficacy and uptake. The model accounts for state-specific age distributions, incorporating demographic effects on transmission risk.

# Model Assumptions

## Immunity assumptions

### Number/type of immune classes considered

The model contains one fully susceptible class, and one fully immune class, R, per geography. These classes however, are governed by the age-structured differences within each geography, and the model therefore incorporates demographic differences in initial susceptibility, vaccine efficacy, and vaccination rates.

### Initial proportion of population with residual immunity from previous infections and previous seasonal vaccinations (by age, if available)

Initial susceptibility is estimated by geography during parameter calibration. While initial states are not calibrated at the age-group level, they are based on historical data and other parameters that are adjusted and weighted by age-group level population within each state. Initial immunity varies between 3.2% and 45%.

### Waning immunity throughout the season (yes, no, differs for vaccination and natural infection)

The model assumes no waning immunity within the simulation period, but vaccine failure is implicitly captured in an effective vaccination rate per geography, weighted by age demographics:

EffectiveVaxRate<sub>time, geography, age</sub> = VaccineEfficacy<sub>age</sub> * VaccinationRate<sub>time, geography</sub>, and then EffectiveVaxRate<sub>time, geography</sub> is weighted by the relative population sizes of age groups within that geography.

## Details on Influenza Strain(s)

### Number of strains/subtypes included in model

The model only explicitly models a single strain, but the dual-harmonic seasonal-forcing term can mimic dynamics observed when two or more strains are present that season.

### Strain(s) specifications (immune escape, transmissibility)

The model only considers one strain, but transmission and immunity terms are calibrated depending on exemplar season (H3N2 dominant or H1N1 dominant).

### Are interactions between strains/subtypes implicitly modeled?

No

## Seasonality implementation

Seasonal forcing follows a two-peak harmonic function fitted per dominant strain (exemplar season). Peak weeks are estimated separately for each season.

## Initial Conditions

### Details on circulating strains at the start of the projection period

Only one strain is modeled, but initial conditions are estimated separately for the H1N1 scenarios and the H3N2 scenarios.

## Non-pharmaceutical interventions (NPIs)

None are considered.

## Age Group Variability

### No of age groups

Six age groups: 0-4, 5-17, 18-49, 50-64, 65-130, and 0-130.

Within our system of differential equations, only one age group is tracked, however, model parameters are calibrated based on state-specific age demographics. Outside of the system of differential equations, our model captures age-specific death and hospitalization rates using a multiplier applied to the new hospitalizations at time, t.

### Age-stratification differences (susceptibility, vaccine effectiveness, waning)

Geography-level differences in parameters are informed by the age demographics within that geography, but the ODE is not explicitly age-stratified.

## State-level Variability

### State-stratification details (prior immunity, vaccine coverage)

Vaccination coverage varies by state, affecting risk stratification. Vaccine efficacy varies by age group, and age group distributions vary by state. Therefore vaccine efficacy varies by state, because we weighted vaccine efficacy by relative age group population sizes. Age distributions within each state also influence hospitalization and death projections. State-level hospitalization data is used for parameter estimation, ensuring geographic heterogeneity.

## Vaccine Effectiveness

### VE against infection (by age, if relevant)

Vaccine efficacy is incorporated into an effective vaccination rate term. Efficacy values were taken from CDC estimates of exemplar season (dominant strain) vaccine efficacy, by age group. We aggregated efficacy terms across all age groups for each geography by weighting efficacy on the relative populations of each age group within that geography.

### VE against mortality (by age, if relevant)

VE is only explicitly modeled against infection.

### VE against transmission (by age, if relevant)

VE is only explicitly modeled against infection.

## Other Model Assumptions

- Age-specific hospitalization outcomes are scaled based on age-specific multipliers.
- Vaccine efficacy is considered constant within each modeled season.
