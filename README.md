# BAML-coursework

**Business Analytics and Machine Learning (BAML)** — coursework completed during the **Summer Semester 2025** at the **University of Freiburg**.
Final grade: **2.3** (ranked 3rd in the cohort that semester).

---

## What this project demonstrates

This repository walks through a complete, practical data-science pipeline — from raw data all the way to interpretable machine-learning models — using real and synthetic datasets. Across the notebooks it shows the ability to:

- **Query relational data with SQL** — filtering, aggregation, `GROUP BY` / `HAVING`, and multi-table joins over an e-commerce schema (via DuckDB + JupySQL).
- **Clean and wrangle messy real-world data** — fixing broken types, parsing dates, recoding categories, detecting and winsorizing outliers, and handling missing values with sensible imputation strategies.
- **Explore and visualize data** — summary statistics, histograms, scatter plots, grouped bar charts, and correlation matrices with `pandas` + `matplotlib`.
- **Build statistical / econometric models** — OLS and logistic regression, non-linear (quadratic) features, plus heteroscedasticity-robust (HC0/HC1) and clustered standard errors with `statsmodels`.
- **Train and evaluate ML models** — decision trees, random forests, and gradient boosting; cost-complexity pruning, cross-validation, and nested hyperparameter search with `scikit-learn`.
- **Handle imbalanced classification** — stratified CV, class weighting, over-/under-sampling, threshold tuning, and precision–recall / AUPRC evaluation on a credit-card fraud dataset.
- **Explain black-box models** — built-in feature importance plus **LIME** and **SHAP** (permutation & TreeExplainer) to interpret individual predictions.

**Tech stack:** Python · pandas · NumPy · matplotlib · scikit-learn · statsmodels · DuckDB / JupySQL · LIME · SHAP · Jupyter / Google Colab.

> Most notebooks load their datasets directly from this repository's raw GitHub URLs, so they run top-to-bottom in Colab or Jupyter with no manual downloads.

---

## Repository structure

The folders follow a natural progression: **access → clean → model → explain**.

### 📁 `SQL/`
Hands-on SQL over a small e-commerce database (`customers`, `orders`, `products`, `suppliers`, `addresses`).
- **`SQL.ipynb`** — runs SQL against CSVs in-notebook with **DuckDB + JupySQL** (`%%sql`). Covers filtering and sorting, date-range queries, revenue aggregation per customer / product / supplier / country, `GROUP BY` + `HAVING`, and multi-table `JOIN`s.
- **`datas/`** — the five source CSV tables.

### 📁 `Bone Mineral Density database/`
Data-cleaning fundamentals on a deliberately "broken" clinical dataset.
- **`BMD.ipynb`** — type coercion (e.g. `"fifty"` → `50`), datetime parsing and length-of-stay computation, missing-value imputation, outlier handling via 95% winsorization of bone-mineral-density, feature creation (BMI), and EDA (boxplots, bar charts by sex/fracture, correlation plot).
- **`bmd_broken_with_dates.csv`** — raw input · **`bmd_cleaned.csv`** — cleaned output.

### 📁 `Melbourne Housing dataset/`
A full, end-to-end data-wrangling pipeline that produces the clean housing data reused by later notebooks.
- **`MH.ipynb`** — dropping zero-variance/duplicate columns, renaming and unifying columns, recoding categoricals (`Type`, `Car`), outlier detection + winsorization (Rooms, Landsize, BuildingArea), missing-data handling (drop rows without price, a `Car_Missing` flag, mode-imputation of bedrooms by property type), feature engineering (distance to the CBD), CSV export, and a visualization section (histograms, scatter, grouped bar plots).
- **`melbourne_housing.csv`** — raw input · **`melbourne_clean.csv`** — cleaned output.

### 📁 `Regressions/`
Statistical and econometric modeling with `statsmodels`.
- **`RM.ipynb`** — OLS regression on the advertising dataset (with standardized coefficients), logistic regression on a bank-marketing dataset, quadratic features and a non-linear decision boundary ("Japanese flag"), **heteroscedasticity-robust standard errors** (HC0/HC1) with residual diagnostics, and **clustered standard errors** (by suburb) on the Melbourne housing data.
- **`datasets/`** — advertising, bank, Melbourne, and a standard-errors example.

### 📁 `Decision Trees/`
Tree-based models, from a single interpretable tree to ensembles.
- **`RF.ipynb`** — decision-tree decision boundary and `plot_tree` visualization on a 2-D dataset, **cost-complexity pruning** and a `max_depth` × `ccp_alpha` validation grid, **random forests on imbalanced credit-card fraud** (stratified CV, entropy criterion, `balanced` / `balanced_subsample` class weights, over-/under-sampling, prediction-threshold tuning, and a custom AUPRC-based CV routine), and **Melbourne house-price regression** with nested-CV `GridSearchCV` + gradient boosting.
- **`datasets/`** — `df_xai.csv`, `creditcard_processed.csv`, `melbourne_clean.csv`.

### 📁 `Explainable AI/`
Interpreting black-box models trained on four different datasets (spiral, Melbourne housing, credit-card fraud, diabetes).
- **`XAI.ipynb`** — trains random-forest classifiers/regressors, then explains them with **built-in feature importance**, **LIME** (tabular explanations for classification *and* regression, comparing correctly vs. incorrectly predicted points and hand-crafted instances), and **SHAP** (both permutation `Explainer` and `TreeExplainer`, with waterfall plots).
- **`datasets/`** — `creditcard_processed.csv`, `melbourne_clean.csv`.

---

*Last updated: August 2026*
