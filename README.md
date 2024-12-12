# Wesley Life Stat 172 Project - Predicting Food Insecurity Among Seniors by PUMA

## Authors
- Eric Pfaffenbach
- Anthony Esboldt
- Jason Nguyen
- Riley Schultz

## Project Overview
This project aims to predict food insecurity among seniors in different geographic locations across Iowa based on various demographic and socio-economic characteristics. We are using lasso and ridge regression models to analyze the data and make predictions about food insecurity for different Public Use Microdata Areas (PUMAs). The goal is to identify target regions to inform policy decisions and support appropriate resource allocation to support food security for senior populations.

## Requirements

To install the required R packages, run the following code in R:

```{r install-packages, echo=TRUE}
install.packages(c("tidyverse", "pROC", "glmnet", "lubridate", "sf", "logistf",
                   "tigris", "ggplot2", "ggthemes", "rmapshaper", "haven"))
```

## Data Sources and Description

We use 2 data sources: one from CPS, one from ACS. These are sourced from publicly available government data.

CPS: cps_00006.csv (found above)

ACS: spm_pu_2022.sas7bdat (found on https://www.census.gov/programs-surveys/acs)

  

  The CPS (Current Population Survey) gathers data at the individual level, along with household information, making it useful for predicting food insecurity at the household level. While the CPS does collect food insecurity measures, it only covers a small number of representative counties in Iowa, which is insufficient for Wesley’s expansion decisions. Therefore, we cannot rely solely on CPS data to predict food insecurity among seniors.
  Note, we are using CPS data from across the entire Midwest, as Iowa only has 3 counties represented, which would severly limit our predictions if we were to use just CPS data from Iowa.

  The Census provides ACS (American Community Survey) Supplemental Poverty Measure data, which, like the CPS, is collected at the individual level with additional household details. Although the ACS does not specifically collect food insecurity measures, it offers a broader range of data across Iowa and includes PUMA-level information. However, due to its lack of data on hunger, the ACS alone is not sufficient to predict senior food insecurity.



```{r}
list.files()
```
