# Wesley Life Stat 172 Project - Predicting Food Insecurity Among Seniors by PUMA

## Authors
- Eric Pfaffenbach
- Anthony Esboldt
- Jason Nguyen
- Riley Schultz

## Project Overview and Goals
In this project, we aim to predict two indicators of food insecurity, FSWROUTY, and FSBAL, among seniors in different geographic locations across Iowa based on various demographic and socio-economic characteristics.

FSWROUTY: Worried that food would run out before able to afford more during past year.

FSBAL: Could not afford to eat balanced meals in the past year

We are using lasso and ridge regression models to analyze the data and make predictions about food insecurity for different Public Use Microdata Areas (PUMAs). Our goal is to identify target regions to  inform policy decisions and support appropriate resource allocation to increase food security for senior populations.

## Requirements

To install the required R packages, run the following code in R:

```{r install-packages, echo=TRUE}
install.packages(c("tidyverse", "pROC", "glmnet", "lubridate", "sf", "logistf",
                   "tigris", "ggplot2", "ggthemes", "rmapshaper", "haven"))
```

## Data Sources and Description

We use 2 data sources: one from CPS, one from ACS. These are sourced from publicly available government data.

CPS: `cps_00006.csv` (found in above files)

ACS: `spm_pu_2022.sas7bdat` (found on https://www.census.gov/programs-surveys/acs)

  The CPS (Current Population Survey) gathers data at the individual level, along with household information, making it useful for predicting food insecurity at the household level. While the CPS does collect food insecurity measures, it only covers a small number of representative counties in Iowa, which is insufficient for Wesley’s expansion decisions. Therefore, we cannot rely solely on CPS data to predict food insecurity among seniors.
  Note, we are using CPS data from across the entire Midwest, as Iowa only has 3 counties represented, which would severely limit our predictions if we were to use just CPS data from Iowa.

  The Census provides ACS (American Community Survey) Supplemental Poverty Measure data, which, like the CPS, is collected at the individual level with additional household details. Although the ACS does not specifically collect food insecurity measures, it offers a broader range of data across Iowa and includes PUMA-level information. However, due to its lack of data on hunger, the ACS alone is not sufficient to predict senior food insecurity.

## Cleaning

Much of the cleaning code for the CPS and ACS datasets was provided by Dr. Lendie Follett, our STAT 172 professor. Our group changed a categorical variable to a numeric variable, made a few other variable tweaks, and created three interaction terms, all of which can be found in the `clean_cps.R` file.

For our models, we used all demographics available in both datasets as our explanatory variables, along with the variables we created. 

## Methods

 In this project, we applied both Ridge and Lasso regression techniques to predict food insecurity outcomes. These methods help mitigate multicollinearity and overfitting. While both methods showed promise, Ridge regression outperformed Lasso in terms of the AUC value for both predictor variables, indicating better model accuracy and generalizability. As a result, Ridge regression was selected for both final models, as it provided better predictive accuracy in the given context.

## Reproduce

### 1. Run `ACS_WROUTY.R`

The script `ACS_WROUTY.R` is responsible for predicting the **WROUTY** variable. To ensure proper functionality, it sources two other scripts:
- `ACSCleaning.R`: Prepares and cleans the ACS data.
- `predict_wrouty.R`: Contains the model to predict the WROUTY variable, which itself sources the `clean_cps.R` script.

Running this script will produce two choropleth maps of Iowa:
- **Predicted Proportion of People Worried Food Will Run Out Per PUMA**
- **Predicted Number of Seniors Worried Food Will Run Out Per PUMA**

#### Script Dependencies:
- `ACSCleaning.R`
- `predict_wrouty.R`
- `clean_cps.R`

### 2. Run `ACS_FSBAL.R`

The script `ACS_FSBAL.R` is responsible for predicting the **FSBAL** variable. To ensure proper functionality, it sources two other scripts:
- `ACSCleaning.R`: Prepares and cleans the ACS data.
- `predict_FSBAL.R`: Contains the model to predict the FSBAL variable, which itself sources the `clean_cps.R` script.

Running this script will produce two choropleth maps of Iowa:
- **Predicted Proportion of People Who Cannot Afford Balanced Meals Per PUMA**
- **Predicted Number of Seniors Who Cannot Afford Balanced Meals Per PUMA**

#### Script Dependencies:
- `ACSCleaning.R`
- `predict_FSBAL.R`
- `clean_cps.R`

## Acknowledgments 
I want to thank my Stat 172 Professor, Dr. Lendie Follett, as well as my group members Anthony, Jason, and Riley for their large contributions to this project. Additionally, ChatGPT was well utilized in creating the choropleth maps.
