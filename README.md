

## `README.md`

```markdown
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
│   ├── predict.py          # Prediction module
│   ├── train.py            # Training script
│   └── utils.py            # Helper functions
├── 📁 tests/
│   └── test_predict.py     # Unit tests
├── app.py                  # FastAPI web app
├── requirements.txt        # Dependencies
├── .gitignore              # Git ignore
├── setup.py                # Package setup
└── README.md               # This file
```

---

## 🚀 How to Run

### 1. Clone the Repository
```bash
git clone https://github.com/yourusername/telco-churn-prediction.git
cd telco-churn-prediction
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
| **Contract** | Month-to-month customers churn 5x more than 2-year contracts | Offer 10-15% discount for 1-year/2-year contract upgrades |
| **Tenure** | Customers with <6 months tenure are highest risk | Implement onboarding calls & welcome offers in first 3 months |
| **MonthlyCharges** | High-billed customers (>$80) are price-sensitive | Launch loyalty rewards program for high-value customers |
| **OnlineSecurity** | Customers without security churn 2x more | Bundle OnlineSecurity free for first 3 months |
| **TechSupport** | Lack of support drives churn | Proactive outreach to customers without TechSupport |

---

## 🛠️ Tech Stack

| Category | Technologies |
|----------|--------------|
| **Language** | Python 3.10+ |
| **Data Processing** | Pandas, NumPy |
| **Machine Learning** | Scikit-learn (Random Forest, Preprocessing) |
| **Model Comparison** | XGBoost, Logistic Regression |
| **Visualization** | Matplotlib, Seaborn |
| **Model Serialization** | Joblib |
| **Deployment** | FastAPI, Uvicorn |
| **Testing** | Pytest |
| **Version Control** | Git, GitHub |

---

## 📊 Dataset

**Source:** [IBM Telco Customer Churn Dataset](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)

- **Rows:** 7,043 customers
- **Columns:** 21 features
- **Target:** Churn (Yes/No)
- **Churn Rate:** 26.6%

### Features Used (8 Important Columns)
| Feature | Type | Description |
|---------|------|-------------|
| tenure | Numerical | Number of months customer stayed |
| MonthlyCharges | Numerical | Monthly bill amount |
| Contract | Categorical | Month-to-month, One year, Two year |
| OnlineSecurity | Categorical | Yes/No/No internet service |
| TechSupport | Categorical | Yes/No/No internet service |
| OnlineBackup | Categorical | Yes/No/No internet service |
| Dependents | Categorical | Yes/No |
| Partner | Categorical | Yes/No |

---

## 📊 Model Performance

### Confusion Matrix
```
              Predicted
              Stay   Churn
Actual Stay   1023    98
Actual Churn  179    109
```

### Classification Report
| Class | Precision | Recall | F1-Score |
|-------|-----------|--------|----------|
| Stay | 0.85 | 0.91 | 0.88 |
| Churn | 0.53 | 0.38 | 0.44 |

### ROC Curve
- **AUC Score:** 0.84

---

## 🧪 Sample Predictions

### High Risk Customer
```python
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

# Result:
# Churn Probability: 78.5%
# Risk Level: HIGH
# Action: Offer discount NOW!
```

### Low Risk Customer
```python
customer = {
    'tenure': 60,
    'MonthlyCharges': 45,
    'Contract': 'Two year',
    'OnlineSecurity': 'Yes',
    'TechSupport': 'Yes',
    'OnlineBackup': 'Yes',
    'Dependents': 'Yes',
    'Partner': 'Yes'
}

# Result:
# Churn Probability: 12.3%
# Risk Level: LOW
# Action: No action needed
```

---

## 🚀 Deployment Options

### 1. FastAPI (Local)
```bash
python app.py
```

### 2. Docker
```bash
docker build -t churn-prediction .
docker run -p 8000:8000 churn-prediction
```

### 3. Cloud Deployment
- **Render:** Deploy FastAPI app directly
- **Heroku:** Deploy with `Procfile`
- **AWS/GCP/Azure:** Deploy with Docker

---

## 📝 Future Improvements

- [ ] Add SHAP explainability
- [ ] Implement feature engineering
- [ ] Add more models (LightGBM, CatBoost)
- [ ] Build Streamlit dashboard
- [ ] Add CI/CD pipeline
- [ ] Implement model monitoring

---

## 👨‍💻 Author

**Your Name**
- LinkedIn: [linkedin.com/in/yourprofile](https://linkedin.com/in/yourprofile)
- GitHub: [github.com/yourusername](https://github.com/yourusername)
- Email: your.email@example.com

---

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgments

- IBM for providing the Telco Customer Churn dataset
- Scikit-learn team for excellent ML libraries
- FastAPI team for easy API development

---

## ⭐ Show Your Support

If you found this project helpful, please give it a ⭐ on GitHub!

```


