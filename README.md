
# Email Marketing Campaign Analysis

## Overview
This project analyzes email campaign data to optimize click-through rates and engagement. Using machine learning models, the project predicts which users are most likely to open emails and click on links, allowing for more targeted and effective email marketing campaigns.

## Dataset
The analysis uses three main datasets:
- `email_table.csv`: Contains information about sent emails including email text type, version, weekday, and user country.
- `email_opened_table.csv`: Records which emails were opened by users.
- `link_clicked_table.csv`: Records which email links were clicked by users.

### Dataset Characteristics
- **Email Types**: Long emails (50,276) and short emails (49,724)
- **Email Versions**: Generic (50,209) and personalized (49,791)
- **User Countries**: Primarily US (60,099), UK (19,939), FR (9,995), and ES (9,967)
- **Baseline Metrics**:
  - Open Rate: 10.35%
  - Click-Through Rate (CTR): 2.12%

## Features
- **Exploratory Data Analysis**: Analyzing email open rates and click-through rates across different factors
- **Machine Learning Models**: Predicting which users are most likely to click on email links
- **Campaign Optimization**: Identifying the top percentage of users who are most likely to engage

## Key Findings

### Email Performance by Version
- Personalized emails significantly outperform generic ones:
  - Personalized: 12.78% open rate, 2.73% CTR
  - Generic: 7.93% open rate, 1.51% CTR

### Email Performance by Content Length
- Short emails perform better than long ones:
  - Short emails: 11.59% open rate, 2.39% CTR
  - Long emails: 9.12% open rate, 1.85% CTR

### Performance by Day of Week
- Midweek days show the highest engagement:
  - Tuesday: 12.05% open rate, 2.49% CTR
  - Wednesday: 12.03% open rate, 2.76% CTR
  - Thursday: 11.84% open rate, 2.44% CTR
  - Monday: 11.61% open rate, 2.29% CTR
- Weekend days show lower engagement

### Performance by Country
- UK: 12.02% open rate, 2.47% CTR
- FR: 4.06% open rate, 0.80% CTR
- ES: 3.91% open rate, 0.83% CTR

### Time of Day Analysis
- Highest CTR during hour 23 (11 PM): 4.14%
- Other peak engagement times: 
  - Hour 24 (12 AM): 2.90%
  - Hour 10 (10 AM): 2.82%
  - Hour 11 (11 AM): 2.71%

## Machine Learning Models
The project evaluates several machine learning models:

### Standard Models
- Random Forest
- Logistic Regression
- Support Vector Classifier (SVC)
- K-Nearest Neighbors

### Models with SMOTE (Addressing Class Imbalance)
- Random Forest: 82.05% accuracy, ROC AUC 0.5902
- Logistic Regression: 67.12% accuracy, ROC AUC 0.7077
- SVC: 58.59% accuracy, ROC AUC 0.7034
- K-Nearest Neighbors: 93.94% accuracy, ROC AUC 0.5719

### Ensemble Model
- A voting classifier combining all models achieved 97.88% accuracy

## Campaign Optimization Results
- By targeting the top 20% of users most likely to click (based on model predictions):
  - Achieved CTR of 9.20% (vs. baseline 2.12%)
  - 7.08% improvement in CTR
- When simulated on test data (top 30% targeted):
  - Achieved CTR of 2.33%
  - 0.21% improvement over the baseline

## Technical Implementation
- **Data Processing**: Pandas for data manipulation
- **Visualization**: Matplotlib and Seaborn with dark theme
- **Machine Learning**: scikit-learn for model training and evaluation
- **Class Imbalance Handling**: SMOTE for synthetic minority oversampling

## Usage
```python
# Load datasets
email_df = pd.read_csv('email_table.csv')
opened_df = pd.read_csv('email_opened_table.csv')
clicked_df = pd.read_csv('link_clicked_table.csv')

# Add target variables
email_df['opened'] = email_df['email_id'].isin(opened_df['email_id']).astype(int)
email_df['clicked'] = email_df['email_id'].isin(clicked_df['email_id']).astype(int)

# Train models and predict
# (See code for detailed implementation)
```

## Conclusion
This project demonstrates that machine learning can effectively optimize email marketing campaigns by identifying users most likely to engage. Key recommendations:
1. Use personalized rather than generic emails
2. Prefer shorter email content
3. Send emails mid-week (Tuesday-Thursday)
4. Target appropriate times (10-11 AM, 11 PM)
5. Consider regional differences in engagement

By implementing these findings and using the predictive models to target the most receptive users, marketers can significantly improve their campaign performance and ROI.
