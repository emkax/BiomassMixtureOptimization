# Biomass Mixture Optimization using Genetic Algorithm and Machine Learning

## Overview

This project performs **biomass mixture optimization** using:

- Genetic Algorithm (GA) for mixture generation and optimization
- Machine Learning (XGBoost) for predicting:
  - Higher Heating Value (HHV)
  - Efficiency
  - Emission
- Mixture Design principles using weighted mass balance

The system generates optimal biomass blends while maintaining:

$$
x_1 + x_2 + x_3 + \dots + x_n = 1
$$

where:

- \(x_i\) = biomass fraction
- all fractions are non-negative
- total mixture equals 100%

---

# Features

- Biomass mixture optimization
- Sparse mixture generation
- Multi-objective optimization
- HHV prediction using machine learning
- Efficiency and emission prediction
- Weighted mass balance mixing
- Genetic Algorithm search
- Ranking of optimized mixtures
- Batch/vectorized computation
- Progress tracking using `tqdm`

---

# Methodology

## 1. Data Preprocessing

The dataset is cleaned by:

- removing duplicates
- handling missing values
- converting numeric columns safely
- generating derived features

Derived features:

- efficiency proxy
- emission proxy

---

## 2. Mixture Generation

The project uses sparse Dirichlet sampling to generate realistic biomass combinations:

$$
x \sim Dirichlet(\alpha)
$$

with small \(\alpha\) values to encourage sparse mixtures.

---

## 3. Weighted Mass Mixing

Mixture properties are computed using weighted averages:

$$
VM_{mix} = \sum_i x_i VM_i
$$

$$
C_{mix} = \sum_i x_i C_i
$$

and similarly for:

- FC
- ASH
- H
- O
- N
- S

---

## 4. Machine Learning Prediction

A multi-output XGBoost model predicts:

- HHV
- Efficiency
- Emission

Input features:

- VM
- FC
- ASH
- C
- H
- O
- N
- S

---

## 5. Genetic Algorithm Optimization

The GA performs:

- population initialization
- crossover
- mutation
- elitism
- selection

Objective function:

$$
Score =
1.0(HHV)
-2.0(Emission)
+0.5(Efficiency)
$$

The algorithm evolves biomass mixtures toward optimal performance.

---

# Technologies Used

- Python
- Pandas
- NumPy
- Scikit-learn
- XGBoost
- tqdm

---

# Example Output

```text
=== BEST MIXTURE ===

willow: 27.79%
pine sawdust: 9.71%
fir mill residue: 7.82%
spruce wood: 7.31%
bamboo whole: 6.75%

=== PERFORMANCE ===

HHV: 19.94
Efficiency: 47.59
Emission: 8.70
Score: 26.32
```

---

# Key Concepts

## Mixture Constraint

All biomass fractions satisfy:

$$
\sum_i x_i = 1
$$

ensuring valid mixture compositions.

---

## Weighted Mass Principle

Each mixture property is computed through mass-weighted averaging.

---

## Surrogate Modeling

The machine learning model acts as a surrogate predictor for:

- HHV
- efficiency
- emission

allowing rapid optimization without expensive physical simulations.

---

# Future Improvements

- NSGA-II multi-objective optimization
- Pareto front visualization
- Constraint-based optimization
- SHAP explainability
- Deep learning surrogate models
- Uncertainty-aware optimization
- Interactive dashboard

---

# Results

The optimization framework can:

- identify high-performance biomass blends
- reduce emission impact
- improve combustion efficiency
- rank thousands of candidate mixtures

---

# Installation

## Clone the Repository

```bash
git clone https://github.com/yourusername/biomass-mixture-optimization.git
cd biomass-mixture-optimization
```

## Install Dependencies

```bash
pip install -r requirements.txt
```

---

# requirements.txt

```txt
pandas
numpy
scikit-learn
xgboost
matplotlib
plotly
tqdm
```

---

# Usage

Run the optimization script:

```bash
python main.py
```

---

# License

This project is licensed under the MIT License.

---

# Author

Developed for biomass mixture optimization and machine learning research.