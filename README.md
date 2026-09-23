# Skillset-Go-EduTech-AIML-Week1-Foundation-Phase-Python Mathematics & Machine Learning Foundations

A complete, executed submission for **Week 1 (Foundation Phase)** of the Skillset Go EduTech AI/ML 4-Week Practical Learning Track. The submission covers Python fundamentals, real-world data cleaning and exploratory data analysis, applied mathematics for machine learning, and two trained Scikit-learn models — one regression and one classification.

## Project Overview

Week 1 of the AI/ML track builds the foundational skills needed before moving into deep learning (Week 2 onward): solid Python fluency, the ability to clean and explore messy real-world data, the mathematical grounding behind ML algorithms, and hands-on experience training and evaluating baseline models with Scikit-learn.

This repository contains four Jupyter notebooks, each mapped to one official task from the track roadmap, all executed end-to-end so that every printed value, table, and chart is a real, reproducible result rather than placeholder text.

## Key Features

- Eight core Python topics solved with working, demonstrated code
- A real clinical dataset (Breast Cancer Wisconsin) deliberately corrupted with missing values, duplicates, and outliers, then cleaned using Pandas and NumPy
- Full exploratory data analysis with Matplotlib visualizations (class balance, distributions, boxplots, correlation heatmap)
- Hand-worked math problems in statistics, probability, linear algebra, and calculus, each verified numerically
- Two trained and evaluated Scikit-learn models: Linear Regression (diabetes progression) and Logistic Regression (breast cancer diagnosis)
- The cleaned dataset from the EDA task is reused directly as the training data for the classification model, linking Task 1.2 and Task 1.4 into one pipeline
- Google Colab / Jupyter compatible / VS Code
- Lightweight, dependency-light Python implementation

## Technologies Used

- **Python** — Programming language
- **NumPy** — Numerical and array operations
- **Pandas** — Data cleaning and tabular analysis
- **Matplotlib** — Data visualization
- **Scikit-learn** — Machine learning models, preprocessing, and evaluation metrics
- **Jupyter Notebook / Google Colab** — Development and execution environment

## Task Workflow

### 1. Python Fundamentals Assignment
Solved exercises covering variables and type casting, loops (FizzBuzz, nested patterns), functions (recursion, `*args`/`**kwargs`), list comprehensions and custom sorting, dictionary-based frequency counting, object-oriented programming (inheritance with a bank account model), file handling (write/read with error handling), and custom exception classes.

### 2. Data Cleaning & EDA
The clean Breast Cancer Wisconsin dataset is intentionally corrupted with missing values, duplicate rows, and injected outliers to create a realistic cleaning problem. Missing values are handled with median imputation, duplicates are dropped, and outliers are detected and capped using the IQR method. The cleaned data is then explored through class-balance plots, distribution histograms, a diagnosis-wise boxplot, and a feature correlation heatmap, with key findings summarized at the end.

### 3. Math for ML Practice Set
Worked problems across four areas used throughout the deep-learning phases of the track: descriptive statistics (mean, median, mode, variance, standard deviation), Bayesian probability (a medical-testing example), linear algebra (matrix multiplication, eigenvalues/eigenvectors, vector norms and cosine similarity), and calculus (the sigmoid derivative and a manual gradient-descent walkthrough). Each hand-derived solution is verified numerically with NumPy.

### 4. Two ML Models with Scikit-learn
- **Regression:** Linear Regression trained on the `diabetes` dataset (loaded directly from Scikit-learn) to predict disease progression, with standardized features and an 80/20 train/test split. Evaluated using MAE, RMSE, and R².
- **Classification:** Logistic Regression trained on `breast_cancer_cleaned.csv` — the same cleaned dataset produced in Task 2 — using a stratified 80/20 split to preserve class balance. Evaluated using accuracy, precision, recall, F1-score, and a confusion matrix.

## Project Structure

```
Week1-Foundation-Phase/
│
├── 1_python_fundamentals.ipynb
├── 2_data_cleaning_eda.ipynb
├── 3_math_for_ml.ipynb
├── 4_ml_models_sklearn.ipynb
├── breast_cancer_cleaned.csv
├── eda_overview.png
├── eda_boxplot.png
├── eda_correlation.png
├── regression_actual_vs_predicted.png
├── classification_confusion_matrix.png
├── week1_log.txt
└── README.md
```

## Installation

Clone the repository:

```
git clone https://github.com/Prithyadarshan/Week1-Foundation-Phase.git
```

Navigate to the project directory:

```
cd Week1-Foundation-Phase
```

Install the required dependencies:

```
pip install numpy pandas matplotlib scikit-learn jupyter
```

## How to Run

**Step 1: Open a Notebook**
Open any of the four `.ipynb` files using Google Colab or Jupyter Notebook.

**Step 2: Run the Cells**
Execute the cells sequentially from top to bottom. Task 2 must be run before Task 4, since Task 4's classification model reads `breast_cancer_cleaned.csv`, which Task 2 generates.

**Step 3: View the Results**
Each notebook prints its own evaluation output inline, and Tasks 2 and 4 additionally save chart images to the project folder.

## Output

**breast_cancer_cleaned.csv**
The fully cleaned dataset (missing values imputed, duplicates removed, outliers capped) produced by Task 2 and reused in Task 4.

**eda_overview.png / eda_boxplot.png / eda_correlation.png**
Visualizations of class balance, feature distributions, and correlations from the EDA task.

**regression_actual_vs_predicted.png**
Actual-vs-predicted scatter plot for the diabetes progression regression model.

**classification_confusion_matrix.png**
Confusion matrix for the breast cancer diagnosis classification model.

## Applications

- Foundational ML project structuring and documentation
- Real-world dataset cleaning and preprocessing workflows
- Exploratory data analysis for medical/clinical datasets
- Baseline model benchmarking before deep learning
- Reusable groundwork for the CNN and TensorFlow tasks in Weeks 2–3

## Concepts Demonstrated

- Python Programming Fundamentals
- Object-Oriented Programming
- Data Cleaning and Preprocessing
- Exploratory Data Analysis
- Descriptive Statistics and Probability
- Linear Algebra for Machine Learning
- Differential Calculus and Gradient Descent
- Supervised Learning: Regression and Classification
- Model Evaluation Metrics

## Future Enhancements

- Cross-validation instead of a single train/test split
- Regularized models (Ridge/Lasso regression, L2-penalized logistic regression)
- Non-linear models for comparison (Random Forest, Gradient Boosting)
- Automated data-quality reporting for the cleaning pipeline
- Hyperparameter tuning ahead of Week 2's PyTorch experiments

## Limitations

- The EDA and classification tasks use a single reference dataset (Breast Cancer Wisconsin); results may not generalize to other clinical datasets without re-cleaning.
- Outlier and missing-value injection in Task 2 is synthetic, simulating real-world messiness rather than being drawn from an inherently messy source.
- Models in Task 4 are intentionally simple baselines (Linear/Logistic Regression) and are not yet tuned or cross-validated.

## Learning Outcome

This submission provides practical, end-to-end experience across the full foundation of an AI/ML workflow — from core Python programming, through cleaning and exploring a real dataset, to the underlying mathematics of machine learning, and finally training and evaluating baseline supervised learning models. It demonstrates how these foundational skills connect directly into the deep learning and applied AI work planned for the remaining weeks of the track.
