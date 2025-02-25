# Safeguarding Employment: Unmasking Fraudulent vs. Legitimate Jobs with Machine Learning

## Project Overview
This project addresses the critical problem of fraudulent job advertisements, which pose significant risks to job seekers. With employment scams causing estimated annual losses of $2 billion and affecting millions of individuals, this research aims to develop an effective machine learning solution to distinguish between legitimate and fraudulent job postings using conventional information available on job search websites.

## Problem Statement
Scammers create sophisticated fake job advertisements that appear legitimate but are designed to steal personal information or perpetrate various forms of fraud. This project seeks to answer whether machine learning techniques can effectively identify fraudulent job listings based on common features found in job advertisements.

## Dataset Description
The dataset contains 17,880 job descriptions (with approximately 800 fraudulent listings) and includes:

- Basic information: job_id, title, location, department, salary_range
- Company details: company_profile, has_company_logo
- Job specifics: description, requirements, benefits, telecommuting option
- Employment details: employment_type, required_experience, required_education
- Industry information: industry, function
- Binary target variable: fraudulent (indicating legitimate or fraudulent status)

## Challenges
- Significant class imbalance (only ~4.5% of listings are fraudulent)
- Substantial missing values across features (67,148 total missing entries)

## Data Preparation
- Comprehensive preprocessing of text features
- Extraction of location data into country, state, and city variables
- Feature engineering from text data (length calculations, URL/email/phone detection)
- Missing value handling by replacing nulls with "Unspecified"
- Label encoding for categorical variables with limited values
- Feature selection based on correlation analysis and VIF (Variance Inflation Factor)

## Methodology
Several machine learning approaches were implemented to address the class imbalance:

1. **Sampling Techniques**:
   - Random Sampling
   - Stratified Sampling
   - SMOTE (Synthetic Minority Over-sampling Technique)
   - Bootstrapping
   - Undersampling
   - Hybrid approach (Undersampling-Oversampling)

2. **Model Implementation**:
   - XGBoost algorithm with parameter optimization
   - 10-fold cross-validation
   - Threshold optimization to maximize F-measure

3. **Feature Importance Analysis**:
   - SHAP (SHapley Additive exPlanations) to determine feature importance
   - Model retraining with selected features

## Performance Evaluation
Due to class imbalance, the following metrics were prioritized over accuracy:
- Precision: Minimizes false positives (legitimate jobs incorrectly flagged as fraudulent)
- Recall: Maximizes detection of truly fraudulent listings
- F-measure: Balanced metric combining precision and recall

## Results
After optimizing with SHAP and threshold adjustments:

| Method | Recall | Precision | F-measure | Accuracy |
|--------|--------|-----------|-----------|----------|
| Stratified Sampling | 0.694 | 0.896 | 0.782 | 0.981 |
| Random Sampling | 0.717 | 0.822 | 0.766 | 0.978 |
| SMOTE | 0.723 | 0.762 | 0.742 | 0.976 |
| Oversampling-Undersampling | 0.699 | 0.720 | 0.709 | 0.972 |
| Bootstrapping | 0.746 | 0.592 | 0.660 | 0.963 |
| Undersampling | 0.786 | 0.533 | 0.636 | 0.956 |

## Conclusions
- Different sampling techniques offer various trade-offs between precision and recall
- Stratified Sampling achieved the highest F-measure (0.782) and overall accuracy (0.981)
- The choice of method depends on specific priorities (higher precision vs. higher recall)

## Future Enhancements
- Deep Learning techniques to analyze text content more thoroughly
- Advanced NLP models (BERT, Word2Vec, Transformers)
- Web application deployment for broader access using Flask or Streamlit

## References
1. Kelly J. Fake Job Scams Are Becoming More Common—Here's How To Protect Yourself. Forbes, 2023.
2. Group O. What Is a Fake Job Posting and Ways to Spot it? Omnes Group, 2021.
3. Bansal S. Real/Fake Job Posting Prediction. Kaggle, 2019.
4. Sharma S. Real/Fake Job Posting Prediction. Medium, 2023.

## Author
Matteo Pasotti, Università degli Studi di Milano Bicocca, CdLM Data Science
