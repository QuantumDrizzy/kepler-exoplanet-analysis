# 🪐 Exoplanet Hunter — NASA Kepler Data Analysis

**Dataset:** NASA Kepler Objects of Interest (KOI) — DR25 Catalog  
**Tools:** Python · Pandas · NumPy · Matplotlib · Seaborn · Scikit-learn

---

## Overview

Analysis of 9,564 Kepler Objects of Interest from the NASA DR25 catalog. The project covers statistical comparison of confirmed planets vs false positives, habitable zone identification, and binary classification using only physical observational parameters.

**Central question:** can we distinguish confirmed exoplanets from false positives using only raw physical and orbital measurements — without using NASA's own classification scores?

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

## Key Results

| Model | AUC | Balanced Accuracy |
|-------|-----|-------------------|
| Logistic Regression | ~0.91 | ~0.84 |
| Random Forest | ~0.94 | ~0.86 |

**Important methodological note:** `koi_score` and the `koi_fpflag_*` columns were deliberately excluded from the model. `koi_score` is NASA's own classification confidence — using it to predict the classification is circular reasoning (data leakage). The fp_flags are also derived judgments, not raw measurements. The models here classify using only physical and orbital observables.

An earlier version of this analysis achieved AUC ~0.999 by including `koi_score`. That result is methodologically wrong and has been corrected.

**Other findings:**
- Transit depth (`koi_depth`), planet radius (`koi_prad`) and impact parameter (`koi_impact`) are the strongest physical separators
- 14 confirmed planets fall within conservative habitable zone criteria (200K–400K equilibrium temperature, 0.25–4x Earth insolation flux)
- ~30% of the 2,202 candidates are classified as likely planets by the corrected model

---

## Structure

```
kepler-exoplanet-analysis/
├── kepler_exoplanet_analysis.ipynb   — main analysis notebook
├── kepler_koi.csv                    — NASA KOI dataset (DR25)
├── requirements.txt
└── figures/
    ├── fig1_distribution.png
    ├── fig2_parameters.png
    ├── fig3_habitable_zone.png
    ├── fig4_correlation.png
    ├── fig5_flags.png
    └── fig6_model_evaluation.png
```

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

*Part of a series of data science explorations on public scientific datasets.*  
*Previous: Global Seismic Activity (USGS + NOAA) · UFO Sightings (NUFORC) · Quantum Navigation & Magnetic Disruption (IGRF-14)*
