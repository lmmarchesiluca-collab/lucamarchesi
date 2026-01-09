# Structural Macroeconometrics: Identification of Monetary Policy Shocks

This repository contains a full reproduction of the empirical framework in **Lakdawala (2019)**, centered on identifying monetary policy shocks using a **Structural Vector Autoregression with Instrumental Variables (SVAR-IV)** approach. The project implements the **Minimum Distance (MD)** estimation procedure following the Angelini & Fanelli (2019) framework to achieve partial identification of structural shocks.

## Project Overview
The core objective is to disentangle two dimensions of U.S. monetary policy:
1. **Target Shock:** Immediate changes in the federal funds rate.
2. **Path Shock (Forward Guidance):** Changes in the future path of interest rates.

Identification is achieved using high-frequency external instruments (proxies) and a specific structural restriction where the **Path Shock** is assumed to have no contemporaneous effect on the **Federal Funds Rate (FFR)** ($B_{1,2} = 0$).

## Key Features
* **SVAR-IV Identification:** Leverages external proxies for Target and Path factors to identify the structural impact matrix $B$.
* **Minimum Distance Estimation:** Instead of standard GMM or ML, the model minimizes the distance between sample moments (covariances of residuals and instruments) and the theoretical model.
* **Odyssean vs. Delphic Components:** Includes a specialized script (`MainCodeOdyssean.m`) to clean the Path instrument from its Delphic component, isolating "Odyssean" Forward Guidance shocks.
* **Advanced Inference:** Implements a Recursive **Wild Bootstrap** procedure and generates **Sup-T simultaneous bands** for Impulse Response Functions (IRFs).

---

## Repository Structure

```text
.
├── MainCode.m                # Baseline replication of Lakdawala (2019)
├── MainCodeOdyssean.m        # Scenario isolating Odyssean shocks (Path instrument cleaned)
├── Data/
│   └── all_data.mat          # Macroeconomic series (FFR, 1Y, log(CPI), log(IP))
├── Instruments/
│   └── TP1_instr.mat         # External proxies (Target and Path factors)
└── functions/                # Core library for MD estimation and SVAR logic
    ├── MinimumDistance_Partial_g2.m # MD objective function with Lakdawala zero restriction
    ├── MD_boot_target.m             # Objective function adapted for Bootstrap routines
    ├── buildPmatrix_vech_to_blocks.m# Mapping vech(Sigma) to block-specific vectors
    ├── DuplicationMatrixFunction.m  # Utilities for symmetric matrix vectorization
    ├── CommutationMatrixFunction.m  # Utilities for matrix commutation (vec-operator)
    ├── Likelihood_SVAR.m            # Log-Likelihood evaluation for identification checks
    ├── vech.m / vec.m               # Standard matrix vectorization utilities
    ├── func_zeta_theta.m            # Analytical mapping from theta to zeta moments; used for Jacobian rank condition and local identification checks
