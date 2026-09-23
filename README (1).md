# Week 1 — Foundation Phase: Python, Mathematics & Machine Learning Foundations
**Skillset Go EduTech — AI/ML 4-Week Practical Learning Track**

All four Week 1 tasks, complete and executed.

| Task | File | Deliverable type |
|---|---|---|
| 1.1 Python Fundamentals Assignment | `1_python_fundamentals.ipynb` | Solved exercises: variables/casting, loops, functions, lists, dictionaries, OOP, file handling, exceptions |
| 1.2 Data Cleaning & EDA | `2_data_cleaning_eda.ipynb` | Cleaned dataset (`breast_cancer_cleaned.csv`) + visualizations (class balance, distributions, boxplot, correlation heatmap) |
| 1.3 Math for ML Practice Set | `3_math_for_ml.ipynb` | Worked solutions: statistics, Bayesian probability, linear algebra, calculus/gradient descent — each verified numerically |
| 1.4 Two ML Models with Scikit-learn | `4_ml_models_sklearn.ipynb` | Linear Regression (diabetes progression) + Logistic Regression (breast cancer diagnosis), with preprocessing, train/test split, and evaluation metrics |

## Notes on data choices
- Task 1.2 and the classification half of Task 1.4 use the **Breast Cancer Wisconsin (Diagnostic)**
  dataset — a real clinical dataset of cell-nuclei measurements — chosen deliberately for its relevance
  to cancer/histopathology-adjacent classification work.
- Task 1.2's "real-world" messiness (missing values, duplicates, outliers) was intentionally injected into
  the clean source data so the cleaning workflow has genuine problems to solve; this is documented directly
  in the notebook.
- All notebooks were executed end-to-end in this environment — every printed value, table, and chart is a
  real, reproducible result, not placeholder text.

## How to run
Each notebook is self-contained. From this folder:
```
pip install numpy pandas matplotlib scikit-learn
jupyter nbconvert --to notebook --execute --inplace <notebook>.ipynb
```
or open directly in Jupyter/VS Code and run all cells.

## Suggested next step (per the track's submission standard)
Push this folder to a GitHub repository as the required evidence artifact for Week 1, with this README
as the top-level summary.
