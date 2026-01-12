# Supermarket Customer Analysis

## Project Overview

This project analyzes supermarket customer data to identify characteristics that predict campaign response. The analysis uses various data science techniques including data cleaning, feature engineering, exploratory data analysis (EDA), and inferential statistics to provide actionable business insights for improving marketing campaign effectiveness.

**Problem Statement:** Identify customer characteristics that are most likely to respond to promotional campaigns in the future.

## Objectives

1. Describe customer characteristics based on campaign response
2. Identify features that are most correlated with campaign success
3. Provide actionable recommendations for the supermarket to improve campaign effectiveness

## Dataset

- **Source:** Supermarket Customers Dataset
- **Size:** 2,240 rows × 29 columns (after cleaning: 2,216 rows)
- **Features:** 
  - Demographics: Year_Birth, Education, Marital_Status, Income
  - Purchase Behavior: MntWines, MntFruits, MntMeatProducts, MntFishProducts, MntSweetProducts, MntGoldProds
  - Channel Usage: NumWebPurchases, NumCatalogPurchases, NumStorePurchases, NumDealsPurchases
  - Campaign Response: Response (target variable)
  - Other: Recency, NumWebVisitsMonth, AcceptedCmp1-5, etc.

## Tools & Technologies

- **Python 3.x**
- **Libraries:**
  - `pandas` - Data manipulation and analysis
  - `numpy` - Numerical computing
  - `matplotlib` - Data visualization
  - `seaborn` - Statistical data visualization
  - `scipy.stats` - Statistical tests (t-test, chi-square)

## Project Structure

```
Capstone2/
│
├── SupermarketCustomer.ipynb          # Main analysis notebook
├── SupermarketCustomers.csv          # Raw dataset
├── cleaned_supermarket_data.csv      # Cleaned dataset (output)
├── README.md                          # This file
└── Supermarket Customers Data Dictionary.pdf  # Data dictionary
```

## Analysis Workflow

1. **Data Overview**
   - Initial data exploration
   - Data type checking
   - Missing value identification

2. **Data Cleaning & Preparation**
   - Missing value handling (24 missing values in Income column)
   - Outlier detection and handling (winsorization for Income)
   - Feature engineering (9 new features created):
     - TotalSpending
     - TotalPurchases
     - AvgTransactionValue
     - Customer Tenure (Days/Months/Years)
     - Customer Lifetime Value (CLV)
     - DominantChannel
     - FavoriteCategory
     - RFM Segments
     - Campaign Engagement

3. **Exploratory Data Analysis (EDA)**
   - Univariate analysis (Income, MntWines, Recency, etc.)
   - Categorical variable analysis (Education, Marital_Status)
   - Response rate overview (15.03%)

4. **Inferential Analysis**
   - Independent t-tests for numeric variables (Income, MntWines)
   - Chi-square tests for categorical variables (Education, Marital_Status)
   - Effect size calculations (Cohen's d, Cramer's V)
   - Additional variable analysis

5. **Business Insights & Recommendations**
   - Key findings summary
   - Actionable recommendations for campaign targeting

## Key Findings

### Response Rate
- **15.03%** of customers (333 out of 2,216) responded to the campaign

### Significant Predictors

1. **Income**
   - Responders have significantly higher income (USD 60,209 vs USD 50,839)
   - t-statistic = 6.70, p-value < 0.001
   - Effect size: Small-Medium (Cohen's d)

2. **Wine Spending (MntWines)**
   - Responders spend significantly more on wine (USD 502.62 vs USD 270.16)
   - t-statistic = 9.50, p-value < 0.001
   - Strong predictor of campaign response

3. **Education Level**
   - Significant association with campaign response (χ² = 23.15, p-value = 0.0001)
   - Higher education (Graduate, PhD) shows higher response rates

4. **Marital Status**
   - Significant association with campaign response
   - Single, Divorced, and Widow have higher response rates (≥ 20%)
   - Married and Together tend to have lower response rates

### Customer Profile Most Likely to Respond
- Income > USD 60,000
- High wine spending
- Higher education background (Graduate, PhD)
- Non-traditional marital status (Single, Divorced, YOLO, Alone)

## Recommendations

1. **Target campaigns to high-income customers**
   - Focus on customers with income > USD 60,000
   - Optimize income-based segmentation to increase conversion

2. **Focus promotions on high wine spenders**
   - Target customers with high MntWines values
   - Suitable for upselling campaigns and loyalty programs

3. **Use combined behavioral and demographic segmentation**
   - Combine Income, MntWines, Education, and Marital_Status
   - Build classification models for improved targeting accuracy

**Expected Impact:** With proper segmentation, response rate can potentially increase from 15% to 22-25% for high-priority segments while reducing ineffective promotional costs.

## How to Run

### Prerequisites

```bash
pip install pandas numpy matplotlib seaborn scipy jupyter
```

### Running the Analysis

1. Clone or download this repository
2. Ensure `SupermarketCustomers.csv` is in the same directory
3. Open `SupermarketCustomer.ipynb` in Jupyter Notebook
4. Run all cells sequentially

```bash
jupyter notebook SupermarketCustomer.ipynb
```

### Output Files

- `cleaned_supermarket_data.csv` - Cleaned dataset with engineered features

## Statistical Methods Used

- **Descriptive Statistics:** Mean, median, quartiles, skewness
- **Inferential Statistics:**
  - Independent t-test (for numeric variables)
  - Chi-square test (for categorical variables)
  - Effect size calculations (Cohen's d, Cramer's V)
- **Data Visualization:** Box plots, histograms, bar charts, heatmaps

## Project Status

✅ **Completed**
- Data cleaning and preparation
- Feature engineering
- Exploratory data analysis
- Inferential statistical analysis
- Business insights and recommendations

## Future Work

1. Implement segmentation based on recommendations
2. A/B testing for campaign message and timing optimization
3. Continuous monitoring and evaluation for improvement
4. Build predictive models (classification) for campaign response
5. Develop automated segmentation pipeline

## Author

Capstone Project Module 2 - Data Analyst Bootcamp

## License

This project is for educational purposes.

## References

- Dataset: Supermarket Customers Dataset
- Statistical methods: Independent t-test, Chi-square test, Effect size measures
- Tools: Python, Jupyter Notebook, pandas, scipy

---

**Note:** This analysis provides actionable insights for improving marketing campaign effectiveness through data-driven customer segmentation.

