# Telecom Churn Predictor

## Project Overview
A machine learning model that predicts which telecom customers are likely to churn, enabling proactive retention strategies and reducing customer attrition.

---

## Dataset
- **Source**: IBM Telco Customer Churn Dataset (Kaggle)
- **Size**: 7,043 customers, 21 features
- **Target Variable**: Churn (Yes/No)
- **Class Distribution**: ~73% No Churn, ~27% Churn (Imbalanced)

---

## Methodology

### 1. Data Preprocessing
- Converted `TotalCharges` to numeric, handled missing values
- Encoded categorical variables for modeling
- Created new features: `TenureGroup`, `AvgMonthlySpend`

### 2. Exploratory Data Analysis (EDA)
- **Key findings**: Contract type, tenure, and monthly charges are the strongest drivers of churn
- Month-to-month contracts have 45% churn vs 3% for 2-year contracts
- Customers with <12 months tenure are 3x more likely to churn

### 3. Feature Engineering
- Created `TenureGroup`: 0-1yr, 1-2yr, 2-4yr, 4-6yr
- Created `AvgMonthlySpend`: TotalCharges / Tenure
- Selected 11 most important features based on correlation analysis

### 4. Modeling
- **Model**: Logistic Regression (chosen for interpretability and performance)
- **Imbalance handling**: SMOTE (Synthetic Minority Over-sampling)
- **Feature scaling**: StandardScaler for normalization

### 5. Model Interpretation
- SHAP (SHapley Additive exPlanations) analysis for model explainability
- Identified top drivers of churn
- Individual customer explanations

---

## Results

| Metric | Value | Interpretation |
|--------|-------|----------------|
| **ROC-AUC** | 0.8283 | Excellent discrimination ability |
| **Recall (Churn)** | 0.80 | Finds 80% of actual churners |
| **Precision (Churn)** | 0.49 | 49% of churn alerts are correct |
| **F1-Score (Churn)** | 0.61 | Good balance of precision & recall |
| **Accuracy** | 72% | Overall correct predictions |

---

## Top Drivers of Churn

Based on SHAP analysis:

| Rank | Feature | Impact |
|------|---------|--------|
| 1 | **Contract** | Month-to-month contracts → Highest churn risk |
| 2 | **Tenure** | New customers (0-12 months) → High churn risk |
| 3 | **MonthlyCharges** | Higher bills → Higher churn risk |
| 4 | **InternetService** | Fiber optic → Higher churn risk |
| 5 | **OnlineSecurity** | No security → Higher churn risk |
| 6 | **TechSupport** | No support → Higher churn risk |

---

## How to Run

### Prerequisites
- Python 3.8+
- Jupyter Notebook / JupyterLab

### Setup
```bash
# 1. Clone the repository
git clone https://github.com/Chiboy588/telecom_churn_predictor.git
cd telecom_churn_predictor

# 2. Create and activate virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Run notebooks in order
jupyter notebook


## Data Source

The dataset is included in the repository under `data/raw/`.
- **Source**: IBM Telco Customer Churn Dataset (Kaggle)
- **Download URL**: https://www.kaggle.com/datasets/blastchar/telco-customer-churn
- **License**: CC0 (Public Domain)

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## Acknowledgments

- **IBM** for providing the Telco Customer Churn dataset
- **Kaggle** for hosting the dataset
- **My Instructor and Mentors** for their guidance and support
- **The Open Source Community** for the excellent libraries used in this project