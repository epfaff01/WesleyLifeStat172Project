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

## Data Sources and Preparation

### Data Source
The dataset is sourced from publicly available government data on food insecurity, socio-economic factors, and demographic information for seniors across different PUMAs in the United States.

---
