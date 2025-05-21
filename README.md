# Machine Learning and Artificial Intelligence

This repository contains projects and exercises developed as part of my Machine Learning and Artificial Intelligence certificate program from Berkeley Engineering. Each subfolder represents a distinct project, showcasing practical applications of ML and AI concepts.

## Projects
1. [Will a Customer Accept the Coupon?](https://github.com/salorozco/machine-learning-and-artificial-intelligence/tree/main/customer_coupons)
- Analyzes customer behavior to predict whether they will accept a coupon based on various demographic and behavioral features. The project includes:
- Data Cleaning and Preparation: Addressed missing values, corrected column names, and standardized data for analysis.
- Acceptance Rate Analysis: Over half of the observations (56.84%) chose to accept the coupon, indicating strong interest.
- Category Breakdown: Coffee House and inexpensive restaurant coupons were the most accepted, while Bar and expensive restaurant coupons showed lower acceptance.

2. [What Drives the Price of a Used Car?](https://github.com/salorozco/machine-learning-and-artificial-intelligence/tree/main/used_cars)
- Investigates factors influencing used car prices using a dataset of over 426,000 vehicles, guided by the CRISP-DM framework, to optimize dealership inventory and pricing.
- **Data Cleaning and Preparation**: Removed irrelevant columns (e.g., `id`, `VIN`), filtered data (1960+, ```$500```-```$200,000```, 10K-300K miles), and created `car_age` from `year` (Data Understanding/Preparation phases).
- **Model Performance**: Ridge Regression achieved 74% accuracy (Test R² 0.7415, MAE ```$4,442```), outperforming Simple Linear, Polynomial, Lasso, and SFS Linear models (Modeling/Evaluation phases).
- **Price Drivers**: Year (car age), model, and mileage are key—newer cars, popular trucks (f-150), and low mileage (<50K miles) drive higher prices (Business Understanding/Evaluation phases).
- This project leverages the CRISP-DM process—spanning Business Understanding to Evaluation—to deliver regression modeling and feature analysis for data-driven pricing and inventory insights.

3. [Will a Client Subscribe to a Term Deposit?](https://github.com/salorozco/machine-learning-and-artificial-intelligence/tree/main/bank)
- Analyzes client demographics, contact methods, and economic context to predict term deposit subscription, supporting marketing strategy optimization for a Portuguese bank.
- **Data Cleaning and Preparation**: Removed the `duration` column to prevent data leakage, handled `unknown` values in categorical features (e.g., `job`, `education`, `marital`, `loan`) by replacing them with either the mode or `'other'`, and added the `contacted_before` feature from `pdays`. Binned `age` into groups and dropped the raw `age` column. Duplicates were removed to ensure data quality.
- **Feature Engineering and Exploration**: Discovered highest conversion rates among students (31%) and retirees (25%), and seasonal trends showing better performance in March, December, and October. Created visualizations for each categorical feature to guide feature prioritization and targeting.
- **Modeling**: Built a baseline Dummy Classifier and compared multiple classification models (Logistic Regression, K-Nearest Neighbors, Decision Tree, and Support Vector Machine) using pipelines with SMOTE to address class imbalance. Preprocessing included `JamesSteinEncoder`, `OneHotEncoder`, and `StandardScaler`, combined via `ColumnTransformer`.
- **Model Performance and Improvement**: After hyperparameter tuning with GridSearchCV and improved handling of categorical values, the Decision Tree model achieved the best balance (Precision 0.50, Recall 0.44, F1 Score 0.47, ROC AUC 0.74). Logistic Regression offered the highest recall (0.66), while SVM had the best F1 score (0.46) but took longer to train. All models significantly outperformed the baseline dummy classifier.
- This project highlights the value of model comparison, recall-driven evaluation, and thoughtful data preparation when designing intelligent systems for marketing conversion.

4. [What factors impact the likelihood of developing coronary heart disease (CHD) in the next 10 years?](https://github.com/salorozco/machine-learning-and-artificial-intelligence/tree/main/heart)

- **Data Cleaning and Preparation**:
    - Dropped medically incomplete rows and removed irrelevant features like `education` and sparse columns.
    - Binned `age` into five age groups and categorized `totChol` using clinical thresholds.
    - Engineered domain-relevant features such as:
        - `pulse_pressure = sysBP - diaBP`
        - `chol_age_ratio = totChol / age`
        - `smoking_intensity = cigsPerDay × age`
        - `bp_category` defined per clinical blood pressure stages.

- **Exploratory Data Analysis**:
    - Found CHD risk was highest among individuals with **Stage 2 Hypertension**, **diabetes**, and **high cholesterol**.
    - Visualized CHD rates by `bp_category`, `cholesterol group`, and `age group`.
    - Conducted class distribution analysis to identify the imbalance (~15% positive cases).

- **Feature Engineering and Preprocessing**:
    - Applied One-Hot Encoding and James-Stein Encoding for categorical variables.
    - Standardized numeric features with `StandardScaler`.
    - Handled imbalance with **SMOTE** to oversample minority class in training.

- **Modeling and Evaluation**:
    - Compared multiple classifiers:
        - **Logistic Regression**
        - **K-Nearest Neighbors (KNN)**
        - **Decision Tree**
        - **Support Vector Machine (SVM)**
    - Evaluated models on **precision**, **recall**, **F1 score**, and **ROC AUC**.
    - Used **custom thresholds** for optimizing recall-critical medical scenarios.

- **Model Tuning and Ensemble Techniques**:
    - Performed **GridSearchCV** for all models to find optimal hyperparameters.
    - Implemented ensemble methods:
        - **Voting Classifier** (hard and soft voting)
        - **Bagging**
        - **AdaBoost**
        - **Gradient Boosting**
        - **XGBoost**
        - **LightGBM**
        - **CatBoost**
    - Tracked training time, test time, and generalization metrics for each.

- **Results Summary**:
    - **Gradient Boosting** and **LightGBM** showed the best balance across metrics with F1 ≈ 0.48–0.50 and ROC AUC ≈ 0.75+.
    - **Logistic Regression** achieved the highest **recall** (≈ 0.66), which is critical in clinical applications.
    - **SVM** gave strong ROC AUC, but slower to train and less interpretable.
    - All models outperformed the baseline dummy classifier.
