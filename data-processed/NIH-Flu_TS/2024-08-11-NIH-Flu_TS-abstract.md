# Summary of Results (Round 5)

Our projections for the 2024-2025 season vary based on the dominant influenza A virus (IAV) subtype (A/H3N2 or A/H1N1) and vaccine coverage levels (high, low, or 'business as usual'). At the national level, an A/H3N2-dominant season is expected to result in earlier and larger waves of hospitalizations than an A/H1N1-dominant season. For both IAV subtypes, lower vaccine coverage produces larger epidemics. Nationally, we project that similar epidemic sizes could occur across A/H1N1 and A/H3N2 dominant seasons, depending on vaccine coverage. Specifically, higher vaccine coverage during an A/H3N2 dominant season could offset its intrinsically greater severity, aligning it with the epidemic size of an A/H1N1 dominant season with low coverage.

**Cumulative and peak hospitalizations**

At the national level, cumulative and peak projections increase from Scenario B to D to F (A/H1N1-dominant scenarios), then A to C to E (A/H3N2 dominant scenarios) (Tables 1-2).

Nationally, Scenario B (A/H1N1 dominant, high coverage) is the most 'optimistic' scenario (median 182,293 total hospitalizations, 95% PI: 125,628 – 250,679), while Scenario E (A/H3N2 dominant, low coverage) is the most 'pessimistic' (median 381,419 total hospitalizations, 95% PI: 293,510 - 489,305). Scenario F (A/H1N1 dominant, low vaccine coverage) is projected to have slightly fewer hospitalizations than Scenario A (A/H3N2 dominant, high vaccine coverage).

**Table 1.** Projected cumulative influenza hospitalizations in the U.S. for six scenarios, ordered by increasing severity.

| Scenario          | Description 											| Median  	| 95% PI 		  |
| :---------------- | :-----------------------------------------------------| :-------:	| :--------------:|
| Scenario B        | A/H1N1 dominant, high vaccine coverage   				| 182,293	| 125,628 - 250,679 |
| Scenario D        | A/H1N1 dominant, "business as usual" vaccine coverage | 217,942	| 156,449 - 293,964 |
| Scenario F    	| A/H1N1 dominant, low vaccine coverage    				| 259,470	| 191,147 - 342,389 |
| Scenario A  		| A/H3N2 dominant, high vaccine coverage  				| 283,509 	| 209,523 - 376,208 |
| Scenario C  		| A/H3N2 dominant, "business as usual" vaccine coverage | 329,823	| 248,615 - 429,609 |
| Scenario E  		| A/H3N2 dominant, low vaccine coverage  				| 381,419	| 293,510 - 489,305 |

**Table 2.** Projected peak influenza hospitalizations in the U.S. for six scenarios, ordered by increasing severity.

| Scenario          | Description 											| Median | 95% PI 		 |
| :---------------- | :-----------------------------------------------------| :----: | :------------:|
| Scenario B        | A/H1N1 dominant, high vaccine coverage   				| 18,194 | 11,823 - 25,732 |
| Scenario D        | A/H1N1 dominant, "business as usual" vaccine coverage | 21,392 | 13,831 - 28,953 |
| Scenario F  		| A/H1N1 dominant, low vaccine coverage   				| 24,922 | 16,040 - 32,416 |
| Scenario A    	| A/H3N2 dominant, high vaccine coverage   				| 26,057 | 19,830 - 37,674 |
| Scenario C  		| A/H3N2 dominant, "business as usual" vaccine coverage | 30,033 | 22,578 - 41,739 |
| Scenario E  		| A/H3N2 dominant, low vaccine coverage  				| 34,369 | 25,553 - 46,069 |

**Comparisons of national-level scenario projections to historical seasons**

- Scenario B (A/H1N1 dominant, high vaccine coverage): The most optimistic scenario, slightly smaller than the 2014-2015 and 2016-2017 seasons.
- Scenario D (A/H1N1 dominant, "business as usual" coverage): Similar in size to the 2019-2020 season, as A/H1N1 scenarios are indexed against this season.
- Scenario F (A/H1N1 dominant, low coverage): Similar in size to last season's total hospitalizations.
- Scenario A (A/H3N2 dominant, high coverage): Projected to exceed last season's hospitalizations by 15%.
- Scenario C (A/H3N2 dominant, "business as usual" coverage): Similar in size to the 2017-2018 season, as A/H3N2 scenarios are indexed against this season.
- Scenario E (A/H3N2 dominant, low coverage): The most pessimistic scenario, 11% larger than the 2017-2018 season.

**Peak timing**

Nationally, hospitalizations are projected to peak in early January for A/H3N2 dominant scenarios and in early February for A/H1N1 dominant scenarios.

