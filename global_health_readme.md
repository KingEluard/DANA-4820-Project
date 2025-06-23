# Global Health Analysis Project

## Overview

This project analyzes global health data to investigate three key research questions related to life expectancy, socioeconomic factors, and infant mortality across different countries and time periods. The analysis is divided into three main objectives, each addressing different aspects of global health patterns.

## Dataset

The project uses a global health dataset (`global_health.csv`) containing various health, economic, and social indicators for multiple countries across different years, including:

- **Health Indicators**: Life expectancy (overall, male, female), infant deaths, immunization rates
- **Economic Indicators**: GDP per capita, unemployment rate, sanitary expenses
- **Social Indicators**: Urban population percentage, safe water access, fertility rate
- **Environmental Indicators**: CO2 exposure, air pollution
- **Healthcare Infrastructure**: Hospital beds per 1000 people

## Research Objectives

### Objective 1: Gender Differences in Life Expectancy

**Research Question**: Are there significant differences in life expectancy between genders?

**Methodology**:
- Categorical analysis using life expectancy thresholds (Low: <60, Medium: 60-75, High: ≥75 years)
- Statistical tests including:
  - Wald Test
  - Score Test (Chi-square)
  - Likelihood Ratio Test
  - Binomial Exact Test
  - Paired t-test
  - ANOVA
- Confidence interval estimation (Wald, Wilson, Likelihood Ratio methods)

**Key Findings**:
- Significant gender gap in life expectancy globally
- Females consistently show higher life expectancy than males
- Analysis includes visualization of trends over time and by country

### Objective 2: Socioeconomic Factors and Life Expectancy

**Research Question**: What economic and social factors most influence lower life expectancy by gender?

**Methodology**:
- Chi-square tests of independence between categorical variables
- Logistic regression models (GLM with binomial family)
- Comparative analysis by gender
- Variables analyzed:
  - GDP per capita (categorized as Low/High)
  - Urban population percentage
  - Unemployment rate
  - Safe water access

**Key Findings**:
- **For Both Genders**: GDP, urbanization, and safe water access significantly impact life expectancy
- **Gender-Specific Differences**: 
  - Unemployment shows significant association with female life expectancy but not male
  - In the GLM analysis, unemployment becomes significant for males when controlling for other factors

**Effect Sizes (Odds Ratios)**:
- **Female**: Low GDP countries have 77% lower odds of high life expectancy
- **Male**: Low GDP countries have 93% lower odds of high life expectancy
- Safe water access shows the strongest effect for both genders

### Objective 3: Factors Influencing Infant Mortality

**Research Question**: What factors most significantly influence infant mortality rates?

**Methodology**:
- Count regression analysis (Poisson and Negative Binomial models)
- Overdispersion testing and model comparison
- Variables analyzed:
  - CO2 exposure percentage
  - Fertility rate
  - Sanitary expenses per GDP
  - Unemployment rate
  - Safe water access percentage
  - Immunization rate
  - Hospital beds per 1000 people

**Key Findings**:
- Negative Binomial model preferred over Poisson due to overdispersion
- Significant predictors identified through coefficient analysis
- Model explains substantial proportion of deviance in infant mortality

## Technical Implementation

### Required R Packages

```r
# Data manipulation and analysis
library(dplyr)
library(tidyr)

# Visualization
library(ggplot2)
library(corrplot)

# Statistical testing
library(binom)
library(exactci)
library(PropCIs)
library(epitools)
library(car)

# Advanced modeling
library(MASS)        # Negative binomial regression
library(survival)    # Survival analysis
library(survminer)   # Survival analysis visualization
library(caret)       # Machine learning utilities

# Geographic data
library(countrycode) # Country classification
```

### Data Preprocessing

1. **Missing Value Treatment**: Median imputation by country
2. **Outlier Handling**: 99th percentile capping for extreme values
3. **Categorical Variables**: Life expectancy and socioeconomic factors converted to meaningful categories
4. **Data Validation**: Complete case analysis after preprocessing

### Statistical Methods Used

- **Descriptive Statistics**: Summary statistics, frequency tables
- **Hypothesis Testing**: Chi-square, t-tests, ANOVA
- **Regression Analysis**: 
  - Logistic regression for binary outcomes
  - Poisson/Negative binomial for count data
- **Confidence Intervals**: Multiple methods for proportion estimation
- **Model Diagnostics**: Residual analysis, goodness-of-fit testing

## Key Visualizations

1. **Gender Analysis**:
   - Density plots comparing male vs female life expectancy
   - Box plots showing distributions by gender
   - Time series analysis of life expectancy trends
   - Geographic analysis of gender gaps by country

2. **Socioeconomic Analysis**:
   - Comparative bar charts by gender and economic factors
   - Proportion plots showing life expectancy categories
   - Faceted visualizations for multiple factor analysis

3. **Infant Mortality Analysis**:
   - Correlation matrices for predictor variables
   - Residual plots for model diagnostics
   - Distribution analysis of count variables

## Results Summary

### Main Conclusions

1. **Persistent Gender Gap**: Females consistently outlive males globally, with significant statistical evidence across multiple testing methods

2. **Economic Determinants**: GDP per capita emerges as the strongest predictor of life expectancy for both genders, with developing countries showing substantially lower life expectancy

3. **Infrastructure Importance**: Access to safe water and healthcare infrastructure (hospital beds) significantly impact both life expectancy and infant mortality

4. **Gender-Specific Vulnerabilities**: Males show stronger sensitivity to economic factors, while females show more sensitivity to social factors like unemployment

5. **Public Health Priorities**: The analysis identifies key intervention areas: economic development, water access improvement, and healthcare infrastructure development

## Limitations and Future Work

- **Temporal Analysis**: Future studies could incorporate time-series analysis for trend prediction
- **Causal Inference**: Current analysis shows associations; causal relationships would require experimental or quasi-experimental designs
- **Additional Variables**: Cultural, political, and conflict-related factors could provide additional insights
- **Regional Analysis**: Continent-specific analysis could reveal regional patterns and priorities

## File Structure

```
project/
├── global_health.csv              # Main dataset
├── Project_Objective 1.Rmd       # Gender differences analysis
├── Project_Objective 2.Rmd       # Socioeconomic factors analysis
├── Project_Objective 3.Rmd       # Infant mortality analysis
└── README.md                      # This file
```

## Usage

1. Ensure all required R packages are installed
2. Place the `global_health.csv` file in the working directory
3. Run each objective file sequentially or independently
4. Each file generates both statistical outputs and visualizations

## Authors

DANA4820 Course Project - Group 1

## License

This project is for educational purposes as part of academic coursework.