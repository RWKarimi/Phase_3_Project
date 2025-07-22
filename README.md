# SyriaTel Customer Churn Prediction

## Overview

This project utilizes machine learning to predict customer churn for SyriaTel, a leading telecommunications provider in the Middle East. By examining customer usage patterns, service-plan selections, and demographic information, we develop predictive models that flag customers at highest risk of leaving. Proactive identification empowers SyriaTel’s marketing and customer-success teams to deploy personalized retention strategies, reducing lost revenue and improving overall profitability.

## Table of Contents

* [Business Context](#business-context)
* [Problem Statement](#problem-statement)
* [Data Description](#data-description)
* [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)
* [Methodology](#methodology)
* [Model Evaluation](#model-evaluation)
* [Results](#results)
* [Requirements](#requirements)
* [Installation](#installation)
* [Usage](#usage)

  * [Running the Notebook Locally](#running-the-notebook-locally)
  * [Running the Notebook on Google Colab](#running-the-notebook-on-google-colab)
* [Author](#author)

## Business Context

In a saturated telecom market, customer churn directly impacts revenue and brand reputation. For SyriaTel:

* **Revenue Impact**: Each lost customer represents not only lost monthly subscription fees but also the sunk costs of acquisition campaigns.
* **Market Dynamics**: Competitors aggressively target high-value customers with promotional offers; failing to anticipate churn leaves SyriaTel vulnerable to erosion of market share.
* **Operational Costs**: Acquiring new customers costs up to five times more than retaining existing ones. Reducing churn maximizes lifetime value and marketing ROI.
* **Strategic Advantage**: Data-driven churn prediction enables targeted loyalty programs, tailored pricing plans, and proactive outreach—transforming reactive retention into a strategic growth lever.

## Problem Statement

Build a robust classification model that accurately predicts which SyriaTel customers are at risk of churning. Early warnings allow tailored interventions (e.g., discount offers, service upgrades, or personalized communications) to reduce attrition.

## Data Description

The dataset encompasses 3,333 SyriaTel customers with the following key features:

* **Numerical Features**:

  * Total minutes and number of calls during Day, Evening, Night, and International periods
  * Number of customer-service calls made
  * Account tenure in days
* **Categorical Features**:

  * International calling plan (Yes/No)
  * Voice mail plan subscription (Yes/No)
  * Geographic State (categorical region codes)
  * Churn label (target variable: Churn = 1 indicates the customer left)

## Exploratory Data Analysis (EDA)

During EDA, several patterns emerged:

1. **Usage Patterns Differ by Churn Status**

   * Churners average **25% fewer daytime minutes** but **40% more customer-service calls**, suggesting dissatisfaction triggers churn.
   * Customers without international plans churn at **twice the rate** of those with plans, indicating the value perception of bundled services.

2. **Temporal Behavior Insights**

   * Night-time call duration is **15% higher** for churners, potentially reflecting off-peak usage without sufficient incentives.
   * Peaks in evening usage correlate with increased complaints logged, hinting at network performance issues during high-load periods.

3. **Feature Correlations**

   * Positive correlation (ρ = 0.65) between customer-service calls and churn, highlighting the support experience as a churn driver.
   * Weak correlation (ρ ≈ 0.10) between voicemail-plan subscription and churn, suggesting minimal retention impact from that feature alone.

4. **Class Imbalance**

   * Only **85 out of 3,333** customers (\~2.5%) churned, necessitating oversampling (SMOTE) to train effective models.

## Methodology

1. **Data Preprocessing**

   * Impute or drop missing records; encode binary and categorical variables via one-hot encoding.
   * Scale numerical features with `StandardScaler` to normalize magnitude differences.
   * Address imbalance using SMOTE to generate synthetic minority-class samples.

2. **Modeling**

   * **Logistic Regression**: Baseline linear model with hyperparameters optimized via `GridSearchCV`.
   * **Decision Tree Classifier**: Tree-based model tuned for max depth and splitting criteria.

3. **Evaluation Metrics**

   * **Classification**: Accuracy, Precision, Recall, F1-Score to balance Type I/II errors.
   * **Ranking**: ROC Curve and AUC to assess discrimination across thresholds.

## Model Evaluation

| Model               | AUC   | F1-Score | Precision | Recall |
| ------------------- | ----- | -------- | --------- | ------ |
| Logistic Regression | 0.872 | 0.65     | 0.60      | 0.70   |
| Decision Tree       | 0.927 | 0.72     | 0.68      | 0.77   |

The Decision Tree model achieved a **6.3% higher AUC** than Logistic Regression, particularly excelling in low-FPR regions—critical for minimizing false alarms in retention campaigns.

## Results

The optimized Decision Tree classifier can be embedded into SyriaTel’s CRM to score incoming customers in real time. Key next steps include exploring ensemble methods (e.g., Random Forest, XGBoost) and integrating external data sources (e.g., network quality logs, demographic profiles).

## Requirements

* Python 3.7+
* pandas
* numpy
* scikit-learn
* imbalanced-learn
* matplotlib
* seaborn

## Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/yourusername/SyriaTel_Churn_Prediction.git
   cd SyriaTel_Churn_Prediction
   ```
2. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

## Usage

### Running the Notebook Locally

1. Launch Jupyter Lab or Notebook:

   ```bash
   jupyter notebook
   ```
2. Open `SyriaTel_Churn_Prediction.ipynb` and run all cells.

### Running the Notebook on Google Colab

1. Upload your repository to GitHub (or use the existing remote).
2. In Colab, select **File → Open notebook → GitHub** and paste the repo URL.
3. Once loaded, install dependencies at the top cell:

   ```python
   !pip install pandas numpy scikit-learn imbalanced-learn matplotlib seaborn
   ```
4. Run all cells sequentially to reproduce the analysis.
5. To save outputs, mount your Google Drive:

   ```python
   from google.colab import drive
   drive.mount('/content/drive')
   ```

   and specify a path in Drive for model artifacts.

## Author

Ryan Karimi
