# 🪐 Exoplanet Hunter — NASA Kepler Data Analysis

**Google Advanced Data Analytics Certificate — Capstone Project**

[![Python](https://img.shields.io/badge/Python-3.10-blue)](https://python.org)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-1.3-orange)](https://scikit-learn.org)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)

---

## Overview

Advanced analytics project applying statistical analysis, machine learning, and data visualization to the NASA Kepler Space Telescope dataset — 9,564 Kepler Objects of Interest (KOI) from the DR25 catalog.

**Central question:** *What physical and orbital characteristics distinguish confirmed exoplanets from false positives, and can we classify unconfirmed candidates?*

---

## Dataset

**Source:** NASA Exoplanet Archive — Kepler Objects of Interest (KOI) Catalog, DR25  
**Reference:** Thompson et al. 2018, ApJS, 235, 38  
**URL:** https://exoplanetarchive.ipac.caltech.edu

| Class | Count | % |
|-------|-------|---|
| Confirmed Planets | 2,345 | 24.5% |
| False Positives | 5,017 | 52.5% |
| Candidates | 2,202 | 23.0% |
| **Total** | **9,564** | |

---

## Structure

```
kepler-exoplanet-analysis/
│
├── kepler_exoplanet_analysis.ipynb   # Main analysis notebook
├── kepler_koi.csv                    # Dataset (DR25 statistics)
├── README.md
└── figures/
    ├── fig1_distribution.png
    ├── fig2_parameters.png
    ├── fig3_habitable_zone.png
    ├── fig4_correlation.png
    ├── fig5_flags.png
    └── fig6_model_evaluation.png
```

---

## Key Results

| Model | AUC | Precision | Recall |
|-------|-----|-----------|--------|
| Logistic Regression | ~0.999 | 0.98 | 0.97 |
| Random Forest | ~0.999 | 0.99 | 0.98 |

- **14 potentially habitable-zone confirmed planets** identified
- **~30-35% of candidates** classified as likely planets by the model
- **koi_score** (NASA's disposition confidence) is the strongest single predictor
- Transit depth and planet radius are the clearest physical separators

---

## Techniques Applied

- Exploratory Data Analysis (EDA)
- Statistical hypothesis testing (Mann-Whitney U)
- Feature engineering (SNR proxy, orbital compactness, radius ratio)
- Binary classification (Logistic Regression, Random Forest)
- ROC/AUC evaluation
- Feature importance analysis

---

## Setup

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
jupyter notebook kepler_exoplanet_analysis.ipynb
```

---

## References

- Thompson et al. (2018). Planetary Candidates Observed by Kepler. VIII. *ApJS*, 235, 38
- NASA Exoplanet Archive: https://exoplanetarchive.ipac.caltech.edu
- Kepler Mission: https://www.nasa.gov/mission_pages/kepler

---

*Part of the Google Advanced Data Analytics Professional Certificate portfolio*
