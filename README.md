# SyriaTel Customer Churn Prediction

<h1 align="center">🎯 <span style="color:#2E86C1">SyriaTel Churn Prediction</span></h1>

<p align="center">
  <a href="https://colab.research.google.com/github/your-repo/SyriaTel_Churn_Prediction.ipynb"><img src="https://img.shields.io/badge/Open%20in-Colab-ff69b4.svg" alt="Open in Colab"/></a>
  <img src="https://img.shields.io/badge/Python-3.8+-blue.svg" alt="Python Version"/>
  <img src="https://img.shields.io/badge/Framework-scikit--learn-green.svg" alt="Scikit-Learn"/>
</p>

---

## 🌟 Overview

This notebook implements a complete **churn prediction** workflow for **SyriaTel** customers, empowering the business to:

* **Identify at-risk subscribers** before they leave.
* **Prioritize retention efforts** by predicted risk levels.
* **Optimize marketing spend** with data-driven thresholds.

Two models are evaluated:

1. **Logistic Regression**: A linear classifier offering interpretability and stable, generalized performance.
2. **Decision Tree**: A non-linear model capturing complex decision boundaries and delivering high recall on minority churn cases.

By comparing accuracy, precision, recall, and F1-score, this analysis selects the model that maximizes retention impact.

---

## 🗂️ Table of Contents

1. [Setup & Installation](#setup--installation)
2. [Open in Google Colab](#open-in-google-colab)
3. [Project Structure](#project-structure)
4. [Notebook Walkthrough](#notebook-walkthrough)

   * [Data Loading & Preprocessing](#1-data-loading--preprocessing)
   * [Exploratory Data Analysis](#2-exploratory-data-analysis)
   * [Model Training](#3-model-training)
   * [Evaluation & Visualization](#4-evaluation--visualization)
5. [Results & Insights](#results--insights)
6. [Next Steps & Deployment](#next-steps--deployment)

---

## 🚀 Setup & Installation

Follow these steps to run the notebook locally or in the cloud:

1. **Clone the repository**

   ```bash
   git clone https://github.com/your-repo/SyriaTel_Churn_Prediction.git
   cd SyriaTel_Churn_Prediction
   ```

2. **Create & activate a virtual environment**

   ```bash
   python3 -m venv venv
   source venv/bin/activate  # macOS/Linux
   venv\\Scripts\\activate  # Windows
   ```

3. **Install dependencies**

   ```bash
   pip install -r requirements.txt
   ```

4. **Launch Jupyter Notebook**

   ```bash
   jupyter notebook
   ```

---

## ☁️ Open in Google Colab

Instantly run the analysis in a managed environment:

[![Open in Colab](https://img.shields.io/badge/Open%20in-Colab-ff69b4.svg)](https://colab.research.google.com/github/your-repo/SyriaTel_Churn_Prediction.ipynb)

---

## 🏗️ Project Structure

```
├── data/                     # Raw CSVs and preprocessed datasets
├── notebooks/                # Main Jupyter notebooks
│   └── SyriaTel_Churn_Prediction.ipynb
├── src/                      # Helper modules (feature engineering, modeling)
├── images/                   # Generated plots for metrics & confusion matrices
│   ├── model_comparison.png
│   └── confusion_matrices.png
├── requirements.txt          # Python package dependencies
└── README.md                 # Overview and instructions
```

---

## 📓 Notebook Walkthrough

### 1. Data Loading & Preprocessing

* **Load raw usage and billing data**, inspect schema and missing values.
* **Impute or drop** missing entries based on feature importance.
* **Encode categorical variables** (e.g., contract type, payment method) into numeric representations.
* **Scale numerical features** (e.g., monthly charges, tenure) for model compatibility.

### 2. Exploratory Data Analysis

* **Univariate analysis** of key features: churn rates by contract type, tenure distribution.
* **Correlation heatmap** to detect multicollinearity and inform feature selection.
* **Class balance check**: quantify churn vs. non-churn instances to guide resampling or class-weight strategies.

### 3. Model Training

* **Split data** into training (80%) and testing (20%) sets with stratified sampling.
* **Define pipelines** for each classifier: preprocessing steps + model.
* **Hyperparameter tuning** with `GridSearchCV`:

  * Logistic Regression: regularization strength `C`.
  * Decision Tree: `max_depth`, `min_samples_leaf`, `criterion`.
* **Cross-validation** ensures robust metric estimates.

### 4. Evaluation & Visualization

* **Metric bar chart**: side-by-side comparison of Accuracy, Precision, Recall, and F1-score for each model.

  ![Metric Comparison](images/model_comparison.png)

* **Confusion matrices**: visualize True Positives, False Positives, False Negatives, and True Negatives for both models.

  ![Confusion Matrices](images/confusion_matrices.png)

* **Key takeaway**: Decision Tree reaches higher recall and F1, critical for catching churners.

---

## 📊 Results & Insights

* **Accuracy**: Both models score similarly, indicating overall predictive power.
* **Precision**: Logistic Regression excels at minimizing false alarms, essential when retention offers are costly.
* **Recall**: Decision Tree identifies more true churners, crucial for aggressive retention campaigns.
* **F1-Score**: Decision Tree achieves the best balance, justifying its selection.

> **Business Impact**: Adopting the Decision Tree model ensures SyriaTel flags the maximum number of at-risk customers, directly supporting revenue preservation efforts.

---

## 🔮 Next Steps & Deployment

1. **Threshold Calibration**

   * Analyze Precision–Recall curve to select the optimal probability cutoff based on the cost of outreach vs. value of retention.

2. **Pilot Study & A/B Testing**

   * Implement a controlled campaign to measure uplift, validate model predictions, and refine cost assumptions.

3. **Integration & Automation**

   * Embed the model in the CRM for daily scoring and trigger retention workflows automatically.

4. **Monitoring & Retraining**

   * Set up dashboards to track key metrics and detect data or performance drift.
   * Schedule quarterly retraining with fresh data and reassess hyperparameters.

5. **Documentation & Training**

   * Provide user guides for marketing and data teams on interpreting churn scores and executing campaigns.

enriching SyriaTel’s customer retention strategy with a robust, data-driven approach to minimize churn and maximize lifetime value.

---

*Made with ❤️ using scikit-learn, pandas, and Matplotlib in Jupyter Notebook*


## Author

Ryan Karimi
