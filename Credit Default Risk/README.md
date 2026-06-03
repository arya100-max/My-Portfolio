# 📊 Predicting Credit Default Risk
<img src="Predicting credit risk analysis tools.png"></img>
## 📌 Project Overview

Banks and financial institutions face significant financial risk when borrowers fail to repay their loans — a situation known as **credit default**. This project uses machine learning to predict whether a borrower will experience **serious delinquency (90+ days past due)** within two years, helping financial institutions make more informed lending decisions.

---

## 🎯 Objective

- Predict credit default risk accurately using historical borrower data
- Compare the performance of multiple machine learning models
- Evaluate models using standard classification metrics
- Identify key factors that influence loan default

---

## 📁 Dataset

- **Source:** GiveMeSomeCredit (`GiveMeSomeCredit-training.csv`)
- **Records:** 74,829 entries
- **Target Variable:** `SeriousDlqin2yrs` — (1 = Default, 0 = No Default)
- **Class Distribution:** ~93.3% No Default | ~6.7% Default (Imbalanced)

### 🔢 Features

| Variable | Description | Type |
|----------|-------------|------|
| `RevolvingUtilizationOfUnsecuredLines` | Ratio of credit card balance to credit limit | Percentage |
| `age` | Age of borrower | Integer |
| `NumberOfTime30-59DaysPastDueNotWorse` | Times 30–59 days late (last 2 years) | Integer |
| `DebtRatio` | Monthly debt / gross monthly income | Percentage |
| `MonthlyIncome` | Monthly income of borrower | Real |
| `NumberOfOpenCreditLinesAndLoans` | Total open credit lines and loans | Integer |
| `NumberOfTimes90DaysLate` | Times 90+ days late | Integer |
| `NumberRealEstateLoansOrLines` | Number of mortgage/real estate loans | Integer |
| `NumberOfTime60-89DaysPastDueNotWorse` | Times 60–89 days late | Integer |
| `NumberOfDependents` | Number of dependents (excluding borrower) | Integer |

---

## 🛠️ Tech Stack

- **Language:** Python
- **Libraries:** Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn, Statsmodels

---

## 🔍 Project Workflow

### 1. Exploratory Data Analysis (EDA)
- Visualized class distribution, feature distributions, and missing value heatmaps
- Found right-skewed financial variables (income, debt ratio, credit utilization)
- Most borrowers are between 30–70 years old

### 2. Correlation & Multicollinearity Analysis
- Past payment behavior features had the highest correlation with default
- High multicollinearity detected between the three late-payment features (correlation ≈ 0.98–0.99)

### 3. Data Cleaning & Preprocessing
- Filled missing values using **median** (robust to outliers)
- Dropped redundant index column (`Unnamed: 0`)
- Removed highly multicollinear features using **VIF analysis**:
  - Dropped: `NumberOfTime30-59DaysPastDueNotWorse`, `NumberOfTime60-89DaysPastDueNotWorse`

### 4. Feature Selection & Scaling
**Final Features Used:**
- RevolvingUtilizationOfUnsecuredLines
- Age
- NumberOfTimes90DaysLate
- DebtRatio
- MonthlyIncome
- NumberOfOpenCreditLinesAndLoans
- NumberRealEstateLoansOrLines
- NumberOfDependents

Applied **StandardScaler** (mean = 0, std = 1) for Logistic Regression compatibility.

### 5. Train-Test Split
- **80%** Training | **20%** Testing
- Training set: 59,863 samples | Test set: 14,966 samples

---

## 🤖 Models Used

| Model | Description |
|-------|-------------|
| **Logistic Regression** | Binary classification; simple and interpretable |
| **Decision Tree** | Rule-based; captures non-linear patterns |
| **Random Forest** | Ensemble of trees; reduces overfitting |
| **Gradient Boosting** | Sequential boosting; highest predictive performance |

---

## 📈 Model Results

| Model | Accuracy |
|-------|----------|
| Logistic Regression | 93.45% |
| Decision Tree | 93.46% |
| Random Forest | 93.63% |
| **Gradient Boosting** | **93.63%** |

### Classification Metrics Summary

| Model | Precision (Default) | Recall (Default) | F1-Score (Default) |
|-------|---------------------|------------------|--------------------|
| Logistic Regression | 0.53 | 0.02 | 0.03 |
| Decision Tree | 0.50 | 0.19 | 0.28 |
| Random Forest | 0.86 | 0.02 | 0.04 |
| **Gradient Boosting** | **0.56** | **0.14** | **0.22** |

---

## 🏆 Best Model: Gradient Boosting

> **Gradient Boosting** was selected as the best model because it identifies the **highest number of defaulters** — which is the primary objective in credit risk analysis. Detecting risky borrowers is more important than overall accuracy in this domain.

---

## 📊 Key Insights

- The dataset is **highly imbalanced** (~93% non-default), causing most models to predict the majority class
- **Past payment history** (90+ days late) is the strongest predictor of default
- **Credit utilization**, **debt ratio**, and **income stability** are also influential
- Tree-based models outperform Logistic Regression, suggesting **non-linear relationships** in the data
- Techniques like **SMOTE** or **threshold tuning** could further improve minority class detection

---

## 📂 Project Structure

```
Credit-Default-Risk/
│
├── Predicting_Credit_Default_Risk.ipynb   # Main Jupyter Notebook
├── GiveMeSomeCredit-training.csv          # Dataset
└── README.md                              # Project documentation
```

---

## 🚀 How to Run

```bash
# 1. Clone the repository
git clone https://github.com/arya100-max/My-Portfolio/credit-default-risk.git

# 2. Navigate to the project folder
cd Credit-Default-Risk

# 3. Install required libraries
pip install pandas numpy matplotlib seaborn scikit-learn statsmodels

# 4. Open the notebook
jupyter notebook Predicting_Credit_Default_Risk.ipynb
```

---

## 👤 Author

**Devesh Chaudhary**  
[GitHub](https://github.com/arya100-max/) | [LinkedIn](https://www.linkedin.com/in/devesh--chaudhary/)