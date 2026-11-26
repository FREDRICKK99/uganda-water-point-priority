# Predicting Priority Areas for New Rural Water Points in Uganda

**MSC 7103 Machine Learning, Practical Exam Project, Makerere University (2025/2026)**
Fredrick Tamale (2026/HD05/22751U, 2600722751). Case organisation: WaterAid Uganda.

Many rural water points in Uganda serve far more people than they were designed for. This project uses the public
**WPdx+** water point data to classify each rural water point's area as **Low / Medium / High priority** for an
additional water point. It compares logistic regression, random forest and XGBoost, explains the model with SHAP, and
maps priority by sub-county.

## Main results
- **Data:** 96,271 rural water points (78,005 with a pressure score) in 134 districts.
- **Evaluation:** on 27 districts held out completely, the selected model (logistic regression) reaches 82% accuracy,
  macro F1 0.82 and ROC-AUC 0.94. It finds 85% of high-priority water points.
- **Main drivers:** population within 1 km, the number of working water points within 1 km, and the water point's
  design capacity.
- **Map:** 260 of 1,252 sub-counties come out as high priority, mostly in Central and Eastern Uganda.

## Repository contents
| Path | What it is |
|---|---|
| `MSC7103_WaterPoints_Tamale.ipynb` | Main notebook (executed, with all outputs) |
| `data/wpdx_uganda.csv.gz` | Uganda extract of WPdx+ (downloaded 12 Nov 2026), reduced to the columns used |
| `figures/` | All figures produced by the notebook |
| `outputs/priority_map.html` | Interactive sub-county priority map (open in a browser) |
| `outputs/subcounty_priority.csv` | Ranked list of sub-counties with their priority score |
| `outputs/results.json` | Key numbers used in the report |

## How to run
```
pip install -r requirements.txt
jupyter notebook MSC7103_WaterPoints_Tamale.ipynb
```
Then choose **Kernel → Restart Kernel and Run All Cells** (about 3–5 minutes). The first cell installs any missing
packages automatically. All random seeds are fixed, so the results are reproducible.

## Data source
Water Point Data Exchange – Plus (WPdx+), https://www.waterpointdata.org/access-data/. Filtered to Uganda; the full
export (118 MB) was reduced to the columns used so that it fits within GitHub's file-size limit.
