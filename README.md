# SyriaTel Customer Churn Prediction

<h1 align="center">🎯 <span style="color:#2E86C1">SyriaTel Churn Prediction</span></h1>

<p align="center">
  <a href="https://colab.research.google.com/github/your-repo/SyriaTel_Churn_Prediction.ipynb"><img src="https://img.shields.io/badge/Open%20in-Colab-ff69b4.svg" alt="Open in Colab"/></a>
  <img src="https://img.shields.io/badge/Python-3.8+-blue.svg" alt="Python Version"/>
  <img src="https://img.shields.io/badge/Framework-scikit--learn-green.svg" alt="Scikit-Learn"/>
</p>

# Overview

This project focuses on predicting customer churn for **SyriaTel**, a leading telecommunications operator in Syria. By leveraging machine learning techniques on historical usage and billing data, we aim to identify customers who are at high risk of leaving, enabling targeted retention strategies and improving overall business performance.

# Business and Data Understanding

## Business Context

SyriaTel faces intense competition in the telecom sector and aims to reduce customer attrition, which directly impacts revenue and market share. Identifying likely churners before they leave allows the company to deploy proactive retention offers and personalized engagement.

## Stakeholder Audience

* **Senior Management:** To understand projected churn rates and ROI on retention campaigns.
* **Marketing & Customer Care Teams:** To design targeted promotions for at-risk customers.
* **Data Science Team:** To validate model performance and integrate into a production pipeline.

## Dataset Choice

The dataset includes customer demographics, service usage metrics (daytime, evening, nighttime and international call minutes and charges), customer service interactions, and contract details. It provides both behavioral and transactional features necessary for robust churn prediction.

# Modeling

We experimented with two supervised classification models:

1. **Logistic Regression**

   * Feature selection based on correlation and domain knowledge.
   * Standardization of numerical variables.
   * Use of SMOTE to address class imbalance.

2. **Decision Tree Classifier**

   * Default Gini impurity criterion.
   * Pruning parameters tuned via cross-validation to prevent overfitting.

Each model was trained on a stratified train-test split and evaluated on the holdout set.

# Evaluation

Key performance metrics for the models (Churn = 1 class):

| Metric    | Logistic Regression | Decision Tree |
| --------- | ------------------- | ------------- |
| Accuracy  | 0.81                | 0.92          |
| Precision | 0.39                | 0.76          |
| Recall    | 0.57                | 0.62          |
| F1-Score  | 0.47                | 0.68          |
| AUC-ROC   | 0.76                | 0.85          |

**Best Model:** Decision Trees demonstrated the highest balance of precision and recall, making it the preferred choice for deployment.

# Conclusion

* **Recommended Approach:** Deploy the decision tree model for real-time churn scoring.
* **Business Impact:** Targeted retention campaigns could reduce churn by an estimated 10–15%, translating to significant revenue savings.
* **Next Steps:**

  1. Integrate the model into SyriaTel’s CRM system for live scoring.
  2. Monitor model drift and recalibrate quarterly.
  3. Explore ensemble methods or more complex algorithms (e.g., Random Forest, Gradient Boosting).

# Presentation Slides

> *Presentation link [Syriatel presentation.pdf*](https://github.com/RWKarimi/Phase_3_Project/blob/ft-Jupyter-Notebook/Syriatel%20presentation.pdf)

# Running the Notebook

## Local Environment

1. Clone the repository:

   ```bash
   git clone https://github.com/your-username/SyriaTel-Churn-Prediction.git
   cd SyriaTel-Churn-Prediction
   ```
2. Create a virtual environment and install dependencies:

   ```bash
   python3 -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   pip install -r requirements.txt
   ```
3. Launch Jupyter Notebook:

   ```bash
   jupyter notebook
   ```

## Google Colab

1. Upload `SyriaTel_Churn_Prediction.ipynb` to Google Drive.
2. Open the notebook in Colab.
3. Install required packages by running at the top cell:

   ```python
   !pip install -r https://raw.githubusercontent.com/your-username/SyriaTel-Churn-Prediction/main/requirements.txt
   ```
4. Ensure data files are accessible (upload to Colab or mount Drive).
5. Run all cells to reproduce the analysis.

---

*For detailed methodology, refer to the Jupyter Notebook. For any questions or feedback, please contact the data science team.*

*Made with ❤️ using scikit-learn, pandas, and Matplotlib in Jupyter Notebook*


## Author

Ryan Karimi
