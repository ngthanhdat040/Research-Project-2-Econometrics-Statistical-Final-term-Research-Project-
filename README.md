# Research-Project-2-Econometrics-Statistical-Final-term-Research-Project-

# RESEARCH CONTEXT 
The debate on the environmental impact of Foreign Direct Investment (FDI) originated during the trade liberalization wave of the 1970s, establishing two contrasting theoretical paradigms in international environmental economics:Pollution Haven Hypothesis (PHH) (Copeland & Taylor, 1994):Strict environmental regulations in developed nations elevate operational compliance costs, driving carbon-intensive industries to relocate FDI toward developing countries with weaker regulatory frameworks. Consequently, global pollution is geographically displaced rather than reduced $\rightarrow$ FDI accelerates environmental degradation.Pollution Halo Hypothesis (PHaH) (Eskeland & Harrison, 2003):FDI acts as a channel for technology transfer, bringing superior environmental management standards, cleaner production techniques, and positive technology spillovers to host countries $\rightarrow$ FDI abates carbon emissions and promotes green growth.
While these hypotheses make conflicting predictions based on divergent assumptions about the nature of FDI—whether as a cost-arbitrage tool or a technological spillover engine—the empirical literature regarding the relationship between FDI and $\text{CO}_2$ emissions remains highly fragmented and contradictory.This research addresses a critical methodological gap: Is this empirical disagreement a reflection of inherent economic complexity, or a result of overgeneralizing findings across heterogeneous country panels?

# RESEARCH QUESTIONS & OBJECTIVE 
Building upon the theoretical framework and analytical approach, this study focuses on resolving six core research questions across its empirical chapters:
1. Direction and Magnitude of FDI Impact: How does FDI impact CO2 emissions, and what is the direction of this effect? Furthermore, are there systematic variations across distinct national income tiers?
2. Attribution and Confounding Effects: Is the impact of FDI on emissions substantial enough to be identified as a primary emission driver, or is it heavily mediated or dominated by other macroeconomic factors?
3. Economic Development Threshold: Does there exist an economic development threshold (such as a turning point in per capita income) where the environmental impact of FDI reverses from pollution-inducing to emission-reducing?
4. Probability of High-Emission Classification: Holding other covariates constant, does the conditional probability of a country falling into a high-emission tier differ significantly across income groups?
5. Temporal Stability: Is the empirical relationship between FDI and CO2 emissions stable over time, or does it shift across different developmental phases over the past two decades?
6. Unobserved Heterogeneity & Model Specification: Do country-specific unobserved characteristics alter the statistical significance of FDI's impact on emissions? Specifically, do fixed effects or random effects better capture cross-national heterogeneity?

# DATA MODELING WORKFLOW 
1.Data Preprocessing & Preliminary Diagnostics:
- Data Preprocessing: Handling missing values, filtering outliers, transforming non-stationary variables (e.g., logarithmic transformations to compute elasticities), and preparing clean cross-sectional/panel relational structures.\
- Summary Statistics & Diagnostics: Computing descriptive statistics, profiling distributions, and performing initial normality tests.
2. Simple Linear Regression Analysis:
- Baseline Bivariate Modeling: Estimating simple linear regression models (OLS) to establish initial bivariate relationship baselines between FDI inflows and CO2 emissions.
- Direct Effect Assessment: Evaluating goodness-of-fit metrics R^2 and coefficient significance without controlling for confounders.
3. Multiple Linear Regression & Model Selection
- Multivariate Control Specifications: Expanding the baseline model by incorporating key macroeconomic controls (e.g., GDP per capita, trade openness, industrial structure, energy consumption).
- Model Selection Criteria: Employing criteria such as Adjusted $R^2$, Akaike Information Criterion (AIC), and Bayesian Information Criterion (BIC) to identify optimal feature subsets.
4. Structural Extensions & Discrete Choice Modeling
- Dummy Variables & Interaction Terms: Introducing income-group indicator dummies and interaction terms ($\text{FDI} \times \text{Income Level}$) to test for regime shifts and structural heterogeneity.
- Non-linear Threshold Testing: Incorporating quadratic terms to test for turning-point thresholds (Environmental Kuznets Curve framework).
- Discrete Choice Modeling: Fitting Binary Logit/Probit models to estimate the conditional probability of a country being categorized into a high-emission tier.

5. Econometric Diagnostics & Assumption Testing
- Heteroskedasticity Testing: Conducting Breusch-Pagan / White tests and applying Huber-White Robust Standard Errors where necessary.
- Multicollinearity Diagnostics: Calculating Variance Inflation Factor (VIF) scores across explanatory variables.
- Specification Diagnostics: Executing Ramsey RESET tests for omitted variable bias and functional form misspecification.

