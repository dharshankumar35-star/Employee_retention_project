# Employee Retention Prediction

> A machine learning system that predicts whether a data science professional is likely to seek a job change — built as a full end-to-end analytics project with EDA, model comparison, and an interactive Streamlit app.

---

## Overview

Employee attrition is a costly challenge for organizations. This project uses HR profile data to predict the likelihood of a candidate looking for a new job, enabling HR teams to proactively identify at-risk employees and take targeted retention actions.

The project covers the complete data science workflow: data exploration, preprocessing, feature engineering, multi-model training, evaluation, and deployment via a web app.

---

## Demo

Run the Streamlit app locally:

```bash
python -m streamlit run app.py
```

Input a candidate's profile — city, experience, education, company details, and training hours — and get an instant prediction with a retention action recommendation.

---

## Project Structure

```
Dharshan_BIA_project/
│
├── app.py                                      # Streamlit web app for interactive scoring
├── run_app.bat                                 # Windows launcher for the app
├── requirements.txt                            # Python dependencies
│
├── aug_train.csv                               # Training dataset (~19,000 rows)
├── aug_test.csv                                # Test dataset
│
├── Employee_Retention_Prediction.ipynb         # Full analysis notebook (EDA → modelling → evaluation)
├── Employee_Retention_Prediction_Report.docx   # Written project report
├── Employee_Retention_Prediction_Final.pptx    # Presentation deck
│
└── outputs/
    ├── models/
    │   └── best_model.pkl                      # Saved trained pipeline (used by app)
    ├── figures/                                # All EDA and evaluation charts
    ├── predictions/
    │   └── final_test_predictions.csv          # Predictions on the test set
    ├── model_comparison.csv                    # Model performance summary
    └── 01_data_quality_report.csv              # Data quality audit
```

---

## Model Results

Four classifiers were trained and compared on a validation split:

| Model               | Accuracy | F1 Score | ROC-AUC       |
|---------------------|----------|----------|---------------|
| XGBoost             | 79.4%    | 0.620    | **0.8167** ✅ |
| Random Forest       | 79.7%    | **0.632** ✅ | 0.8162     |
| LightGBM            | **79.9%** ✅ | 0.618 | 0.8139      |
| Logistic Regression | 77.1%    | 0.626    | 0.8080        |

XGBoost was selected as the deployment model based on the highest ROC-AUC score.

---

## Features Used

The model uses 14 input features engineered from the raw dataset:

| Feature | Description |
|---|---|
| `city` | Anonymised city code |
| `city_development_index` | Development index of the city (0–1) |
| `gender` | Candidate gender |
| `relevent_experience` | Whether the candidate has relevant experience |
| `enrolled_university` | University enrolment status |
| `education_level` | Highest education attained |
| `major_discipline` | Field of study |
| `company_size` | Size of current employer |
| `company_type` | Type of current employer |
| `training_hours` | Total training hours completed |
| `experience_num` | Years of experience (numeric, engineered) |
| `last_new_job_num` | Gap since last job change (numeric, engineered) |
| `training_per_experience` | Training hours per year of experience (engineered) |
| `is_fresher` | Flag for candidates with ≤1 year experience (engineered) |

---

## Setup & Installation

**1. Clone the repository**
```bash
git clone https://github.com/<your-username>/employee-retention-prediction.git
cd employee-retention-prediction
```

**2. Create and activate a virtual environment**
```bash
python -m venv venv
source venv/bin/activate        # macOS/Linux
venv\Scripts\activate           # Windows
```

**3. Install dependencies**
```bash
pip install -r requirements.txt
```

**4. Run the Streamlit app**
```bash
python -m streamlit run app.py
```

---

## Tech Stack

- **Language:** Python 3.10+
- **ML Libraries:** scikit-learn, XGBoost, LightGBM, imbalanced-learn
- **Data:** pandas, NumPy
- **Visualisation:** matplotlib, seaborn
- **App:** Streamlit
- **Serialisation:** joblib

---

## Dataset

The dataset is based on the [HR Analytics: Job Change of Data Scientists](https://www.kaggle.com/datasets/arashnic/hr-analytics-job-change-of-data-scientists) dataset from Kaggle. It contains anonymised profile information for data science professionals, with a binary target indicating job-seeking intent.

---

## Author

**Dharshan** — BIA Project Submission
