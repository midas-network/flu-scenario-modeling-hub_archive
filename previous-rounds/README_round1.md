<a href="https://fluscenariomodelinghub.org/"><img src= "https://github.com/midas-network/flu-scenario-modeling-hub/blob/main/logo.png" alt="drawing" width="300"/></a>

# Flu Scenario Modeling Hub

Last updated: 7-29-2022 for **Round 1 Scenarios**.

## Round 1 Scenarios     

Round 1 of influenza projections considers the interaction of vaccination 
protection during the current season (first dimension) with the impact of the 
COVID-19 pandemic on prior immunity (2nd dimension) over a 41-week period. We 
follow the usual 2 * 2 table structure from the 
[COVID-19 Scenario Modeling Hub](https://covid19scenariomodelinghub.org/). 

<img src= "https://raw.githubusercontent.com/midas-network/flu-scenario-modeling-hub/main/previous-rounds/flu_round1.png">

### **OTHER SPECIFICATIONS AND ASSUMPTIONS**

**Prior Immunity***

*   Prior influenza immunity is assumed to be a combination of residual 
immunity from previous infections and previous seasonal vaccinations. The 
exact specifications of prior immunity is left at the discretion of each 
team, and will depend on model specification, but we provide suggestions 
below. 

*   At the onset of a typical influenza season (all subtypes combined), 
modeling has been estimated that around 30-35% of the population has prior 
immunity (65-70% susceptible), the effective reproduction number ranges from 
1.2-1.4, and the attack rate (final size) is between 8-25% 
https://www.pnas.org/doi/pdf/10.1073/pnas.1415012112. The 2009 pandemic, 
which was marked by the emergence of a new strain to which individuals under 
the age of 50 yrs were susceptible, was associated with greater transmission 
(cumulative attack rates 32% over 2009) and decreased prior immunity compared 
to a regular season (prior immunity in 2009 is ~25% instead of ~33%).

*   Scenarios A and C (optimistic prior immunity) are meant to project the 
impact of a regular influenza season, with the same average immunity conditions 
as pre COVID19.

*   Scenarios B and D (pessimistic prior immunity) are meant to project the 
impact of a high-transmission influenza season, driven by the immunity gap 
left by two years of low influenza circulation. We expect that the immunity gap 
is primarily driven by loss of immunity from natural infection. Flu vaccination 
has proceeded as usual each fall since 2020 in the US, but vaccine-derived immunity 
is short lasting. In scenarios B and D, the total proportion of immune individuals 
at the start of the season (no matter where immunity comes from) should be half (X0.5) 
of that assumed in scenarios A and C. For instance if prior immunity is 33% in 
scenarios A and C, it should be 16.5% in scenarios B and D.

*   Teams are allowed to vary prior immunity by virus subtype, age or other demographic 
characteristic, as long as the overall matches the scenario specifications.


**COVID-19 Interactions**

*   No major interactions with future COVID-19 surges (immunological, social, 
behavior)

**Influenza strains**

*   All subtypes together (but H3N2 is presumed dominant, >75% H3N2 of all 
positive flu viruses)
    *   Targets include influenza A and B combined

*   Subtype-specific models are allowed
    *   Immunity conditions should be applied to all subtypes/strains that 
    aggregates to the overall conditions specified in the scenarios

*   Intrinsic transmissibility: Assumed H3N2 is same as 2021-2022 H3N2 

**Vaccine Effectiveness**

*   We assume that VE against hospitalizations and medical illnesses is the same. 
We index high VE [(overall estimate 60%)](https://pubmed.ncbi.nlm.nih.gov/22843783/)
 on the 2010-11 season and low VE [(overall estimate 30%)](https://www.cdc.gov/flu/vaccines-work/2018-2019.html) 
 on the 2018-2019 season. 


*   Teams should use the following data  to scale VE to different age groups and 
strains/subtypes. We recommend considering age-specific differences.
https://www.cdc.gov/flu/vaccines-work/2018-2019.html (2018-2019 low VE season)
https://pubmed.ncbi.nlm.nih.gov/22843783/ (2010-2011 high VE season)


*   Vaccine effectiveness against hospitalizations is calculated using a Test Negative 
Design (TND), which compares the odds of current-season vaccination amongst test-positive 
influenza cases and test-negative controls who are admitted into a hospital with an 
influenza-like-illness (ILI). Many studies agree that vaccine effectiveness against 
hospitalization varies by age. Particularly, VE against hospitalizations is highest for 
children and lowest for older adults (65+).
    *   Vaccine effectiveness for adults ages 18-64 is 51% (95 CI:44, 58) on average. 
    However VE declines to 29% (13-44) when the vaccine is not matched. We suggest that 
    teams use 60% for scenarios A and B and 30% for scenarios C and D.  
    https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5912669/
    *   Cited by the CDC on their website 
    https://www.cdc.gov/flu/vaccines-work/effectivenessqa.htm#43


**Vaccine immune waning**

*   Vaccine-induced immunity has been found to decrease rapidly over the course of an 
influenza season https://academic.oup.com/cid/article/64/5/544/2758477?login=true

**Age groups**

*   Age-stratification is optional. If stratified, immunity and vaccination 
should aggregate to specifications in scenarios
*   Suggested age-strata:
    *   0-4, 5-17, 18-49, 50-64, and 65+ (or some aggregation of this, like 18-64, etc.). 
    Most of the burden on hospitalization and deaths come from the 0-4 and 65+ age groups.

**State-level variability**

*   Vaccination coverage, age population 
*   Variability in severity between states is possible
*   It is acceptable to assume prior immunity (due to a combination of 
vaccination and natural infection) the same across states; variability 
between states is allowed as long as it aggregates to the scenario definition 
for the US overall (population weighted average)

**Cross-protection of subtype immunity:** At the discretion of the teams.

**Influenza vaccine coverage data:** Projected week and state-level coverage to use 
in scenarios A-D are provided [here](https://github.com/midas-network/flu-scenario-modeling-hub_resources/blob/main/Rd1_datasets/Age_Specific_Coverage_Flu_RD1_2022_23_Sc_A_B_C_D.csv) for various age groups: 
0-4yr, 5-12yr, 13-17yr, 0-17yr, 18-49yr, 50-64yr, 65+yr. These are based on 110% 
and 90% of the vaccination rates reported in 2020-21; estimates can be used as 
is without further adjustment.

**Seasonality:** Teams should include their best estimates of influenza seasonality 
in their model but we do not prescribe a specific level of seasonal forcing.

**NPI:** No reactive NPIs to COVID-19 or influenza; low level masking allowed at 
groups’ discretion.

**Seeding of influenza:** Influenza begins seeding into the US with 50 infections 
per week for 16 weeks starting August 14, 2022. Seeding locations and distribution 
are at the discretion of the teams. *<u>If influenza is already circulating in the US, 
this seeding will be adjusted.</u>*

**Initial Conditions:** The mix of circulating strains at the start of the projection 
period is at the discretion of the teams based on their interpretation/analysis of the 
available data and estimates at the time of projection. Variation in initial prevalence 
between states is left at teams’ discretion.
 
**All of the teams’ specific assumptions should be documented in metadata and 
abstract.**


### **Targets and Time Horizon:**

**Projection time horizon:** We consider a **41-week projection period:**

*    *August 14, 2022* to *June 3, 2023*

**Targets:** 

*   **Weekly target**
    *   Weekly state-level incident and cumulative hospitalizations, based on 
    HHS COVID and flu [reporting system](https://healthdata.gov/Hospital/COVID-19-Reported-Patient-Impact-and-Hospital-Capa/g62h-syeh). This dataset is updated daily and covers 2020-2022. Weekly 
    hospitalizations should be based on the “previous_day_admission_influenza_confirmed” 
    variable, without any adjustment for reporting (=raw data from HHS dataset to be 
    projected). A current version of the weekly aggregated data has [been posted here](https://github.com/midas-network/flu-scenario-modeling-hub_resources/blob/main/Rd1_datasets/HHS_flu_2020_2022_dataset.csv).
    *   Weekly national incident deaths, from the CDC multiplier model. These are real-time 
    model estimates updated weekly during the influenza season.  The model relies on 
    influenza deaths reported in the hospitals via the flusurvnet system, adjusted for under 
    testing of flu in the hospital and the proportion of deaths occurring outside of the 
    hospital. There is no state detail.  3 historical seasons of weekly data are provided 
    [for calibration](https://github.com/midas-network/flu-scenario-modeling-hub_resources/blob/main/Rd1_datasets/In-season-National-Burden.csv). Further, see [here](https://www.cdc.gov/flu/about/burden/preliminary-in-season-estimates.htm) for cumulative estimates at the end of the season for a longer time period. 
    * No case target
    * No infection target   
    * All targets should be numbers of individuals, rather than rates.

*   **Seasonal target**
    * State-level peak hospitalizations.
    * State-level timing of peak hospitalizations.
    * Note that cumulative deaths and cumulative hospitalizations at the end of the 
    projection period/season will also be used as seasonal targets. These quantities 
    are already listed under weekly targets (=cumulative weekly outcomes on week 41, 
    the last week of projections).

All cumulative outcomes start at 0 at the start of the projection period, i.e. on week 0 of projections.

</br>

## Submission Information    

| Scenario | Scenario name for submission file | Scenario ID for submission file |
| ---------------------------------------------- |:---------------------------------:|:-------------------------------:|
| Scenario A. High vaccine protection, Optimistic immunity         | highVac_optImm | A-2022-08-14 |
| Scenario B. High vaccine protection, Pessimistic immunity        | highVac_pesImm | B-2022-08-14 |
| Scenario C. Low vaccine protection, Optimistic immunity          | lowVac_optImm  | C-2022-08-14 |
| Scenario D. Low vaccine protection, Pessimistic immunity         | lowVac_pesImm  | D-2022-08-14 | 
*   **Due date**: Aug 16, 2022 
*   **End date for fitting data**: Aug 13, 2022 
*   **Start date for scenarios**: Aug 14, 2022  (first date of simulated 
transmission/outcomes)
*   **Simulation end date:** June 3, 2023  (41-week horizon)
*   We aim to release results by Aug 30, 2022 


**Other submission requirements**

*   **Geographic scope:** state-level and national projections
    *    All states not required, US overall recommended.
*   **Results:**
    *  Summary: Results must consist of a subset of weekly and/or summary 
    targets listed below; all are not required. Weeks follow epi-weeks (Sun-Sat)
    dated by the last day of the week.
    *  **Weekly Targets** (subset of: hospitalizations, deaths)
        *    Weekly incident 
        *    Weekly cumulative since start of season (August 14, 2022)
    *  **Summary Targets** (hospitalizations)
        *    Peak size
        *    Peak timing 
*   **Metadata:** We will require a brief meta-data form, from all teams.
*   **Uncertainty:** We ask for 0.01, 0.025, 0.05, every 5% to 0.95, 0.975, and 
0.99. Teams are also encouraged to submit 0 (min value) and 1 (max) quantiles 
if possible. At present time, *inclusion in ensemble models requires a full set 
of quantiles from 0.01 to 0.99.*
*    **Simulation sample:** We ask that teams submit a sample of up to 100 
simulation replicates. Simulations should be sampled in such a way that they 
will be most likely to produce the same summary statistics as that quantile 
submitted. For some models, this may mean a random sample of simulations, for 
others with larger numbers of simulations, it may require weighted sampling.

</br>

## More details on target:

### Hospital target:

*   We use the [HHS COVID-19 Reported Patient Impact and Hospital Capacity by State Timeseries](https://healthdata.gov/Hospital/COVID-19-Reported-Patient-Impact-and-Hospital-Capa/g62h-syeh). The target to be 
projected is confirmed influenza hospital admissions, reported as 
*previous_day_admission_influenza_confirmed*. Therefore, before aggregating to the 
weekly values, the gold standard or “truth” data will shift the values in the date 
column one day earlier so that the date aligns with the date of admission. As an 
example, if 17 confirmed influenza hospital admissions were reported in the 
`previous_day_admission_influenza_confirmed` field in a row where the `date field` 
was 2021-10-30, then the “truth” dataset would assign those 17 hospital admissions 
to a date of 2021-10-29. These cases would then be counted towards the weekly total 
computed for EW43, which runs from 2021-10-24 through 2021-10-30.
*   Influenza admission reporting became mandatory in this dataset on Feb-02-2021,
 and should continue to be mandatory for the duration of the summer and into the 
 next flu season. Accordingly, more than 41,000 US hospitals are reporting flu on 
 a weekly basis and no adjustment for reporting changes should be made. However the 
 data before Feb-02-2021 should be treated with caution.
*   Unlike flu admissions, flu deaths are no longer mandatory to report in this system 
and hence a different source of data will be used for deaths.
*   There is no age breakdown for flu in this HHS dataset. If teams need age-specific 
hospitalization data for calibration, or a longer dataset, they can apply the age 
distribution of flu hospitalizations available in [Flusurv-NET](https://gis.cdc.gov/GRASP/Fluview/FluHospRates.html) 
to the all-age HHS rate. Flusurv-NET is CDC’s parallel and long-running hospitalization 
surveillance system, which is based on a smaller set of US hospitals (9%). We have provided 
state-specific time [series here](https://github.com/midas-network/flu-scenario-modeling-hub_resources/blob/main/Rd1_datasets/Flusurvnet_2003_2022_dataset.csv) (2003-present). Because Flusurv-NET data is not 
available for all states, we recommend that teams use the national age distribution of 
hospitalizations estimated in Flusurv-NET and apply it to national and state-specific 
HHS data. Adjustment for demographic differences between states can be considered, but 
are not required.
*   Earlier analyses have shown that estimates of influenza incidences are consistent 
between the HHS and CDC hospital surveillance systems in areas where both systems overlap.

</br>

## Additional resources:

#### Delphi CMU group: 

See https://delphi.cmu.edu/flu/

API documentation: https://cmu-delphi.github.io/delphi-epidata/

*   This includes HHS flu hospitalizations: https://cmu-delphi.github.io/delphi-epidata/api/covidcast-signals/hhs.html
*   Outpatient ILI (influenza and other similar 
illnesses) computed from medical insurance claims: https://cmu-delphi.github.io/delphi-epidata/api/covidcast-signals/chng.html

 
 
