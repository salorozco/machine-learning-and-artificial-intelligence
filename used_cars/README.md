# What Drives the Price of a Car?

This project analyzes a dataset of over 426,000 used cars from Kaggle to determine the key factors driving their prices. The goal is to provide actionable insights for a used car dealership to optimize inventory and pricing strategies. Below, we outline the data preparation, modeling results, and findings answering the question: *What drives the price of a used car?*

## Data Cleaning and Preparation

To ensure the dataset was suitable for analysis, the following steps were taken:

- **Dropped Unnecessary Columns**:  
  Removed `id`, `VIN`, `size`, `paint_color`, `state`, and `drive` due to irrelevance or excessive missing values (e.g., `size` had many nulls).

- **Removed Duplicate Rows**:  
  Eliminated duplicates to prevent skewed results.

- **Filtered Data**:  
  Applied ranges to focus on realistic used cars:
    - Year: ≥ 1960 (post-1960s car sales growth).
    - Price: ```$500``` to ```$200,000``` (excluded extremes and new cars).
    - Odometer: 10,000 to 300,000 miles (removed unrealistic values).
    - Condition: Excluded "new" cars to target used vehicles only.

- **Handled Missing Values**:  
  Dropped rows missing `year` or `odometer`. Filled missing categorical features with the most frequent value:
  ```python
  categorical_features = ['manufacturer', 'model', 'condition', 'cylinders', 'fuel', 'title_status', 'transmission', 'type', 'region']
  cat_imputer_freq = SimpleImputer(strategy='most_frequent')
  df[categorical_features] = cat_imputer_freq.fit_transform(df[categorical_features])
  ```
- **Created New Feature**:
  Added car_age = 2025 - year to measure vehicle age.
- **Removed Rare Categories**:
  Dropped manufacturers appearing in less than 0.5% of rows to reduce noise.
- **Removed Outliers**:
    Excluded top 1% of price and odometer values for typical used car focus. 
- **Converted Data Types**:
    Used convert_dtypes() for efficiency and set categorical features to category type. 
- **Split Data**:
    Divided into 70% train, 15% validation, and 15% test sets for modeling.
    These steps cleaned and standardized the dataset, preparing it to identify price drivers effectively.

These steps cleaned and standardized the dataset, preparing it to identify price drivers effectively.


### Section 3: Model Performance Overview

## Model Performance Overview

Five regression models were trained to predict used car prices:

- **Ridge Regression**: Best performer with Test R² of 0.7415 (74% accuracy), Test MAE of ```$4,442```, and Test MSE of 40,473,954.
- **Polynomial Regression**: Matched Ridge at 74% accuracy (Test R² 0.7415, MAE ```$4,442```).
- **Lasso Regression**: Close at Test R² 0.7393, MAE ```$4,452```, faster training (46s vs. ~60-100s).
- **SFS Linear**: Test R² 0.7328, MAE ```$4,511```.
- **Simple Linear**: Lowest at Test R² 0.7149, MAE ```$4,637```.

Ridge excels in accuracy and generalization, while Lasso offers speed and simplicity.

## Key Observations: What Drives Used Car Prices?

### Main Features Driving Prices
Analysis from Ridge coefficients and permutation importance identifies:

- **Year (Car Age)**:
    - `car_age^2` (coefficient 16,560) boosts newer car prices; `car_age^3` (-6,858) shows sharp drops after 10-15 years.
    - Newer cars (e.g., 2010-2020) command premiums; older ones (pre-2000) depreciate heavily.
- **Model**:
    - Coefficient 6,153, permutation 67.3M—luxury brands (Ferrari: ```$99,458``` avg) and trucks (f-150) drive high prices.
- **Mileage (Odometer)**:
    - Coefficient -1,538, permutation 13.4M—low mileage (<50K miles) adds value; high mileage (150K+) reduces it.
- **Condition**:
    - Coefficient 216, permutation 137K—“good” often outprices “excellent,” hinting at perception issues.
- **Type**:
    - Transmission (-2,022)—trucks/SUVs retain value better than sedans.

### Top 20 Models by Count
Frequent models reflect demand:
- f-150: 6,968 cars
- silverado 1500: 4,417
- camry: 2,745
- Trucks lead, sedans are common but lower-priced.

## Hypotheses About What Drives Used Car Prices

- **Newer Cars Are Valued Higher**:  
  Cars under 10-15 years old fetch more due to reliability—older ones lose appeal fast.
- **Model Popularity Boosts Prices**:  
  High-demand trucks (f-150) and luxury brands (Ferrari) command premiums—brand and type matter.
- **Mileage Impacts Resale**:  
  Low mileage (<50K miles) signals quality; high mileage (>150K) suggests wear, cutting value.
- **Condition Perception Varies**:  
  “Good” beating “excellent” suggests buyers trust subjective labels—needs clarity.
- **Trucks/SUVs Outlast Sedans**:  
  Buyers favor durability—trucks/SUVs hold value longer.
