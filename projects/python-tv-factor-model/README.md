
# Time-Varying Factor Loadings: Macro-Financial Analysis

This repository implements a **Time-Varying Factor Model** estimated in Python. The framework tracks the evolution of latent structural relationships in macro-financial time series using local kernel-based estimation techniques. The analysis focuses on identifying how the impact of underlying factors changes across different economic regimes.

## Project Overview
The core objective is to relax the assumption of constant factor loadings, allowing the model to capture structural breaks and evolving dynamics in the euro-area macro-financial landscape. By utilizing local weighting, the model extracts time-specific latent structures that are not captured by traditional static PCA or factor models.

### Key Methodologies
**Kernel-Based Estimation:** Employs local weighting functions to estimate factor loadings at each point in time, allowing for smooth parameter evolution.
**Procrustes Alignment:** Implements factor space alignment to ensure that latent components are comparable across the entire time series.
**Information Criteria:** Features robust selection methods including **Bai & Ng (2002)** and **Alessi-Barigozzi-Capasso (ABC)** criteria to determine the optimal number of latent factors.
**Stability Testing:** Includes statistical tests for parameter time-variation based on **Su & Wang (2017)** to validate the necessity of the time-varying approach.

---

