# Supply_Chain_Optimization_with_Demand_Forecasting

## 🎯 Objective
The main objectives of this project are:
1.  **Predict `Weekly_Sales`**: Develop a robust regression model to predict weekly sales for each store department.
2.  **Feature Analysis**: Identify and analyze the key drivers and features that most significantly influence sales.
3.  **Provide Actionable Insights**: Generate visualizations and reports to understand sales trends and help stakeholders optimize inventory and marketing strategies.

---

## 📦 Dataset
The analysis is based on four distinct datasets:

* `stores.csv`: Contains information about the 45 stores, including their type and size.
* `features.csv`: Contains external data points for each store, such as temperature, fuel prices, promotional markdowns, CPI, unemployment rates, and holiday information.
* `train.csv`: Contains historical training data, including weekly sales for each store and department.
* `test.csv`: Contains the dataset for model evaluation, with the same features as the training set but without the `Weekly_Sales` target variable.

---

## 🛠️ Step-by-Step Process

### 1. Data Loading and Integration
* The four datasets (`features.csv`, `stores.csv`, `train.csv`, `test.csv`) were loaded into Pandas DataFrames.
* The `train` and `stores` DataFrames were initially merged on the `Store` column.
* This combined DataFrame was then merged with the `features` DataFrame on both `Store` and `Date` to create a unified and comprehensive dataset.

### 2. Data Cleaning and Preprocessing
* **Handling Missing Values**: A significant number of missing values were found in the `MarkDown` columns (over 60% missing). To handle this, we implemented the following strategy:
    * **Numerical Columns**: Missing values in columns like `MarkDown1` through `MarkDown5` were filled with the **median** value of their respective columns.
    * **Categorical Columns**: Missing values in any categorical columns were filled with the **mode** (most frequent value).
* **Data Type Conversion**: The `Date` column was converted from an object to a `datetime` type to enable time-series analysis and feature extraction.

### 3. Feature Engineering
To enhance the model's predictive power, several new features were extracted from the `Date` column:
* `Year`
* `Month`
* `Day`
* `Week` (of the year)
* `DayOfWeek`

These temporal features help the model capture seasonality and trends.

### 4. Encoding Categorical Variables
* The `Type` column, which is a categorical feature representing the store type ('A', 'B', 'C'), was converted into a numerical format using **one-hot encoding**. This creates new binary columns (`Type_B`, `Type_C`) that the model can interpret.

### 5. Model Training
* **Data Splitting**: The processed dataset was split into training and testing sets, with **80%** of the data used for training and **20%** for testing.
* **Model Selection**: A **RandomForestRegressor** was chosen as the primary model due to its high performance with tabular data and its ability to handle complex non-linear relationships.
* **Baseline Model**: A `LinearRegression` model was also trained as a baseline. It achieved an R² of only **0.09**, indicating it was not suitable for this problem.
* **Training**: The RandomForestRegressor was trained on the `x_train` and `y_train` datasets.

### 6. Model Evaluation
The trained model's performance was evaluated on the test set using standard regression metrics:
* **Mean Squared Error (MSE)**: `12,030,018`
* **R-squared (R²)**: `0.977`

An **R² value of approximately 97.7%** indicates that the model can explain a very high proportion of the variance in weekly sales, confirming its excellent predictive accuracy.

---

## 📊 Results & Key Insights
* The **RandomForestRegressor** model demonstrated outstanding performance, achieving an **R² score of 97.7%**. This high level of accuracy makes it a reliable tool for forecasting weekly sales.
* **Feature Importance Analysis** (performed during the project) revealed that key drivers of sales include store size, department, and various temporal features like the week of the year, which captures seasonal shopping peaks.
* **Visualizations** like sales trends over time and sales distribution by store type helped in identifying patterns, such as holiday sales spikes and performance differences between store types.

---

## 💻 Tools and Technologies
* **Language**: **Python**
* **Libraries**:
    * **Pandas** for data manipulation and analysis.
    * **Scikit-Learn** for machine learning (model training and evaluation).
    * **Plotly** and **Seaborn** for advanced data visualization.
    * **Matplotlib** for basic plotting.


Scikit-learn – Model building and evaluation

Jupyter Notebook – Development environment
