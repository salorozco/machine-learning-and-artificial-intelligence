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