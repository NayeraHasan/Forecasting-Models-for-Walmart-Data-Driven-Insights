# **Walmart Sales Forecasting: Data-Driven Insights**

This project focuses on building predictive models to forecast weekly sales for Walmart stores. By leveraging machine learning , we explore temporal patterns, feature engineering, and optimization to develop robust models that provide actionable insights for sales forecasting.

## **Problem Statement**
The task is to predict weekly sales for Walmart stores using historical sales data and features such as:
- **Temporal Features**: Date, year, week, month.
- **Store Attributes**: Store number, type, and size.
- **Promotions and Events**: Markdowns (1–5).
- **Seasonality and Holidays**: Holiday flags to capture sales anomalies during special events.

### **Target Variable**
- Weekly sales for each store.

---

## **Project Highlights**
### **1. Linear Regression**
- **Why?** Serves as a baseline to compare with more complex models.
- **Approach**:
  - Introduced lag features (e.g., prior week's sales).
  - Engineered rolling averages to capture recent trends (4-week and 8-week windows).
  - Incorporated cyclic features using sine/cosine transformations to account for seasonality.
- **Challenges**:
  - Struggled with capturing complex, non-linear relationships.
- **Performance**:
  - **RMSE**: 5276.93
  - **R²**: 0.9466

### **2. Random Forest Regressor**
- **Why?** Provides versatility, robustness to outliers, and the ability to model non-linear relationships.
- **Approach**:
  - Extracted meaningful temporal features (month, week, day).
  - Implemented lag features (1-week, 2-week, 52-week lags) to capture historical dependencies.
  - Imputed missing values (e.g., markdowns) and scaled features for consistency.
- **Strengths**:
  - Captured seasonality and overall trends effectively.
  - High interpretability through feature importance scores.
- **Performance**:
  - **RMSE**: 2703.76
  - **MAE**: 1330.88

### **3. LSTM Neural Network**
- **Why?** Designed for sequential, time-dependent data to learn long-term and short-term trends.
- **Approach**:
  - Scaled all features and target values.
  - Developed a multi-layer LSTM architecture:
    - **Input**: 75 2D arrays of time-series data with 50 timestamps.
    - **LSTM Layer**: Learned sequential dependencies with dropout for regularization.
    - **Output Layer**: Predicted the scaled target for the 51st timestamp.
  - Tuned hyperparameters such as learning rate, dropout rate, and architecture depth.
- **Challenges**:
  - High computational cost.
  - Sensitivity to scaling and architecture tuning.
- **Performance**:
  - **RMSE**: 244035
  - **R²**: 0.81

---

## **Data Preparation and Feature Engineering**
### **Steps Taken**:
1. **Data Cleaning**:
   - Merged datasets on `Store` and `Date`.
   - Filled missing markdown values with zeros and imputed CPI and unemployment metrics.
2. **Feature Engineering**:
   - Temporal features (rolling averages, lag features, cyclic features).
   - Categorical features (one-hot encoding for `Store Type` and `IsHoliday`).
   - Numerical scaling for consistent model input.
3. **Train-Test Splits**:
   - **Training**: February 2010 to April 2012.
   - **Validation**: April 2012 to October 2012.

---

## **Model Comparisons**
| Model                  | RMSE     | R²      | MAE     |
|------------------------|----------|---------|---------|
| **Linear Regression**  | 5276.93  | 0.9466  | 1836    |
| **Random Forest**      | 2703.76  | 0.98+   | 1330.88 |
| **LSTM Neural Network**| 244035   | 0.81    | 163882  |

- **Random Forest** achieved the best balance of performance and interpretability.
- **LSTM models** struggled with scaling and optimization but show promise for future improvements.

---

## **Conclusions**
- **Key Takeaways**:
  - Feature engineering significantly improves model accuracy.
  - Lag and rolling average features are essential for capturing temporal patterns.
  - Random Forest excels in balancing accuracy and interpretability for this dataset.
  - LSTM models require further tuning but provide unique capabilities for sequential modeling.

- **Challenges**:
  - Sharp sales spikes remain difficult to predict, necessitating additional temporal context.
  - Random Forest and LSTM models, while accurate, lack interpretability compared to simpler models.

---

## **Resources**
- **Dataset**: [Walmart Sales Forecast](https://www.kaggle.com/datasets/aslanahmedov/walmart-sales-forecast)
- **References**:
  - [Keras LSTM Documentation](https://keras.io/api/layers/recurrent_layers/lstm/)
  - [Time-Series Forecasting](https://machinelearningmastery.com/multivariate-time-series-forecasting-lstms-keras/)
- **Notebooks**:
  - [Linear Regression](https://colab.research.google.com/drive/1pBby3dPgeNrx7FNnA6ZpM9jduqkwXLkt)
  - [Random Forest](https://colab.research.google.com/drive/1qGeyMYRrfVXQG4s6vjWGeU24XFXMsIQf)
  - [LSTM Neural Network](https://colab.research.google.com/drive/1QbqwAzxZJphEnIVH6DO5EpUPONdf6Lqx)

---

This Markdown-formatted README file can be directly copied and pasted into the `README.md` file in your GitHub repository. Let me know if you need help updating your repo! 😊