At the state level, A/H3N2 scenarios generally follow a west-to-east pattern: west coast and mountain states are projected to peak from late December to mid-January, southern, Midwest, and Mid-Atlantic states from mid-January to early February, and northeastern states from early to mid-February. Outside of this pattern, Mississippi, Louisiana, and Texas are projected to peak first in late December, and South Dakota and Montana are projected to peak last in early March. In contrast, A/H1N1 scenarios project that epidemics will peak from early February to early March, with no clear geographic pattern.

# General Model Description

We model flu hospitalizations in each location using dynamic harmonic regression with ARMA errors and exogenous covariates for seasonal vaccine coverage, seasonal vaccine effectiveness, weekly A/H3N2 virus circulation, and weekly estimated influenza infections.

Our time series approach requires providing values for exogenous covariates during the projection period. For projections, we use weekly values of A/H3N2 virus circulation and estimated influenza infections from the 2017-2018 season (for A/H3N2 dominant scenarios) or the 2019-2020 season (for A/H1N1 dominant scenarios). For each location, we assume "business as usual" cumulative vaccine coverage is the same as observed in 2022-2023 season (the most recent season with available data) and set vaccine effectiveness at 40%, as dictated by the hub.

Models trained on hospitalizations during the first years of the COVID-19 pandemic and initial rebound of influenza produced unrealistic projections. Instead, we trained models on weekly hospitalizations spanning five pre-pandemic seasons (2015-2016 to 2019-2020), with the 2023-2024 season (considered the return to typical flu seasonality) appended to the end of the pre-pandemic time series. Thus, model calibration excludes hospitalizations from the 2020-2021 to 2022-2023 seasons.

Methods for inferring weekly infections and information about initial susceptibility, historical vaccine effectiveness, and historical vaccine coverage are provided in later sections.

# Explanation of observed dynamics given model assumptions

The dominant influenza A virus (IAV) subtype has a greater impact on epidemic severity than vaccine coverage, though increased coverage reduces cumulative and peak hospitalizations for each dominant IAV subtype. Nationally and for most individual states, A/H3N2 dominant seasons are projected to have higher peak and cumulative hospitalizations than A/H1N1 dominant seasons. National projections show that lower vaccine coverage leads to higher hospitalizations, but some states show little difference across coverage scenarios (e.g., Hawaii, Idaho, Illinois, Maine, Minnesota, South Carolina, Washington). This may be due to historical anomalies in those states (e.g., large epidemics despite high vaccine coverage or vice versa), as our model is statistical rather than mechanistic.

# Model Calibration

We calibrated our model using historical data on influenza hospitalizations, outpatient influenza-like illness (ILI) rates, influenza A virus (IAV) subtype circulation, and vaccine coverage and effectiveness. To determine the optimal training period, we tested the accuracy of out-of-season projections for historical seasons prior to 2020-2021.

