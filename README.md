# Project Report: Automobile Price Prediction - Data Cleaning and Feature Engineering

# 1. Introduction

This project aimed to prepare an automobile dataset for predictive modeling by performing essential data cleaning and feature engineering steps. The primary focus was on handling missing values, addressing outliers, encoding categorical features, and creating new features to potentially improve model performance. The dataset used was sourced from an Excel file named 'cars.xlsx'.

# 2. Objectives

Data Import and Inspection: Load the dataset and understand its structure, data types, and initial content.

Missing Value Handling: Identify and impute missing values present in the dataset.

Outlier Management: Detect and mitigate the impact of outliers in the 'price' variable.

Categorical Feature Encoding: Convert categorical features into numerical representations suitable for machine learning models.

Feature Engineering: Create new features from existing ones to capture potentially valuable information.

Data Transformation: Apply data scaling techniques to numerical features.

# 3. Data and Methods

Data Source: 'cars.xlsx' (loaded using pandas)

Libraries: pandas, numpy, matplotlib, seaborn, scikit-learn

Key Steps:

Data Loading and Inspection:

The pandas library was used to load the dataset from the 'cars.xlsx' file into a DataFrame.

The head() method was used to display the first few rows of the DataFrame, and columns to inspect the column names.

The unique_values() function was created to output each column name with its unique values.

Missing Value Handling:

Missing values were initially represented as '?'. These were replaced with np.nan.

The 'normalized-losses' column had missing values, which were imputed using the median of the non-missing values. The column was explicitly cast to float type before imputation and kept as integer after imputation.

The 'horsepower' column was handled similarly, replacing missing values with the median.

Outlier Management:

Box plots (sns.boxplot) were used to visualize price distributions by 'make' and identify potential outliers.

Specific outlier removal strategies were applied. Cars from 'toyota', 'dodge', 'honda', 'isuzu', 'mitsubishi', and 'plymouth' with prices exceeding certain thresholds (15000, 12000, 12500, 20000, 14000, and 10000 respectively) were removed from the dataset. This removal was based on the intention of removing particularly high-priced cars within those brands, presumably identified as outliers.

Categorical Feature Encoding:

LabelEncoder from sklearn.preprocessing was used to convert categorical features (object dtype) into numerical labels. All object-type columns ('make', 'fuel-type', 'body-style', 'drive-wheels', 'engine-location', 'engine-type') were encoded using this approach.

Feature Engineering:

A new feature named 'area' was created by multiplying the 'height' and 'width' columns.

The original 'width' and 'height' columns were then dropped from the DataFrame.

Data Transformation:

The numerical features were identified and scaled using StandardScaler and MinMaxScaler, although these transformations were performed on a small sample DataFrame d.

DataFrame Combination:

The numerical features, the encoded categorical features, and the area were combined to create the final dataframe.

# 4. Results and Findings

Missing values were successfully imputed using the median for 'normalized-losses' and 'horsepower'. This ensured that these columns could be used in subsequent analysis without introducing bias from missing data.

Outliers in the 'price' column were identified and removed.

Categorical features were successfully encoded into numerical representations, making them compatible with most machine learning algorithms.

The feature 'area' was created. This could potentially capture the overall size of the car and its impact on price.

The dataset was scaled.

# 5. Discussion

Missing Value Imputation: Using the median for imputation is a common and generally robust approach, especially when the data might contain outliers. However, more sophisticated methods like k-NN imputation or model-based imputation could be explored in future iterations.

Outlier Removal: Outlier removal is a sensitive step. The thresholds used for removing outliers were somewhat arbitrary. A more data-driven approach (e.g., using IQR or z-score methods combined with domain knowledge) could be beneficial. It's important to carefully consider the reasons for outliers and whether they represent genuine data points or errors.

Categorical Encoding: Label encoding is suitable when there is an ordinal relationship between categories. If there's no ordinal relationship, one-hot encoding might be a better choice to avoid introducing artificial ordering.

Feature Engineering: The 'area' feature seems like a reasonable addition, but its actual impact on model performance needs to be evaluated. Other potential features could be derived from engine size, horsepower, or combinations of existing features.

Data Transformation: Scaling can improve the performance of some models, but it's not always necessary. The choice of scaling method (StandardScaler vs. MinMaxScaler) depends on the specific model and data distribution.

# 6. Next Steps and Recommendations

Model Building: Train and evaluate various machine learning models (e.g., linear regression, random forest, gradient boosting) to predict automobile prices using the prepared dataset.

Feature Selection: Use feature selection techniques to identify the most relevant features for price prediction and potentially simplify the model.

Hyperparameter Tuning: Optimize the hyperparameters of the chosen model(s) using cross-validation to achieve the best possible performance.

Advanced Feature Engineering: Explore more sophisticated feature engineering techniques, such as creating interaction terms or polynomial features.

Evaluate Model Performance: Evaluate the model using appropriate metrics such as Mean Squared Error (MSE), Root Mean Squared Error (RMSE), R-squared, and Mean Absolute Error (MAE).

Consider Additional Data: Incorporate external data sources (e.g., economic indicators, market trends) to potentially improve prediction accuracy.

Refine Outlier Handling: Investigate the outliers more deeply and consider alternative approaches for handling them, such as winsorization or transformation.

Experiment with different encoding methods: Use OneHotEncoder for the categorical variables and compare the performance.

Perform Analysis of Variance (ANOVA) tests: These tests will help identify the features that have a significant influence on the outcome.

7. Conclusion

This project successfully performed several key data preparation steps, including missing value imputation, outlier management, categorical feature encoding, and feature engineering. The resulting dataset is now better suited for building and evaluating predictive models for automobile prices. The next steps involve model selection, training, evaluation, and further refinement to achieve the desired prediction accuracy.
