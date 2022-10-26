# Summary of Results
This model provides influenza scenario projections for the state of California (CA). Optimistic prior immunity scenarios roughly align with historical patterns of CA hospitalization trends (2014-2017 & 2018-2020). Pessimistic prior immunity scenarios roughly align with historical patterns of CA hospitalization during the 2017-2018 flu season. 

- For the high vaccination coverage, optimistic prior immunity scenario (scenario A), the model predicts a peak weekly incidence hospitalization size of 1642 individuals (50th percentile) and a cumulative hospitalization burden of 12017 (50th percentile).
- For the high vaccination coverage, pessimistic prior immunity scenario the model predicts a peak weekly incidence hospitalization size of	4580 individuals (50th percentile) and a cumulative hospitalization burden of 24919 (50th percentile).
- For the low vaccination coverage, optimistic prior immunity scenario (scenario C), the model predicts a peak weekly incidence hospitalization size of 2003 individuals (50th percentile) and a cumulative hospitalization burden of 14737 (50th percentile).
- For the low vaccination coverage, pessimistic prior immunity scenario (scenario D), the model predicts a peak weekly incidence hospitalization size of 5633 individuals (50th percentile) and a cumulative hospitalization burden of 30804 (50th percentile).


# General Model Description

This model provides scenarios for the state of CA. The model is a stochastic, mechanistic model implemented via the tau leap method with the following states:

- Susceptible = $S(t)$
- Vaccinated = $V(t)$
- Exposed: Unvaccinated= $E(t)$
- Exposed: Vaccinated= $E_v(t)$
- Infected = $I(t)$
- Infected: Vaccinated= $I_v(t)$
- Hospitalized= $H(t)$
- Dead= $D(t)$
- Recovered= $R(t)$

Scenario results are based on a sample size of 500 simulations per scenario. 

# Explanation of observed dynamics given model assumptions

We modeled the effect of vaccination on hospitalization, but not explicitly on probability of infection or transmission-- which meant that vaccinated individuals could still contribute equally to the force of infection. Given these assumptions, the effect of prior immunity is much stronger than vaccination coverage and effectiveness, as modeled in these scenarios.

# Model Assumptions
## Immunity assumptions
### Number/type of immune classes considered

Individuals can be either Recovered, $R(t)$ (immunity due to prior infection), or Vaccinated, $V(t)$ (from vaccination during current season).

### Initial proportion of population with residual immunity from previous infections and previous seasonal vaccinations (by age, if available)

Initial proportions with residual immunity were calculated as a function of the age class population and the frequency with which different age classes experience flu infection (captured by the \kappa values described in the "Natural immunity waning details below"). More specifically, these values were calculated by solving a series of linear equations:

$0.054R_1+ 0.167x_2+ 0.442R_3+0.185R_4+0.153R_5= R(t=0)$ where the coefficients correspond to the relative proportion of the population in each age class, $R_i$ corresponds to the initial proportion of that age class that is immune, and $R(t=0)=0.30$ or $0.15$ per scenario specifications.
$R_i$ is then proportional to the rate of natural immunity waning for age class $i$, $\kappa_i$, such that for example:
 $r= \kappa_2/\kappa_1$ & $R_2 = rR_1$.
 
**Optimistic Prior Immunity (overall 30%):**

- Ages 0-4: $R_1(t=0) = 0.0966$
- Ages 5-17: $R_2(t=0) = 0.1087$   
- Ages 18-49: $R_3(t=0) = 0.2173$
- Ages 50-64: $R_4(t=0) = 0.4967$
- Ages 65+: $R_5(t=0) = 0.5796$ 

**Pessimistic Prior Immunity (overall 15%):**

- Ages 0-4: $R_1(t=0) = 0.0483$ 
- Ages 5-17: $R_2(t=0) = 0.0543$ 
- Ages 18-49: $R_3(t=0) = 0.1087$
- Ages 50-64: $R_4(t=0) =0.2484$
- Ages 65+: $R_5(t=0) =0.2898$

