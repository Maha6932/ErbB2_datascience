# Development of Machine Learning Models for Compounds Targeting the ErbB2 Gene
# Project Overview
The project revolves around using machine learning (ML) to analyze and predict the bioactivity of compounds targeting the ErbB2 gene (CHEMBL1824). The ErbB2 gene, also known as HER2, is significant in cancer research, particularly in breast cancer. By leveraging bioactivity data from the ChEMBL database, the goal is to classify compounds into three categories—active, inactive, and intermediate—and build regression models to predict their potency using molecular descriptors.

## 1. Data Collection
Source: ChEMBL database.
Gene of Interest: ErbB2 (CHEMBL1824).
Bioactivity Data: Filtered for compounds with IC50 values in nanomolar (nM) units, which indicate the concentration required to inhibit 50% of a biological target.

## 2. Data Preprocessing
Classification of Bioactivity:
Active: IC50 < 1000 nM.
Inactive: IC50 > 10,000 nM.
Intermediate: IC50 between 1000 nM and 10,000 nM (later removed from the dataset for better classification clarity).
Conversion of IC50 to pIC50:
IC50 values are converted to pIC50 (negative logarithm base 10), which ensures a more uniform distribution:
𝑝𝐼𝐶50=−log 10 (IC50 in molar units)
pIC50=−log 10 (IC50 in molar units)
This step standardizes the data and simplifies interpretation.

## 3. Feature Engineering
Lipinski Descriptors:
Christopher Lipinski's Rule of Five evaluates the drug-likeness of compounds based on:
Molecular weight < 500 Da.
LogP (partition coefficient) < 5.
Hydrogen bond donors < 5.
Hydrogen bond acceptors < 10.
These descriptors are calculated for each compound to assess their suitability as potential drugs.
Molecular Descriptors:
Additional molecular descriptors are computed using PaDEL-Descriptor software, generating a set of 881 input features for each compound.

## 4. Exploratory Data Analysis
Chemical Space Analysis:
The distribution of Lipinski descriptors across active and inactive compounds is visualized via frequency plots, scatter plots (e.g., molecular weight vs. LogP), and box plots.
Key Findings:
Significant statistical differences were observed between active and inactive compounds for most descriptors, such as molecular weight, LogP, and hydrogen bond acceptors.
These differences highlight patterns that the ML models can exploit to predict bioactivity.

## 5. Model Building
Dataset Preparation:

X matrix: Features (molecular descriptors).
Y variable: pIC50 values.
Low-variance features are removed, and the dataset is split into training (80%) and testing (20%) subsets.
Regression Models:

Multiple ML algorithms are evaluated, primarily focusing on regression to predict pIC50 values. 

Performance Metrics:
R-squared (R²): Measures the proportion of variance explained by the model.
RMSE: Root Mean Square Error, quantifying prediction error.
Computation Time: Efficiency of the model.

## 6. Model Performance
Top Performers (High R²):
ExtraTreesRegressor, DecisionTreeRegressor, ExtraTreeRegressor, GaussianProcessRegressor, and RandomForestRegressor excelled in predicting pIC50 values, achieving higher R² values (around 0.89–0.90).
Fastest Models (Low Computation Time):
Lasso, LassoLars, DummyRegressor, DecisionTreeRegressor, and ExtraTreeRegressor completed predictions in nearly zero seconds, making them efficient for quick analysis.

## 7. Statistical Analysis
Significant Findings:
Active and inactive compounds showed statistically significant differences in pIC50 values and most Lipinski descriptors (except for the number of hydrogen bond donors).
This supports the use of these features for predictive modeling.

## 8. Conclusions and Next Steps
Conclusions:
The ML models developed in this project successfully predict the bioactivity of compounds targeting the ErbB2 gene.
High-performing models like ExtraTreesRegressor and RandomForestRegressor are effective for this task.
Lipinski descriptors and molecular features play a critical role in distinguishing active compounds from inactive ones.

Next Steps:
Further optimize the models to improve performance.
Explore additional molecular features for better insights.
Apply the dataset for drug discovery efforts focused on ErbB2 inhibitors.
