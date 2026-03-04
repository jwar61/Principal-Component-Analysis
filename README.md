# Principal-Component-Analysis

# Statistical Modeling and Analysis of Fisheries Data

## Project Overview

This repository contains statistical analyses applied to fisheries data, including **Principal Component Analysis (PCA)** and **Multiple Linear Regression**. The analyses aim to understand relationships between fishing activities, catches, and economic variables.


## Methodologies

### 1. Principal Component Analysis (PCA)

PCA is a multivariate statistical technique used to reduce dimensionality while preserving maximum variance in the data.

#### Key Mathematical Concepts:

- **Data Standardization**
 `z_{ij} = \frac{x_{ij} - \bar{x}_j}{\sigma_j}`

- **Correlation Matrix**
`R_{jk} = \frac{Cov(z_j, z_k)}{\sigma_j \sigma_k}`


- **Spectral Decomposition**

`R v_k = \lambda_k v_k`
- **Factor Loadings**
`Loadings_{jk} = \sqrt{\lambda_k \cdot v_{jk}}`
- **Factor Scores**
`F_{ik} = \sum_{j=1}^{p} z_{ij} v_{jk}`


### PCA Results

| Axis | Eigenvalue | Variance | Cumulative |
|------|------------|----------|------------|
| 1 | 3.322 | 47.46% | 47.46% |
| 2 | 2.275 | 32.50% | 79.96% |
| 3 | 1.011 | 14.44% | 94.40% |

**Key Loadings (PC1):**
- Total_catch_specie: **0.926**
- Value_specie: **0.920**
- CompEspec: **0.673**

---

## Multiple Linear Regression

### Model


**Matrix form:** `Y = Xβ + ε`

**OLS Estimation:** `β̂ = (XᵀX)⁻¹XᵀY`

### Regression Results

**Model Fit:**
- R² = 0.202 (20.2%)
- F(7,350) = 12.62, p < 0.001
- n = 358 observations

### Significant Variables (p < 0.05)

| Variable | Coefficient | p-value | Effect |
|----------|------------|---------|--------|
| NbMonthlyFishingDaysPAB | -80.23 | 0.004 | Negative |
| Nombre cpue | +54.86 | <0.001 | Positive |
| CompEspec | +3553.35 | <0.001 | Positive |
| Total_catch_specie | -4209.34 | <0.001 | Negative |
| Value_specie | +1.00 | <0.001 | Positive |

**Non-significant:**
- NbrTotalMonthlyFishingDays (p=0.988)
- CapturesTotales (p=0.919)

pca_result <- PCA(data_scaled, graph = FALSE)
fviz_eig(pca_result)

# Regression
model <- lm(average_prix ~ ., data = your_data)
summary(model)
