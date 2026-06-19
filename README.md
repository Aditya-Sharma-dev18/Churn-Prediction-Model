# 📊 Telco Customer Churn Prediction

## 🎯 Project Overview
End-to-end machine learning model to predict customer churn for a telecom company. Built with **Random Forest** achieving **80% accuracy** and **0.84 ROC-AUC**.

---

## 🏆 Key Results
| Metric | Value |
|--------|-------|
| **Best Model** | Random Forest (Tuned) |
| **Accuracy** | 80.2% |
| **ROC-AUC** | 0.84 |
| **Precision** | 0.65 |
| **Recall** | 0.58 |
| **F1-Score** | 0.61 |

### 🔑 Top 3 Churn Drivers
1. **Contract Type** - Month-to-month customers churn 5x more
2. **Tenure** - New customers (<6 months) highest risk
3. **Monthly Charges** - High-billed customers are price-sensitive

---

## 📁 Project Structure
```
📁 telco-churn-prediction/
├── 📁 data/
│   └── Telco-Customer-Churn.csv
├── 📁 model/
│   └── churn_pipeline.joblib
├── 📁 notebook/
│   └── Churn_Prediction_Model.ipynb
├── 📁 src/
│   ├── predict.py
│   ├── train.py
│   └── utils.py
├── 📁 tests/
│   └── test_predict.py
├── app.py
├── requirements.txt
├── .gitignore
├── setup.py
└── README.md
```

---

## 🚀 How to Run

### 1. Clone the Repository
```bash
git clone https://github.com/Aditya-Sharma-dev18/Churn-Prediction-Model.git
cd Churn-Prediction-Model
```

### 2. Install Dependencies
```bash
pip install -r requirements.txt
```

### 3. Train the Model
```bash
python src/train.py
```

### 4. Run Predictions
```python
from src.predict import ChurnPredictor

predictor = ChurnPredictor()

customer = {
    'tenure': 2,
    'MonthlyCharges': 85,
    'Contract': 'Month-to-month',
    'OnlineSecurity': 'No',
    'TechSupport': 'No',
    'OnlineBackup': 'No',
    'Dependents': 'No',
    'Partner': 'No'
}

result = predictor.predict_single(customer)
print(f"Churn Probability: {result['probability']:.2%}")
print(f"Prediction: {result['prediction']}")
print(f"Risk Level: {result['risk_level']}")
print(f"Action: {result['action']}")
```

### 5. Run FastAPI Web App
```bash
python app.py
```
Visit `http://localhost:8000/docs` for Swagger UI.

### 6. Run Unit Tests
```bash
python -m pytest tests/
```

---

## 📈 Business Insights

| Churn Driver | Insight | Business Action |
|--------------|---------|-----------------|
| **Contract** | Month-to-month customers churn 5x more | Offer 10-15% discount for 1-year/2-year contracts |
| **Tenure** | Customers with <6 months tenure are highest risk | Onboarding calls & welcome offers in first 3 months |
| **MonthlyCharges** | High-billed customers (>$80) are price-sensitive | Loyalty rewards program for high-value customers |
| **OnlineSecurity** | Customers without security churn 2x more | Bundle OnlineSecurity free for first 3 months |
| **TechSupport** | Lack of support drives churn | Proactive outreach to customers without TechSupport |

---

## 🛠️ Tech Stack

| Category | Technologies |
|----------|--------------|
| **Language** | Python 3.10+ |
| **Data Processing** | Pandas, NumPy |
| **Machine Learning** | Scikit-learn (Random Forest) |
| **Model Comparison** | XGBoost, Logistic Regression |
| **Visualization** | Matplotlib, Seaborn |
| **Model Serialization** | Joblib |
| **Deployment** | FastAPI, Uvicorn |
| **Testing** | Pytest |

---

## 📊 Dataset

**Source:** [IBM Telco Customer Churn Dataset](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)

- **Rows:** 7,043 customers
- **Columns:** 21 features
- **Target:** Churn (Yes/No)
- **Churn Rate:** 26.6%

---

## 👨‍💻 Author

**Aditya Sharma**
- GitHub: [Aditya-Sharma-dev18](https://github.com/Aditya-Sharma-dev18)

---

## ⭐ Show Your Support

If you found this project helpful, please give it a ⭐ on GitHub!

---