### Waning immunity throughout the season (yes, no, differs for vaccination and natural infection)
**Natural immunity waning details:**
The rate at which natural immunity wanes is dependent upon age class according to [Kucharski et al. 2015, Fig.4](https://journals.plos.org/plosbiology/article?id=10.1371/journal.pbio.1002082#pbio-1002082-g004):

- Ages 0-4: $\kappa_1= 1/(10/4.5*365)$
- Ages 5-17: $\kappa_2= 1/(10/4*365)$,  
- Ages 18-49: $\kappa_3= 1/(10/2*365)$,
- Ages 50-64: $\kappa_4= 1/(10/1.75*365)$,
- Ages 65+: $\kappa_5= 1/(10/1.5*365)$ 


**Vaccine-induced immunity waning details:**
We assume that vaccine-induced immunity does not wane within a single season. This is an area in progress for future iterations of the model.

## Details on Influenza Strain(s)
### Number of strains/subtypes included in model
The model only considers a single strain of influenza.

### Strain(s) specifications (immune escape, transmissibility)
N/A

### Are interactions between strains/subtypes implicitly modeled?
No

## Seasonality implementation
We calculated a seasonal forcing function $f(t)$ based on a phase-shifted mean of CA flu hospitalization admit from 2014-2020 flu seasons ([HCAI](https://hcai.ca.gov/)). $R_0$ was calculated as $R_0=f(t)*(R_{0max}-R_{0min})+R_{0min}$ and $\beta$ was calculated as $\beta=R_0/(\rho(M)*D)$ where $\rho(M)$ is the dominant eigenvalue of the contact matrix between age groups, $M$, and $D$ is the duration of infectiousness. 

## Initial Conditions
### Details on circulating strains at the start of the projection period
Per Scenario Modeling Hub specifications, influenza begins with seeding into the US with 50 infections per week for 16 weeks starting August 14, 2022, which translates to 6 infections per week for 16 weeks in the state of CA. These seeds were distributed randomly, but proportionally to the population size of each age class in CA. So for the first 16 weeks, each age class received the following new infection seeds:

- Ages 0-4: +0
- Ages 5-17: +1
- Ages 18-49: +3 
- Ages 50-64: +1
- Ages 65+: +1

## Non-pharmaceutical interventions (NPIs)
N/A

## Age Group Variability
### No of age groups
Five age groups were included in the model following typical flu reporting: 0-4, 5-17, 18-49, 50-64, 65+

### Age-stratification differences (susceptibility, vaccine effectiveness, waning)
Age groups differ in their: proportion with prior immunity, vaccine effectiveness, hospitalization rates, hospital length of stay, and death rates.

## State-level Variability
### State-stratification details (prior immunity, vaccine coverage)
Initial conditions for prior immunity and waning of prior immunity by age class are described in the **Model Assumptions** section above. Vaccine coverage was implemented by age class in the model following the vaccination coverage curves provided by the [Scenario Modeling Hub](https://github.com/midas-network/flu-scenario-modeling-hub_resources/blob/main/Rd1_datasets/Age_Specific_Coverage_Flu_RD1_2022_23_Sc_A_B_C_D.csv) for the state of CA. 

## Vaccine Effectiveness
### VE against infection (by age, if relevant)
The model assumes that VE against transmission is negligible. 

### VE against mortality (by age, if relevant)
The model does not explicitly include VE against mortality, but does include VE against hospitalization, which is adjusted by age group from: [Treanor et al. 2012, Table 3](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3657521/); [CDC 2018-2019 season VE](https://www.cdc.gov/flu/vaccines-work/2018-2019.html)

**Optimistic**

- $VE_{h,1} = 0.58$
- $VE_{h,2} = 0.57$ 
- $VE_{h,3} = 0.51$ 
- $VE_{h,4} = 0.51$
- $VE_{h,4} = 0.36$

**Pessimistic**

- $VE_{h,1} = 0.48$
- $VE_{h,2} = 0.20$ 
- $VE_{h,3} = 0.25$ 
- $VE_{h,4} = 0.14$
- $VE_{h,4} =0.12$

### VE against transmission (by age, if relevant)
The model assumes that VE against infection is negligible. 

## Other Model Assumptions
The model includes assortative mixing by age group based off of POLYMOD survey data [Fumanelli et al. 2012 (UK)](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1002673).

**Parameter value estimates:**
*Parameters that were adjusted such that optimistic prior immunity scenarios reasonably replicated historical flu hospitalization trends. 

| Parameter     | Value         | Description                     | Source/Notes       |
| ------------- |:-------------:| -------------------------------:| ------------:|
| $\kappa$      | $\kappa_1= 1/(10/4.5*365)$, $\kappa_2= 1/(10/4*365)$, $\kappa_3= 1/(10/2*365)$, $\kappa_4= 1/(10/1.75*365)$, $\kappa_5= 1/(10/1.5*365)$      |Loss of immunity rate (days^-1^) | [Kucharski et al. 2015](https://journals.plos.org/plosbiology/article?id=10.1371/journal.pbio.1002082#pbio-1002082-g004); [Hill et al. 2019](https://journals.plos.org/plosbiology/article?id=10.1371/journal.pbio.1002082#pbio-1002082-g004) |
| $R_0$*         | 1.3-2.2    |Basic reproduction number | [Grech et. al., 2020](https://www.sciencedirect.com/science/article/pii/S0378378220303455) [Biggerstaff et. al., 2014](https://doi.org/10.1186/1471-2334-14-480) |
| $\beta$       | Calculated with NGM: R0= $\beta/\gamma*\rho(M)$ where $\rho(M)$ is the dominant eigenvalue of the contact matrix, $M$ |Transmission rate                | [Mistry et al. 2021](https://www.nature.com/articles/s41467-020-20544-y); [Fumanelli et al. 2012 (UK)](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1002673)  |
| $\sigma$*      | 1/2.8        | Loss of latency rate (days^-1^)   |[Fox et al. 2017](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1005749); [Chowell et. al., 2008](https://www.cambridge.org/core/journals/epidemiology-and-infection/article/seasonal-influenza-in-the-united-states-france-and-australia-transmission-and-prospects-for-control/CE0D31575579C69D9693890FA0F7C806); [Cori et. al., 2012](https://www.sciencedirect.com/science/article/pii/S175543651200031X)|
| $\gamma$*      | 1/2.0         | Recovery rate (days^-1^)   | 1.0 days [Cori et. al., 2012](https://www.sciencedirect.com/science/article/pii/S175543651200031X); 3.8 days [Hill et al. 2019](https://journals.plos.org/plosbiology/article?id=10.1371/journal.pbio.1002082#pbio-1002082-g004) |
| $\epsilon$    | 0        | Loss of vaccine immunity (days^-1^)   | Here we assume no loss of vaccine-induced immunity during a single flu season |
| $h$           | $h_1= 0.007$, $h_2=0.0027$, $h_3=0.0056$, $h_4=0.011$, $h_5=0.091$         | Probability of being hospitalized with flu given infection  | [FluServ-NET](https://gis.cdc.gov/GRASP/Fluview/FluHospRates.html)|
| $\phi$        | 1/6.3 days          | 1/ (time between symptom onset and hospitalization) (days^-1^)   |  [Li et al. 2019](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6731609/)|
| $LOS$        | $LOS_1= 1/5.881$, $LOS_2= 1/5.881$, $LOS_3= 1/5.881$, $LOS_4= 1/5.881$, $LOS_5= 1/5.881$      | 1/(hospital length of stay) (days^-1^)   | CA OSHPD/HCAI data |
| $\theta$     | $\theta_1 =0.0092$, $\theta_2 =0.013$, $\theta_3 =0.029$, $\theta_4 =0.057$, $\theta_5 =0.089$        | probability of death given hospitalization   | [FluServ-NET](https://gis.cdc.gov/GRASP/Fluview/FluHospRates.html) |
| $VE_h$      | **Optimistic:** .58 (0-4 y/o), 0.57 (5-17 y/o), 0.51 (18-49 y/o), 0.51 (50-64 y/o), 0.36 (65+ y/o) ; **Pessimistic:** 0.48 (0-4 y/o), 0.20 (5-17 y/o), 0.25 (18-49 y/o), 0.14 (50-64 y/o), 0.12 (65+ y/o)| Vaccine effectiveness against medically attended illness and/or hospitalization   | Scenario Specifications; [Treanor et al. 2012, Table 3] (https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3657521/); [CDC 2018-2019 season VE](https://www.cdc.gov/flu/vaccines-work/2018-2019.html)|



