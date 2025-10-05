# Sales Forecasting and Demand Planning

This project focuses on developing a robust model to forecast product demand for a retail business. Accurate demand forecasting is crucial for optimizing inventory levels, minimizing stockouts, preventing overstock situations, and improving overall profitability.

***

## 📝 Problem Statement

In the retail sector, inefficient inventory management leads to significant financial losses. Overstocking results in increased holding costs and potential markdowns, while under-stocking leads to missed sales opportunities and dissatisfied customers. This project aims to build a time-series forecasting model that predicts future product demand, enabling the business to make data-driven decisions for inventory replenishment.

***

## 💾 Data Description

The dataset (`retail_store_inventory.csv`) contains 73,100 records of historical sales and inventory data from January 1, 2022, to January 1, 2024. It includes a variety of features that could influence demand.

**Key Columns:**
* **Date**: The date of the record.
* **Demand Forecast**: The target variable we aim to predict.
* **Store ID, Product ID, Category, Region**: Categorical features identifying the store, product, and its location.
* **Price, Discount, Competitor Pricing**: Pricing and promotional data.
* **Weather Condition, Seasonality, Holiday/Promotion**: External factors that could impact sales.

***

## ⚙️ Approach & Methodology

The project follows a structured approach, beginning with data exploration and preprocessing, followed by model development and evaluation. Three different models were implemented and compared to identify the best-performing solution.

1.  **Exploratory Data Analysis (EDA)**: Initial analysis was performed to understand data distributions, identify correlations between variables, and spot any anomalies or patterns.
2.  **Data Preprocessing**: The data was cleaned and prepared for modeling. This included converting data types for memory optimization and using one-hot encoding to transform categorical features into a numerical format suitable for machine learning models.
3.  **Model Selection**: Three distinct forecasting models were chosen to cover a range of techniques:
    * **Prophet**: A time-series model developed by Facebook, designed to handle seasonality and holiday effects.
    * **XGBoost**: A powerful gradient-boosting algorithm known for its high performance.
    * **AutoARIMA**: A statistical model that automatically finds the best parameters for an ARIMA model.
4.  **Model Training & Evaluation**: The data was split into training (80%) and testing (20%) sets. Each model was trained on the training data and evaluated on the unseen test data using standard regression metrics:
    * **R² Score**: Measures how well the model explains the variance in the data.
    * **Mean Absolute Error (MAE)**: The average absolute difference between predicted and actual values.
    * **Root Mean Squared Error (RMSE)**: Similar to MAE but gives more weight to larger errors.
    * **Mean Absolute Percentage Error (MAPE)**: The average percentage difference between predicted and actual values.

***

## 📊 Results & Insights

The models' performances were evaluated, and the XGBoost Model performed the best.


* **Prophet's Failure**: The Prophet model performed extremely poorly, with a negative R² score indicating it was worse than a naive baseline model. EDA revealed that the dataset was likely synthetic, with uniform distributions and perfect correlations, which Prophet is not well-suited to handle.
* **XGBoost's Superiority**: The **XGBoost** model emerged as the clear winner, achieving higher R² score and lower MAE,MAPE and RMSE values. This demonstrates its ability to capture the complex relationships within the data.

***

## ✅ Conclusion

The analysis demonstrates that for this particular dataset, a machine learning approach with **XGBoost** is significantly more effective than the Prophet time-series model. The artificially perfect nature of the data, discovered during EDA, was a key factor in the models' performance differences. The XGBoost model provides a highly accurate and reliable solution for forecasting demand based on the provided features.

***

## 🚀 Future Improvements

While the XGBoost model is highly accurate, further enhancements could be explored:

* **Hyperparameter Tuning**: Conduct a more extensive search for optimal XGBoost hyperparameters using techniques like Grid Search or Bayesian Optimization.
* **Feature Engineering**: Create new features that might capture more complex interactions, such as the difference between the product price and competitor price.
* **Real-World Data Testing**: The ultimate test would be to apply this modeling pipeline to a real-world, non-synthetic dataset to validate its effectiveness in a business context.
