# **Ensembling Methodologies to Predict Medical Expenses Among Smokers and Non-Smokers**

### **Authors**: Joel Laskow, Oluwadamilola Owolabi, and Simi Augustine  
### **Date**: February 2, 2024  

---

## **Overview**

This project employs advanced machine learning techniques to predict medical expenses based on insurance data. Using methodologies such as multiple linear regression (MLR), random forest, K-nearest neighbors (KNN), and ensemble modeling, the analysis seeks to identify key predictors of medical costs. The final ensembled model integrates multiple algorithms, validated through **Leave One Out Cross Validation (LOOCV)** and **K-Fold Cross Validation** to ensure robust predictions.

---

## **Dataset**

The dataset contains 1,338 records with the following features:
1. **Age**: Continuous, patient age in years.
2. **BMI**: Continuous, body mass index (kg/m²).
3. **Children**: Continuous, number of children covered by insurance.
4. **Charges**: Continuous, yearly medical expenses (target variable).
5. **Gender (Sex)**: Categorical, `male` or `female`.
6. **Smoker Status**: Categorical, `yes` or `no`.
7. **Region**: Categorical, geographic region (`northeast`, `northwest`, `southeast`, `southwest`).

**Data Source**:
- [Packt Publications](https://www.packtpub.com/)
- [Kaggle: U.S. Health Insurance Dataset](https://www.kaggle.com/datasets/teertha/ushealthinsurancedataset)

---

## **Key Features**

### **1. Data Preprocessing**
- Missing values were assessed using `naniar::vis_miss()`; no missing values were found.
- Dummy variables were created for categorical data to facilitate regression and machine learning models.
- Feature scaling was performed for KNN models.

### **2. Exploratory Data Analysis (EDA)**
- Visualized relationships between variables using histograms, scatter plots, and boxplots.
- Explored the effects of `smoker` and `region` on medical expenses using facet plots.
- Conducted statistical tests to confirm relationships between predictors and charges.

### **3. Modeling Methodologies**
#### **a. Multiple Linear Regression (MLR)**
- Constructed both basic and complex MLR models using forward selection.
- Validated using 10-fold cross-validation to evaluate performance.

#### **b. Random Forest**
- Built a random forest model to assess feature importance and predict medical expenses.
- Plotted variable contributions using a bar chart.

#### **c. K-Nearest Neighbors (KNN)**
- Developed both full and reduced KNN models:
  - **Full Model**: Used all features.
  - **Reduced Model**: Focused on top predictors (`bmi`, `age`, `smoker status`) identified by random forest.

#### **d. Ensemble Modeling**
- Combined predictions from Random Forest, KNN, and MLR models.
- Validated ensemble performance using LOOCV and K-Fold Cross Validation.

---

## **Results**

1. **Random Forest**:
   - Best model with an RMSE of **4,594.33**.
   - Most influential predictors: `age`, `bmi`, and `smoker status`.

2. **KNN**:
   - **Full Model**: RMSE = **15,294.78** at k=5.
   - **Reduced Model**: RMSE = **15,241.1** at k=4.
   - Reduced model offers similar performance with fewer predictors, enhancing interpretability.

3. **Ensemble Model**:
   - LOOCV RMSE = **7,736.63**.
   - K-Fold Cross Validation RMSE = **6,071.79**.
   - While ensemble RMSE is higher than Random Forest alone, it offers balanced predictions across models.

---

## **Conclusion**

The project demonstrates that:
- **Random Forest** outperforms other individual models in terms of predictive accuracy.
- Ensemble models can achieve robust predictions by combining strengths of multiple algorithms.
- Additional data and stratified sampling could further enhance model reliability and generalizability.

---

## **Future Work**
1. Incorporate additional variables (e.g., smoking frequency, family medical history).
2. Perform stratified sampling to better represent minority groups (e.g., smokers).
3. Explore deep learning models to capture nonlinear relationships in the data.
4. Enhance ensemble methodologies with weighted averages or stacking.

---

## **Tools & Libraries**
- **Programming Language**: R
- **Key Libraries**:
  - `ggplot2`, `dplyr`, `caret`, `randomForest`, `glmnet`, `naniar`
  - `FNN` (for KNN), `fastDummies` (for dummy variable creation)

---

## **Code Execution**
To reproduce the results, follow these steps:
1. Install the required libraries:
   ```R
   install.packages(c("ggplot2", "dplyr", "caret", "randomForest", "glmnet", "naniar", "FNN", "fastDummies"))
