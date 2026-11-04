# Titanic Survival – Exploratory Data Analysis (EDA)

A beginner-friendly, step-by-step Exploratory Data Analysis of the classic Titanic passenger dataset, done in a Jupyter Notebook with Python. The notebook walks through data loading, cleaning, and univariate, bivariate and multivariate visualization to understand which factors relate to passenger survival.

##  Objectives

- Understand the structure and quality of the Titanic dataset
- Detect and handle missing values, duplicates and outliers
- Explore individual variables (univariate analysis)
- Explore relationships between variables and survival (bivariate analysis)
- Combine several variables in a single view (multivariate analysis)
- Learn which plot to use for which type of variable

##  Project Structure

```
.
├── Titanic_EDA.ipynb                 # Main analysis notebook
├── Titanic_Survival_Train.xls        # Dataset (not included – see "Dataset" below)
└── README.md
```

## 📊 Dataset

- **Source:** The Titanic training dataset (891 passengers), also available in Seaborn via `sns.load_dataset('titanic')` or on Kaggle's *Titanic – Machine Learning from Disaster* competition.
- **Size:** 891 rows × 11 columns (with `PassengerId` as the index).

| Column | Description |
|---|---|
| `Survived` | Target variable (0 = No, 1 = Yes) |
| `Pclass` | Passenger class (1st, 2nd, 3rd) |
| `Name` | Passenger name |
| `Sex` | Gender |
| `Age` | Age in years |
| `SibSp` | Number of siblings / spouses aboard |
| `Parch` | Number of parents / children aboard |
| `Ticket` | Ticket number |
| `Fare` | Ticket fare |
| `Cabin` | Cabin number |
| `Embarked` | Port of embarkation (C, Q, S) |

## Data Cleaning Summary

| Issue | Finding | Action taken |
|---|---|---|
| `Cabin` | ~77% missing (687 rows) | Column dropped |
| `Age` | ~20% missing (177 rows) | Imputed with the median (28.0) to avoid losing rows |
| `Embarked` | 2 missing rows | Rows dropped |
| Duplicates | 0 found | No action needed |

The notebook also compares survival rate and the age distribution *before* (dropping rows) and *after* (median imputation) handling missing Age values to show how the choice affects the analysis.

##  Analysis Performed

**Univariate analysis**
- Count plots for `Survived`, `Sex` (Seaborn, Matplotlib and Plotly versions) and `Embarked`
- Histograms and box plots for `Age` and `Fare` (including outlier checks)

**Bivariate analysis**
- Survival vs. passenger class (bar plot)
- Survival vs. fare (bar plot)
- Age vs. fare (scatter plot)
- Passenger class vs. age, split by survival (bar plot)
- Correlation heatmap of the numeric features

**Multivariate analysis**
- Pair plot of Age, Fare and Survived
- Scatter plot of Age vs. Fare with marker size driven by `Pclass`
- A 2×2 subplot dashboard combining several plots in one output

**Reference material inside the notebook**
- What EDA is, why it matters and how to perform it
- Types of variables (continuous, discrete, categorical)
- Which plot type to use for which variable combination
- Rules of thumb for missing-value handling and correlation strength

##  Key Observations

- Of the 891 passengers, about 38% survived (342 survived, 549 did not).
- Survival was strongly linked to gender: among the 889 passengers kept after cleaning, 231 of 312 women survived versus 109 of 577 men.
- Roughly 20% of ages and 77% of cabin values were missing, so data quality decisions had a real impact on the analysis.
- Fare is heavily right-skewed with a large number of high-value outliers (maximum ≈ 512).
- Most passengers boarded at Southampton (S), followed by Cherbourg (C) and Queenstown (Q).

