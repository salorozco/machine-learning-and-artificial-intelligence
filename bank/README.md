# Will a Client Subscribe to a Term Deposit?

Overview: In this practical application, your goal is to compare the performance of the classifiers we encountered in this section, namely K Nearest Neighbor, Logistic Regression, Decision Trees, and Support Vector Machines. We will utilize a dataset related to marketing bank products over the telephone.

##  Business Objective

The goal of this analysis is to build a predictive model that helps the bank identify clients most likely to subscribe to a term deposit. The marketing team is particularly interested in **maximizing recall**—so fewer potential subscribers are missed—while maintaining at least **0.35 precision** for campaign efficiency.

---

## Data Preprocessing Summary

### Data Cleaning
- Dropped the `duration` column to avoid data leakage.
- Removed duplicate rows.
- Mapped target variable `y` to binary: `'yes' → 1`, `'no' → 0`.

### Feature Engineering
- Split the data into training (70%) and test (30%) sets using stratification.
- Binned `age` into age groups and removed the original `age` column.
- Replaced `'unknown'` values:
    - `job`, `marital`: replaced with mode.
    - `education`, `default`, `housing`, `loan`: replaced with `'other'`.

### New Feature
- Created `contacted_before` based on `pdays` (1 if contacted, 0 otherwise) and dropped `pdays`.

### Feature Transformation
- `james_stein_cols`: Encoded using JamesSteinEncoder.
- `onehot_cols`: Encoded using OneHotEncoder.
- `numeric_cols`: Standardized using StandardScaler.

All transformations were bundled into a `ColumnTransformer` for clean integration into ML pipelines.

---

## Exploratory Data Insights

### Age
- Majority of clients are between 30–40 years old.
- Clients under 25 and over 65 are underrepresented.
- Conversion rate generally decreases with age after 40.

### Job
- Highest conversion rates: **students (31.4%)**, **retired (25.2%)**.
- Lowest: **blue-collar (6.9%)**, despite high volume.
- Students should be a strategic target group, despite small size.

### Marital Status
- **Married** clients have the lowest conversion rate (10.2%).
- **Single** clients convert at 14%, indicating more receptiveness.
- The "unknown" group is too small to draw conclusions.

### Education
- **University** and **high school** graduates are the most populous and moderately converting groups.
- **Illiterate** clients convert at 22.2% but are too few to be actionable.
- Focusing on high-volume, medium-converting education levels is strategic.

### Default
- **No default** group converts at 13.3%.
- **Unknown** group has a low rate (5.2%).
- **Default = Yes** clients never subscribed—very unlikely to convert.

### Housing
- Small difference in conversion rates among `yes`, `no`, and `unknown`—not a strong predictor.

### Loan
- Clients **without personal loans** slightly more likely to convert.
- Overall, loan status has minimal influence.

### Contact Method
- **Cellular** contact method had significantly higher conversion rates than **telephone**.

### Month
- **March, December, September, and October** had the highest conversion rates.
- **May–August** had poor conversion despite high contact volume.
- Suggests marketing may be more effective in late Q3 and Q4.

### Day of Week
- **Thursday** is the best day for conversion (12.1%).
- **Monday** is the worst (9.9%).
- Targeting mid-to-late week may yield better results.

---

## Model Performance Comparison (GridSearchCV-Tuned)

| Model                                     | Train Accuracy | Test Accuracy | Precision | Recall  | F1 Score | ROC AUC Train | ROC AUC Test | Training Time (s) | Best Params |
|-------------------------------------------|----------------|----------------|-----------|---------|----------|----------------|---------------|--------------------|-------------|
| **Baseline Dummy (Stratified)**           | 0.7918         | 0.7970         | 0.1182    | 0.1146  | 0.1163   | 0.4963         | 0.5008        | 0.002              | *N/A*       |
| **Logistic Regression**                   | 0.8072         | 0.8132         | 0.3438    | 0.6613  | 0.4524   | 0.7881         | 0.8001        | 10.85              | `{'C': 50, 'class_weight': 'balanced', 'penalty': 'l2', 'solver': 'lbfgs'}` |
| **KNN**                                   | 0.8461         | 0.8201         | 0.3393    | 0.5729  | 0.4262   | 0.8825         | 0.7629        | 30.21              | `{'algorithm': 'auto', 'n_neighbors': 20, 'p': 2, 'weights': 'uniform'}` |
| **Decision Tree**                         | **0.8936**     | **0.8829**     | **0.4980**| 0.4380  | **0.4660**| 0.7998         | 0.7353        | 53.37              | `{'class_weight': 'balanced', 'criterion': 'entropy', 'max_depth': 10, 'min_samples_leaf': 3, 'min_samples_split': 5}` |
| **SVM**                                   | 0.8289         | 0.8296         | 0.3641    | **0.6171**| 0.4580   | **0.8257**     | **0.7728**    | **662.60**         | `{'C': 1, 'gamma': 'scale', 'kernel': 'rbf'}` |


---

## Final Recommendation

While all models outperformed the baseline dummy classifier, the **Decision Tree** emerged as the **most balanced** and strategic model. It achieved the **highest precision (0.50)** and a respectable **recall (0.44)**, making it effective in targeting clients likely to convert while minimizing wasted marketing effort. It also offers excellent interpretability, which is valuable for stakeholders who need to understand and trust the model's decisions.

Despite Logistic Regression having slightly better recall (0.66), its lower precision (0.34) means more false positives—potentially leading to wasted resources. **Decision Tree’s balance between precision and recall**, along with high test accuracy and fast inference time, make it an ideal candidate for deployment in this bank’s marketing campaign.

---

## Business Suggestions

- Target **students, retirees**, and **university/high school educated clients**, who have higher conversion rates.
- Focus outbound campaigns in **March, December, September**, and **October**, particularly **midweek (Tues–Thurs)**.
- Use **cellular contact methods** over telephone whenever possible.
- Avoid targeting clients who **previously defaulted** or have incomplete data marked as `'other'`.
- Deploy the Decision Tree model to maximize marketing efficiency with interpretable, balanced decisions.