6. Time-Series Regression Diagnostics
- Stationarity & Unit Root Tests: Performing Augmented Dickey-Fuller (ADF) tests to verify order of integration.
- Autocorrelation & Cointegration: Running Durbin-Watson / Breusch-Godfrey tests for serial correlation and checking for long-run cointegrating relationships across time intervals.

7. Panel Data Econometrics
- Fixed Effects (FE) vs. Random Effects (RE): Estimating Pooled OLS, FE, and RE panel models to account for unobserved country-specific heterogeneity.
- Model Discrimination Tests: Conducting the Hausman Specification Test to decide between Fixed and Random Effects, and the Breusch-Pagan Lagrange Multiplier (LM) test against Pooled OLS.

8. Final model Evaluation and Selection
- Robustness Checks: Comparing parameter consistency across different econometric specifications and subsamples.
- Final Model Selection: Selecting the primary empirical model that best resolves diagnostic violations while maximizing explanatory power for policy interpretation.

# DATA SOURCES AND COLLECTING METHODOLOGY

To empirically evaluate the impact of Foreign Direct Investment (FDI) inflows on per capita $\text{CO}_2$ emissions, this study integrates multi-source panel data extracted from two globally recognized open-access databases:

1. **Our World in Data (OWID):**
   * **Source File:** `owid-co2-data.csv`
   * **Key Metrics Extracted:** Historical baseline metrics including per capita carbon emissions ($\text{CO}_2$), national population, total GDP, and primary energy consumption per capita.
   * **Access Link:** [OWID GitHub Repository (`owid-co2-data.csv`)](https://github.com/owid/co2-data/blob/master/owid-co2-data.csv)

2. **World Bank — World Development Indicators (WDI):**
   * **Key Metrics Extracted:** Macroeconomic controls including Net Foreign Direct Investment inflows (`% of GDP`), Trade Openness (`% of GDP`), Industrial Value Added (`% of GDP`), and National Income Classifications.
   * **Direct Indicator Links:**
     * [FDI Inflows (`% of GDP`)](https://data.worldbank.org/indicator/BX.KLT.DINV.WD.GD.ZS)
     * [Trade Openness (`% of GDP`)](https://data.worldbank.org/indicator/NE.TRD.GNFS.ZS)
     * [Industry Value Added (`% of GDP`)](https://data.worldbank.org/indicator/NV.IND.TOTL.ZS)

> **Access Date:** June 26, 2026

### **Data Collection & Preprocessing Pipeline**

#### **1. Data Ingestion**
The dataset is constructed by merging two open-access repositories:
* **Our World in Data (OWID):** Directly queried for $\text{CO}_2$ emissions per capita, GDP, total population, and primary energy consumption per capita.
* **World Bank (WDI):** Manually collected CSV files capturing key macroeconomic indicators: Net Foreign Direct Investment (`fdi`), Trade Openness (`trade`), and Industrial Value Added (`industry`).

---

#### **2. OWID Data Cleaning & Filtering**
The raw OWID dataset contained historical emissions logs along with non-country regional aggregations (e.g., global totals, economic blocs).
* **Filtering Criteria:**
  1. Restricted timeframe to **2000–2022** matching the research scope.
  2. Filtered for valid 3-letter ISO country codes (`iso_code`) to eliminate non-entity regional aggregates.
* **Feature Selection & Missing Value Handling:** Retained core analytical features (`co2_per_capita`, `gdp`, `population`, `energy_per_capita`) and removed incomplete records via `dropna()`.
* **Output Metrics:** Raw OWID shape shifted from `(40,311, 79)` $\rightarrow$ Filtered shape `(3,760, 7)`, covering **164 distinct countries**.

---

#### **3. World Bank Reshaping & Restructuring**
World Bank raw CSV files were delivered in a **wide format** (where each year is represented as a separate column), which is incompatible with OWID's **long format** (panel structure where each row represents a unique country-year observation).
* **Data Transformation (`read_wb_csv` function):**
  * Bypassed initial 4-line metadata headers.
  * Isolated target year columns (2000–2022).
  * Executed `melt()` operations to unpivot wide year-columns into a standardized long panel format.
  * Applied transformation across FDI, Trade Openness, and Industry Share datasets, merging them sequentially on `iso_code` and `year`.
* **Output Metrics:** Integrated World Bank dataset shape: `(6,118, 8)`. Missing value rates per metric remained under 0.2% (`fdi`: 0.09%, `trade`: 0.18%, `industry`: 0.09%).

---

####  DATASET INTEGRATION & FINAL MERGING DATA TECHNIQUE**
* **Integration Strategy:** Merged the cleaned OWID panel with the structured World Bank indicators using a `Left Join` on primary key pair `(iso_code, year)`, preserving the OWID panel scope as the base frame.
* **Casewise Deletion:** Removed records with missing observations across any explanatory variable to guarantee a balanced, complete panel for econometric estimation.
* **Final Panel Dataset Metrics:**
  * **Final Shape:** `(3,258, 10)` records.
  * **Coverage:** **151 countries** over a 23-year timeframe (2000–2022).
  * **Completeness:** 0.0% missing data rate across all 10 analysis features.
    
--- PROJECT OUTPUT --- 
### **Empirical Findings & Answers to Core Research Questions**

Synthesis of empirical estimations from optimal panel econometric specifications (Fixed Effects Model with interaction terms, FEM - Model M5a) yields conclusive answers to the six overarching research questions:

#### **1. Direction and Heterogeneity of FDI Impact (Pollution Haven vs. Pollution Halo)**
Drawn from optimal FEM estimates, net FDI inflows statistically significantly increase per capita $\text{CO}_2$ emissions in low- and middle-income nations ($\beta_{\text{FDI}} = 0.0212$; $p < 0.001$), supporting the **Pollution Haven Hypothesis (PHH)**. Conversely, in high-income economies, the marginal effect of FDI reverses and approaches zero ($\beta_{\text{FDI}} + \beta_{\text{FDI} \times \text{High}} \approx -0.0001$), aligning with the **Pollution Halo Hypothesis (PHaH)**. A Wald test on interaction terms ($F = 9.82$; $p = 1.906 \times 10^{-6}$) confirms systematic heterogeneity, proving that **PHH and PHaH coexist simultaneously depending on a nation's developmental stage**.

#### **2. Effect Magnitude & Dominant Drivers**
While FDI is a statistically significant driver of emissions ($p < 0.001$), its relative effect size is modest compared to structural macroeconomic determinants. **Energy consumption per capita** and **industrial share of GDP** remain the dominant, direct drivers of emissions (established since univariate baseline $R^2 = 75.6\%$). Thus, FDI operates as a **contributing factor rather than the primary driver** of global emission levels.

#### **3. Environmental Kuznets Curve (EKC) & Turning Point Threshold**
Non-linear EKC specifications (Model M2b) confirm an inverted U-shaped relationship between per capita GDP and $\text{CO}_2$ emissions ($\beta_{\text{GDP}} > 0, \beta_{\text{GDP}}^2 < 0$; both $p < 0.001$), establishing a theoretical inflection point at **~USD $44,701 per capita**. However, only **7.3% of sample observations** exceed this threshold, demonstrating that **92.7% of nations are still in the trade-off phase**, prioritizing economic growth at the expense of environmental degradation.

#### **4. High-Emission Probability (Discrete Choice Modeling)**
Binary Logit estimations reveal that after controlling for FDI, trade openness, energy consumption, and industrial structure, income-level dummy variables ($\text{Inc}_{\text{High}}$ and $\text{Inc}_{\text{UpperMiddle}}$) lose statistical significance ($p = 0.522$ and $p = 0.210$, respectively). This indicates that **national income classification alone does not directly determine the likelihood of being a high emitter**; rather, emissions disparities across income tiers are mediated through energy consumption levels and industrial composition.

#### **5. Temporal Stability Across Two Decades (2000–2022)**
Time-series diagnostics indicate that the standalone year variable lacks statistical significance. Autocorrelation patterns observed in average ACF plots ($\rho_1 \approx 0.8$ at lag 1) stem primarily from country-specific within-unit persistence rather than an overarching global secular trend. The empirical FDI–$\text{CO}_2$ relationship remains **structurally stable over the 2000–2022 timeframe**.

#### **6. Unobserved Country Heterogeneity & Model Robustness**
The Hausman Specification Test ($\chi^2(8) = 881.96$; $p < 0.0001$) decisively confirms the presence of **Fixed Effects (FE)** over Random Effects (RE), establishing that unobserved, time-invariant country characteristics (e.g., institutions, geography, energy culture) correlate systematically with explanatory variables. Crucially, after controlling for unobserved heterogeneity via FEM, coefficients for $\text{FDI}$ and $\text{FDI} \times \text{High}$ retain their signs and high statistical significance ($p < 0.001$), proving that **the impact of FDI on $\text{CO}_2$ emissions is a robust structural relationship rather than a spurious artifact of omitted variable bias**.

---

> **Core Synthesis:** FDI impacts $\text{CO}_2$ emissions significantly, but this impact is non-uniform. It intensifies emissions in lower-income nations (Pollution Haven) while neutralizing or reducing pollution in high-income economies (Pollution Halo). **The two competing theories in international environmental economics are not mutually exclusive—they coexist across distinct national income tiers.**
