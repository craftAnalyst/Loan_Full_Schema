### Loan_Full_Schema  
  
**1. Overview**  
The provided Jupyter notebook analyzes loan data from Lending Club, focusing on preprocessing and predicting loan status. Key steps include data cleaning, handling missing values, feature engineering, and training four classification models: Logistic Regression, SVM, Random Forest, and an Artificial Neural Network (ANN).  

Data Preprocessing  
Key Steps:  
Missing Values Handling:  
Dropped columns with >40% missing values (e.g., annual_income_joint, verification_income_joint).  
  
Imputed numerical columns with the mean and categorical columns with the most frequent value.  

Feature Removal:  

Dropped irrelevant columns: emp_title, issue_month, and sub_grade.  

Encoding:  

Label-encoded categorical variables (e.g., loan_status, homeownership).  

Data Insights:  
Class Distribution: Severe imbalance in loan_status:  

Majority class: "Current" loans (class 1, 92.9% of test data).  
  
Minority classes (e.g., "Charged Off," "Late") had minimal representation.  
  
Final Dataset: 55 original columns reduced to 52 after preprocessing.  

Model Training & Evaluation  
Models Tested:  
Logistic Regression: Accuracy = 97.85%  
SVM: Accuracy = 97.20%  

Random Forest: Accuracy = 98.15%  

ANN: Accuracy = 92.90%  

Performance Summary:    
Model Accuracy Precision (Class 1) Recall (Class 1)  
Logistic Regression 97.85% 0.98 1.00  
SVM 97.20% 0.97 1.00  
Random Forest 98.15% 0.98 1.00  
ANN 92.90% - -  
Key Observations:  
Class Imbalance Issue:  

All models excelled at predicting the majority class (Current loans) but failed on minority classes (e.g., precision = 0% for classes 3–5).  
  
Example: For class 5 (likely high-risk loans), Random Forest achieved 100% precision but only 9% recall.   

Anomaly in ANN Training:  
  
Negative loss values during training suggest a critical error (e.g., incorrect loss function or data leakage).  

Critical Issues & Recommendations  
Identified Issues:  
Class Imbalance:  
Models are biased toward the majority class, rendering them ineffective for predicting risky loans.  

ANN Implementation Flaw:  

Negative loss values indicate a technical error (e.g., improper loss function or unscaled outputs).  

Evaluation Metrics:  

Accuracy is misleading due to imbalance. Macro-average F1-score would better reflect performance.  

Recommendations:  
Address Class Imbalance:  

Use techniques like SMOTE, class weighting, or stratified sampling.  

Focus on metrics like F1-score, ROC-AUC, or confusion matrices for minority classes.  

Debug ANN:  

Verify loss function (binary_crossentropy is appropriate for binary labels; ensure labels are correctly encoded).  
  
Normalize outputs and check for data leakage.  

Feature Engineering:    

Explore domain-specific features (e.g., debt-to-income ratio, credit utilization).    

Use one-hot encoding instead of LabelEncoder for categorical variables to avoid ordinal bias.  

Conclusion  
While the models achieve high accuracy, their utility is limited due to class imbalance and technical flaws (e.g., ANN training). Future work should prioritize balancing the dataset, refining evaluation metrics, and correcting model implementations to improve robustness for real-world risk prediction.  
