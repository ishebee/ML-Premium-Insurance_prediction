
# Insurance Premium Prediction App

This project is a complete end-to-end data science solution designed to predict health insurance premiums using machine learning. Built under mentorship from **Codebasics.io**, the project involves extensive data cleaning, segmentation, feature engineering, regression modeling, and an interactive **Streamlit web application** for deployment.
Check out the full story here - https://portfolio.ishebee.in/2025/05/25/predicting-insurance-premiums-with-machine-learning/

---

## Project Structure

- `Prem_Insurance_Prediction.ipynb`: Initial data cleaning, EDA, and modeling.
- `data_segmentation.ipynb`: Splits the data into two subsets based on age (<=25 and >25).
- `Prem_Insurance_Prediction_young.ipynb`: Modeling for young customers (≤25) – low accuracy without GR.
- `Prem_Insurance_Prediction_young_with_gr.ipynb`: Modeling with added `genetical_risk` feature for improved accuracy.
- `Prem_Insurance_Prediction_rest.ipynb`: Modeling for customers aged >25 – high accuracy.
- `Prem_Insurance_Prediction_rest_with_gr.ipynb`: Testing GR impact on older customers (slight improvement).
- `main.py`: Streamlit app script.
- `prediction_helper.py`: Internal helper utilities for preprocessing and feature transformation.

---

## Data Overview

- Dataset: `premiums.xlsx` (~50,000 rows)
- Target: `annual_premium_amount`
- Features: Age, Gender, Region, Marital Status, Number of Dependents, BMI Category, Smoking Status, Employment Status, Income, Medical History, Insurance Plan, Genetic Risk (added later)

---

## Modeling Strategy

1. **Segmentation by Age**:
   - Young Group (≤25): Initially low model accuracy (~60%), improved significantly with `genetical_risk`.
   - Older Group (>25): Performed well (~95% accuracy) with and without GR.

2. **Genetical Risk Feature**:
   - Engineered using weights for medical history conditions.
   - Added as a normalized numeric feature.
   - Significantly boosted young group model performance to ~98–99% R².

3. **Final Models**:
   - Two Linear Regression models trained on segmented datasets.
   - Selected based on user age during prediction.

---

## Evaluation Results

| Model | Dataset | Train R² | Test R² |
|-------|---------|----------|---------|
| Initial Combined | All | ~0.85 | ~0.85 |
| Young (no GR) | Age ≤ 25 | 0.60 | 0.62 |
| Young (with GR) | Age ≤ 25 | 0.988 | 0.989 |
| Older (no GR) | Age > 25 | 0.954 | 0.953 |
| Older (with GR) | Age > 25 | 0.957 | 0.960 |

---

## Streamlit Web Application

The final solution is deployed as a web app using **Streamlit**, allowing users to:

- Input personal and medical details
- Automatically route inputs to the appropriate age-based model
- Get real-time insurance premium predictions

### App Features:
- Clean UI with form inputs for all features
- Internal logic computes genetic risk score
- Real-time feedback and formatted prediction output
- Intuitive layout for both young and older users
- Seamlessly handles segmentation and preprocessing

**Note**: The app can be deployed on [Streamlit Cloud](https://streamlit.io/cloud) or run locally with:

```bash
streamlit run main.py
```

---

## Requirements

- Python 3.8+
- Libraries:
  - `pandas`
  - `numpy`
  - `scikit-learn`
  - `streamlit`
  - `xgboost` (optional for experimentation)

Install with:

```bash
pip install -r requirements.txt
```

---

## Highlights

- Segment-based modeling strategy
- Domain-informed feature engineering
- Linear models outperform complex ones when features are right
- Complete ML lifecycle from data to web deployment
- Educational and interactive user experience via Streamlit
