# PEM Fuel Cell Performance Analysis

This dataset, from Nafion 112 membrane standard tests of PEM fuel cells in various operational conditions ([source](https://github.com/ECSIM/pem-dataset1/tree/master)), was analysed to explore relationships between `power_density`, `current_density`, and `cell_voltage`.

## Correlation Analysis

Using the `cor()` function in R with the Pearson method, a correlation matrix revealed strong relationships:

* `power_density` and `current_density`: strong positive correlation
* `power_density` and `cell-voltage`: moderate negative correlation
* `current_density` and `cell-voltage`: strong negative correlation

## Regression Model

The following  multiple linear regression model was applied:

```R
model <- lm(power_density ~ current_density + cell_voltage, data = data)
```

### Key findings:

* Adjusted R-squared: 0.767, indicating the model explains 76.7% of the variance in `power_density`
* F-statistic: 1071, p-value < 2.2e-16, showing the model is statistically significant overall

### Coefficients

1. Current Density:
   * Highly significant (p < 2e-16)
   * A strong positive relationship with `power_density`, where each unit increase in `current_density` corresponds to a 0.33-unit increase in `power_density`

2. Cell Voltage:
   * Significant (p = 0.0167)
   * A positive effect on `power_density`, where a one-unit increase in `cell_voltage` results in an 84.04-unit increase in `power_density`

## Assumption Checks

The model assumptions of linearity, constant variance, and normality of residuals were validated and found to hold.

## Implications

* Current Density: A primary driver of `power_density`, suggesting optimisation of `current_density` could significantly enhance fuel cell performance
* Cell Voltage: Maintaining higher voltages also contributes positively to `power_density`, though its relationship with `current_density` requires careful consideration

## Future Directions

The analysis is robust but could benefit from:

* Including additional variables (e.g., pressure, relative humidity) to improve accuracy
* Exploring non-linear relationships and interaction effects between predictors
readme-md.md
Displaying readme-md.md.
