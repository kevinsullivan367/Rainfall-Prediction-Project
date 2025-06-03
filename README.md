# Rainfall Prediction Project - All analysis conducted in R

---

## Executive Summary  
This project aimed to identify an accurate yet parsimonious model to predict rainfall using easily obtainable weather metrics. Accurate weather forecasting is crucial for emergency preparedness, public health resource allocation, and daily life decisions. Over 800,000 models from 8 machine learning methods were fit. The final preferred model, logistic regression with 5-fold cross-validation, used just three predictors and achieved a 10.5% error rate with a strong Kaggle score of 0.896. This demonstrates how machine learning can support timely, effective public health and emergency planning decisions.

---

## Problem Statement, Dataset Overview, and Feature Engineering  
According to NOAA, 90% of US counties experienced a weather disaster in the last decade. Flash flooding, driven by heavy rainfall, is a significant public health risk that can be mitigated through accurate rainfall prediction. This project evaluates machine learning methods to predict a binary rainfall indicator based on weather metrics, blending public health and meteorology.  

- **Dataset:** Kaggle “Binary Prediction with a Rainfall Dataset”  
- **Observations:** 2,190  
- **Features:** 16 total (13 base features + 3 engineered)  
- **Outcome:** Binary rainfall indicator (rain/no rain)  
- **No missing data or outliers detected**  

**Feature engineering included:**  
- Dew Point Depression = Temperature – Dewpoint (air saturation metric)  
- Temperature Range = Max Temp – Min Temp (rainy days tend to have smaller ranges)  
- Humidity × Cloud Coverage (interaction term to capture humid, cloudy conditions on rainy days)  

---

## Methods  
Rainfall prediction is a binary classification problem. Evaluated methods included:  
- Logistic Regression (base R)  
- k-Nearest Neighbors (k=1 to 100)  
- Generative classification models (LDA, QDA, Naive Bayes)  
- Model optimization: 5-fold and 10-fold cross-validation  
- Model subset selection (stepwise)  
- Model shrinkage (Lasso, Ridge regression)  
- Random Forest  
- XGBoost  

Four methods used an iterative approach fitting every feature subset (total 8,191 models for 13 predictors). Other methods used the full feature set. Models were trained on a 70% split and validated on 30%. The best models minimized misclassification error and used fewer predictors for ease of implementation. Kaggle ROC AUC scores further validated model quality.

---

## Results  
- Total models run: 868,251 across 8 ML methods  
- Best models had 3–16 predictors, with misclassification errors from 10.2% to 35.5%  
- Most models ranged between 11%–14% error  
- Logistic regression with 5-fold CV using three predictors (pressure, sunshine, humid_cloud) was the preferred model:  
  - Misclassification error: 10.5%  
  - Kaggle score: 0.896 (close to competition leaders’ 0.906)  
- The 10-fold CV logistic model was slightly more accurate (10.2% error) but used 6 predictors  

---

## Evaluation and Discussion  
The preferred logistic regression model balances accuracy and parsimony, using commonly collected weather features. This makes it practical for meteorologists, emergency managers, and public health officials. Some ML methods (kNN, LDA, QDA, Naive Bayes) performed reasonably, while others (Ridge, XGBoost, Random Forest) were less effective, possibly due to data complexity and randomness inherent in rainfall prediction.  

Prediction errors between 10%–35% reflect the challenge of forecasting weather with limited features. Additional factors beyond the data scope influence rainfall. Nevertheless, even imperfect models have utility—as meteorologists say, it may not rain, but it’s wise to carry an umbrella.

---

## Future Work  
Rainfall prediction remains complex. Future directions include:  
- Applying neural networks or support vector machines  
- Combining insights from public health, meteorology, and data science  
- Integrating additional data sources to improve accuracy and nuance  