The HHS Protect ("gold standard") target dataset starts in November 2020, and mandatory reporting of influenza hospitalizations began in February 2021. We found that [CDC FluSurv-NET hospitalization rates](https://www.cdc.gov/flu/weekly/influenza-hospitalization-surveillance.htm) closely align with the HHS data for overlapping seasons (2021-2024). Therefore, we used FluSurv-NET data, converted to counts using census population estimates, as our historical dataset for the U.S. and 12 states. For states without FluSurv-NET data or with a poor match between FluSurv-NET and HHS data, we used a similar approach with [CDC FluView](https://www.cdc.gov/flu/weekly/fluviewinteractive.htm) data, converting ILI x percent positive rates to counts for an additional 27 states. Our projections exclude Alaska, Delaware, Florida, Iowa, Nevada, New Hampshire, New Jersey, North Dakota, Rhode Island, Utah, Wyoming, the District of Columbia, and U.S. territories, due to insufficient or noisy historical data.

For seasons 2015-2016 to 2023-2024, we estimated weekly infections in each location by fitting semi-mechanistic [epidemiological models](https://imperialcollegelondon.github.io/epidemia/) to observed ILI x percent positive rates, assuming a case ascertainment rate of 0.3. We found that influenza infections typically lead hospitalizations by 1-3 weeks, so we include one- and/or two-week lags of weekly infections as exogenous covariates in our models, depending on the particular location. Lagged infections capture the general shape and timing of epidemic waves but do not estimate the 'true' number of flu infections.

Information about historical and projected vaccine effectiveness and vaccine coverage are in the "Vaccine Effectiveness" and "Other Model Assumptions" sections.

# Model Assumptions
## Immunity assumptions
### Number/type of immune classes considered
N/A

### Initial proportion of population with residual immunity from previous infections and previous seasonal vaccinations (by age, if available)
In epidemiological models estimating weekly infections, the initial proportion susceptible is assumed to be 0.65 ([Yang et al. 2015](https://doi.org/10.1073/pnas.1415012112)).

### Waning immunity throughout the season (yes, no, differs for vaccination and natural infection)
N/A

## Details on Influenza Strain(s)
### Number of strains/subtypes included in model
We do not train or project strain-specific hospitalizations. However, we include the weekly proportion of samples testing positive for A/H3N2 as an exogenous covariate, since A/H3N2 dominant seasons are generally more severe. We chose to not include weekly A/H1N1 percent positive values in the model due to their high collinearity with A/H3N2 time series, which would add little value to the model.

### Strain(s) specifications (immune escape, transmissibility)
N/A

### Are interactions between strains/subtypes implicitly modeled?
N/A

## Seasonality implementation
For most locations, flu seasonality is modelled using Fourier terms, with short-term time series dynamics handled by an ARMA error. We determined the optimal number of Fourier sine and cosine pairs (_K_) by comparing model fits with AIC, RMSE, and MAPE. We chose to specify _K_=12 for the U.S. and _K_ = 10 or _K_=12 for states. For nine states (Connecticut, Georgia, Hawaii, Kansas, Kentucky, Maryland, Ohio, Pennsylvania, Virginia), projections are more reasonable when seasonality parameters are estimated by the model itself (i.e., ARIMA instead of ARMA). For these states, we used the auto.arima() function in R to determine the best fit ARIMA model according to AICc.

## Initial Conditions
### Details on circulating strains at the start of the projection period
The initial proportion of samples positive for A/H3N2 is the weekly value observed at the start of the 2017-2018 season (for A/H3N2 dominant scenarios) or the 2019-2020 season (for A/H1N1 dominant scenarios).

## Non-pharmaceutical interventions (NPIs)
N/A. Models are trained on historical data from the 2015-2016 to 2019-2020 seasons and the 2023-2024 season. Thus, we do not consider the effects of COVID-19 pandemic NPIs on hospitalizations.

## Age Group Variability
### No of age groups
N/A

### Age-stratification differences (susceptibility, vaccine effectiveness, waning)
N/A

## State-level Variability
### State-stratification details (prior immunity, vaccine coverage)
Each of the 39 states have separate models with exogenous covariates for seasonal cumulative vaccination coverage, seasonal vaccine effectiveness, weekly A/H3N2 circulation, and weekly estimated influenza infections. The values of exogenous covariates, with the exception of VE, are specific to each state. 

## Vaccine Effectiveness
We obtained adjusted vaccine effectiveness estimates from published observational studies, the majority of which were test-negative case control design and focused on general populations or healthy adult populations in the U.S. See the [CDC's influenza VE page](https://www.cdc.gov/flu-vaccines-work/php/effectiveness-studies/past-seasons-estimates.html?CDC_AAref_Val=https://www.cdc.gov/flu/vaccines-work/past-seasons-estimates.html) for seasonal estimates. Projections use the vaccine effectiveness estimate dictated by the hub (40%).

### VE against infection (by age, if relevant)
N/A

### VE against mortality (by age, if relevant)
N/A

### VE against transmission (by age, if relevant)
N/A

## Other Model Assumptions

**Vaccine coverage in historical seasons**

We obtained national and state-specific monthly vaccine coverage estimates for individuals aged >6 months during seasons 2010-2011 to 2022-2023, from the [National Center for Immunization and Respiratory Diseases](https://data.cdc.gov/Flu-Vaccinations/Influenza-Vaccination-Coverage-for-All-Ages-6-Mont/vh55-3he6). For each historical season, we use the final cumulative vaccine coverage value for the U.S. and each state. For the projection period, we use the seasonal cumulative vaccine coverage values dictated by the hub, which are based on the 2022-2023 season.

**Approach for producing stochastic simulations of model projections**

1. Train the time series model on historical seasons. For most locations, this is a dynamic harmonic regression model with ARMA errors and exogenous covariates for seasonal vaccine coverage and VE, weekly A/H3N2 virus circulation, and weekly estimated influenza infections.
2. Calculate the residuals.
3. Bootstrap the residuals: randomly sample residuals with replacement to create new sets of residuals.
4. Generate new forecasts: add bootstrapped residuals back to the model's predicted values to create new forecasted values. Each new forecast (future sample path) is a combination of the model's prediction and a sampled residual.
5. Repeat this process 1000 times to generate a distribution of forecasts.

For each location, we generate forecasts for each scenario separately but use the same random seed across the six scenarios. For each location and scenario pair, we then sub-sample to 300 representative simulations using the same random seed.

Note: Stochasticity across simulations arises from randomly sampling from the collection of errors (residuals) observed in the past, and there is not an assumed distribution for the residuals. See [Hyndman, R.J., & Athanasopoulos, G. (2021) _Forecasting: principles and practice_, 3rd edition, Chapter 5.5](https://otexts.com/fpp3/prediction-intervals.html#prediction-intervals-from-bootstrapped-residuals).