# Yield Curve Reconstruction using the CIR Model: Calibration, Factor Analysis, and Machine Learning Benchmarks

## Overview

This project explores the reconstruction of the Treasury yield curve using the **Cox-Ingersoll-Ross (CIR)** short-rate model. Given only the observed **3-Month Treasury yield**, the objective is to reconstruct the remaining maturities of the yield curve while maintaining both predictive accuracy and financial interpretability.

In addition to implementing the CIR framework, the project investigates the latent factor structure of the yield curve through **Principal Component Analysis (PCA)** and benchmarks the results against several machine learning models.

---

## Objectives

- Implement the Cox-Ingersoll-Ross (CIR) interest rate model.
- Calibrate model parameters using historical yield data.
- Reconstruct the yield curve from the observed 3-Month yield.
- Analyze the latent structure of the term curve using PCA.
- Explore a PCA-based extension motivated by factor analysis.
- Compare model-based approaches with machine learning benchmarks.

---

## Methodology

### 1. CIR Yield Curve Reconstruction

The short rate is modeled using the CIR process:

\[
dr_t = \kappa(\theta-r_t)dt + \sigma\sqrt{r_t}dW_t
\]

where:

- **κ (Kappa)** : Mean reversion speed
- **θ (Theta)** : Long-run equilibrium rate
- **σ (Sigma)** : Volatility parameter

Using the closed-form CIR bond pricing equations, yields across multiple maturities are reconstructed from the observed short rate.

---

### 2. Calibration Strategy

Instead of fitting the short-rate path directly, the CIR parameters were calibrated by minimizing **yield curve reconstruction error** on the training dataset.

This calibration approach aligns the optimization objective with the final prediction task and significantly improves out-of-sample performance.

---

### 3. PCA-Based Yield Curve Analysis

Principal Component Analysis (PCA) was used to investigate the underlying structure of the term curve.

Key findings:

- **PC1 (Level Factor)** explains the vast majority of yield curve variation.
- **PC2 (Slope Factor)** captures steepening and flattening movements.
- Two factors explain nearly all observed yield curve dynamics.

This analysis provides insight into the strengths and limitations of single-factor term structure models.

---

### 4. PCA-Based Extension

A leakage-free extension was developed by:

1. Extracting latent PCA factors from training data.
2. Learning a mapping from the observed 3-Month yield to the latent factors.
3. Reconstructing the yield curve through inverse PCA transformation.

---

### 5. Machine Learning Benchmarks

The following models were evaluated for comparison:

- Ridge Regression
- Lasso Regression
- ElasticNet
- K-Nearest Neighbors (KNN)
- Gradient Boosting
- XGBoost

---

## Results

### CIR Model Performance

| Metric | Value |
|----------|---------|
| Train R² | 0.9750 |
| Test R² | 0.8945 |

---

### PCA Extension Performance

| Metric | Value |
|----------|---------|
| Test R² | 0.7855 |

---

### Machine Learning Benchmark

| Model | R² Score |
|---------|---------|
| Ridge Regression | **0.9462** |
| ElasticNet | 0.8914 |
| Lasso | 0.8895 |
| Gradient Boosting | 0.8020 |
| XGBoost | 0.8010 |
| KNN | 0.3779 |

---

## Key Insights

- A calibrated CIR framework can achieve strong yield curve reconstruction performance while maintaining financial interpretability.
- The yield curve exhibits a dominant **Level–Slope** factor structure.
- Single-factor models effectively capture level dynamics but struggle to fully explain slope movements at longer maturities.
- PCA provides valuable explanatory insight into the latent structure of the term curve.
- Regularized linear models, particularly Ridge Regression, achieve the highest predictive accuracy in this setting.

---

## Technologies Used

- Python
- NumPy
- Pandas
- SciPy
- Scikit-Learn
- Matplotlib
- XGBoost

---

## Future Work

Potential extensions include:

- Two-Factor CIR Models
- CIR++
- Kalman Filter State-Space Estimation
- Regime-Switching Interest Rate Models
- Dynamic Nelson-Siegel Framework

---

## Author

**Ashutosh Gupta**  
Indian Institute of Technology Roorkee
