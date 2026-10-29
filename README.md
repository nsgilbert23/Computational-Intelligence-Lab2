# Lab 2 — Country Schools Dataset

**Course:** Computational Intelligence and Applications  
**Lab:** Data Preprocessing, Anomaly Detection, and Cluster Analysis  
**Environment:** Python / Google Colab

## Overview

This lab explores a county-level school installation dataset. It applies basic data preprocessing and two unsupervised learning experiments:

1. **Anomaly detection** using Isolation Forest to identify counties with unusual combinations of installation statistics.
2. **Cluster analysis** using K-Means to group counties with similar installation characteristics.

The notebook includes visualizations and evaluation measures to support interpretation. Anomalies are unusual observations, not necessarily data errors; clusters are data-driven groups, not predefined performance categories.

## Dataset

**File:** `Country Schools.csv`  
**Original size:** 50 rows × 8 columns

| Column | Meaning |
| --- | --- |
| `SNO` | County name (also includes an aggregate `TOTAL` row) |
| `TOTALSCHOOLS` | Total number of schools |
| `TotalSchoolsInstalled` | Schools with installations |
| `SchoolsPending` | Schools pending installation |
| `PercentageInstalled` | Percentage of schools installed |
| `InstalledLDDs` | Installed LDD count |
| `InstalledTDDs` | Installed TDD count |
| `FID` | Record identifier |

Two rows have no county name and one row contains aggregate totals. The analysis excludes these three rows, leaving **47 county records**.

## Repository contents

```text
Computational-Intelligence-Lab2/
├── README.md
├── Country Schools.csv
└── Lab_2_Country_Schools_Colab.ipynb
```

## Methods

### 1. Data preprocessing
- Inspect shape, data types, missing values, and duplicates.
- Remove two empty records and exclude the aggregate `TOTAL` row.
- Convert `PercentageInstalled` from percentage strings to numeric values.
- Explore feature distributions with boxplots.
- Standardize six numerical features using `StandardScaler`.

### 2. Anomaly detection
- Train an **Isolation Forest** on the standardized county-level features.
- Use `contamination=0.10` as an assumed anomaly proportion for the experiment.
- Inspect anomaly labels (`-1` for flagged observations, `1` for others) and anomaly scores.
- Visualize the flagged counties and compare their attributes.

### 3. Cluster analysis
- Test candidate numbers of clusters with the **Elbow Method** and **Silhouette Score**.
- Fit **K-Means** using the selected cluster count.
- Inspect county assignments and mean feature values by cluster.
- Evaluate clustering with the **Silhouette Score** and **Davies–Bouldin Index**.
- Visualize clusters using total schools and installed schools; the model itself uses six features.

## How to run in Google Colab

1. Open [Google Colab](https://colab.research.google.com/).
2. Choose **File → Upload notebook** and select `Lab_2_Country_Schools_Colab.ipynb`.
3. Run the notebook cells from top to bottom.
4. When prompted, upload `Country Schools.csv` from this repository.
5. Review the generated tables, plots, anomaly results, cluster summaries, and evaluation scores.

**Python packages:** `pandas`, `numpy`, `matplotlib`, `seaborn`, `scikit-learn` (normally available in Colab).

## Results and interpretation

The notebook computes results from the dataset when executed. Interpret:

- **Anomaly detection:** which counties were flagged and which measurements make them unusual.
- **Clustering:** the selected number of clusters, number of counties per cluster, and their distinguishing average values.
- **Evaluation:** a higher Silhouette Score generally indicates better separation; a lower Davies–Bouldin Index generally indicates better clustering under that metric.

Do not assume cluster numbers indicate “good” or “bad” performance without examining the cluster statistics. The notebook's outputs should be used for the final discussion and conclusions.

## Notes

- The source lab instructions refer to the *country schools dataset*; this repository uses the provided `Country Schools.csv` file.
- The aggregate `TOTAL` row is excluded to prevent it from distorting county-level analysis.
- Isolation Forest flags statistical anomalies; flagged counties require contextual interpretation.

## Submission

Submit the GitHub repository link according to the lecturer's instructions. Confirm that the notebook and dataset are committed and that the notebook runs successfully in Colab.

