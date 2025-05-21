# What factors impact the likelihood of developing coronary heart disease (CHD) in the next 10 years?
---
[View Full Jupyter Notebook](https://github.com/salorozco/machine-learning-and-artificial-intelligence/blob/main/heart/heart_capstone.ipynb)
## What’s This Project About?

Heart disease is the leading cause of death worldwide, but many cases can be prevented with early action.  
This project uses real medical data from over 4,200 people to help predict who might develop heart disease in the next 10 years.

We built a computer program that learns from past patient data and identifies patterns to flag people who may be at higher risk.  
This tool can help doctors take early steps to protect their patients' health.

---

## What Kind of Data Was Used?

The data came from the **Framingham Heart Study**, a well-respected long-term health study.  
We used information such as:

- Age
- Gender
- Cholesterol levels
- Blood pressure (systolic and diastolic)
- Smoking habits
- Diabetes status
- Body weight (BMI)
- Glucose (blood sugar)
- Heart rate
- Use of blood pressure medication

Each record also included whether the person developed coronary heart disease (CHD) within 10 years,  
which helped the model learn what risk factors matter most.

---

## How Was the Data Cleaned?

Before training the model, we cleaned and prepared the dataset:

- Removed records with missing or unrealistic values  
  (e.g., extremely high blood pressure or glucose levels)
- Created helpful new features:
    - **Pulse Pressure** (systolic BP minus diastolic BP)
    - **Smoking Intensity** (age × cigarettes per day × smoker status)
    - **Cholesterol-to-Age Ratio**

We also grouped cholesterol and blood pressure levels into meaningful medical categories:

- **Cholesterol**: Optimal, Borderline High, High
- **Blood Pressure**: Normal, Elevated, Hypertension Stage 1/2, Hypertensive Crisis

---

## What Did We Learn from the Data?

Key patterns emerged from our analysis:

- Higher **blood pressure** and **cholesterol** are strongly associated with heart disease
- **Smokers** face a much higher risk
- People with **diabetes** or **obesity** are also more likely to develop CHD
- The majority of at-risk patients were between **40 and 60 years old**

Grouping patients by these medical indicators helped us identify risk patterns and design better prevention strategies.

---

## How Did the Model Work?

We tested several computer models to see which one could best identify high-risk individuals.  
Each model was judged on its ability to:

- Catch true cases of CHD (**recall**)
- Avoid false alarms (**precision**)
- Perform well on new, unseen data (**generalization**)

We also used a technique called **Grid Search** to fine-tune the models for better performance.

---

## Best Performing Model: XGBoost

Out of all models tested, **XGBoost** performed the best. It achieved:

- **80.4% accuracy** on new patient data
- Balanced performance across **precision** and **recall**
- **Fast training time** (about 20 seconds)

XGBoost was better than other models like logistic regression, decision trees, or even neural networks  
when it came to accurately identifying people at risk for heart disease.

---

## Practical Applications

### For Healthcare Providers:
- Use the model to **flag high-risk patients** early
- Guide patient discussions around lifestyle changes, testing, or medication

### For Clinics and Hospitals:
- **Prioritize care** based on risk
- Allocate resources more effectively for **preventive health programs**

### For Patients:
- Get a clearer picture of their long-term **heart health risks**
- Take action earlier to prevent future complications

---

## Final Recommendation

Based on its performance, **XGBoost** is the best model for predicting 10-year heart disease risk.  
It’s accurate, fast, and reliable—making it well-suited for use in real-world healthcare settings.

By integrating this kind of model into clinical systems, we can help prevent heart disease before it happens  
and improve outcomes for thousands of patients.

---
