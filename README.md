# Water Network Leak Detection — Time-Aware Classification

A portfolio machine-learning project that evaluates whether published hourly anomaly scores can classify observations associated with recorded leak events in an urban water-network dataset.

> **Important:** This is **leak-proximity classification**, not a guaranteed real-time leak detector, production alarm, or early-warning system. `fault_d7 = 1` means an observation lies within approximately ±7 days before or after a recorded leak event.

## Final result

On the untouched future test period, the tuned Logistic Regression did **not** outperform the majority-class baseline.

| Metric | Baseline | Tuned Logistic Regression |
|---|---:|---:|
| Accuracy | **0.890** | 0.292 |
| Precision | 0.890 | **0.805** |
| Recall | **1.000** | 0.270 |
| Specificity | 0.000 | 0.469 |
| Balanced Accuracy | **0.500** | 0.369 |
| F1 | **0.942** | 0.404 |
| ROC-AUC | **0.500** | 0.310 |
| PR-AUC | 0.890 | 0.823 |

The main conclusion is deliberately honest: **these published anomaly scores, used this way, do not support reliable classification of later observations in this one-year dataset.**

## What this project demonstrates

- Time-aware exploratory data analysis
- Class-imbalance analysis
- Feature preparation
- Data-leakage prevention
- Chronological train/validation/test splitting
- Baseline classification
- Logistic Regression
- Random Forest
- HistGradientBoosting
- Accuracy, Precision, Recall, F1
- ROC-AUC and PR-AUC
- Specificity and balanced accuracy
- `TimeSeriesSplit`
- `GridSearchCV`
- Confusion-matrix analysis
- ROC and Precision-Recall curves
- Error analysis
- Feature importance
- Model reality checks
- Risk and limitation analysis

## Repository structure

```text
Water-Network-Leak-Detection/
├── 01_Notebook/       # Executed analytical notebook
├── 02_HTML_Report/    # Polished case-study report
├── 03_Data/           # Dataset and dataset documentation
├── 04_Figures/        # Reusable project figures
├── 05_Documentation/  # Detailed project README
├── requirements.txt
├── LICENSE
└── .gitignore
```

## Run the project

```bash
cd 01_Notebook
pip install -r ../requirements.txt
jupyter notebook Water_Network_Leak_Detection_Time_Aware_Classification.ipynb
```

Run the notebook from `01_Notebook` so its relative paths resolve correctly.

## Dataset

Dataset: *Hourly Anomaly Scores and Leak Labels from a Multi-Source Urban Water Distribution Network Dataset*

Zenodo DOI: `10.5281/zenodo.15096167`

The dataset is attributed under **CC BY 4.0**. See `03_Data/DATASET_README.txt` for dataset details and attribution information.

## Key limitation

The `fault_d7` label is a symmetric ±7-day event-proximity label rather than a forward-looking operational target. The final test period is also strongly class-imbalanced. Results should therefore **not** be interpreted as evidence of production-ready leak detection or generalized to another network, year, or operational setting.

See `05_Documentation/README.md` for the complete methodology, findings, limitations, and project documentation.
