# Supermarket Customer Analysis

**Python · Data Analysis · Statistical Testing · Business Intelligence · Customer Segmentation**  
A comprehensive data analysis project for identifying customer characteristics that predict marketing campaign response.  
The project implements robust data cleaning, feature engineering, exploratory data analysis (EDA), and inferential statistics using Python fundamentals, pandas operations, statistical testing (t-test, chi-square), and data visualization to provide actionable business insights for improving marketing campaign effectiveness.

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
  - `pandas` - Data manipulation, cleaning, and analysis
  - `numpy` - Numerical computing and array operations
  - `matplotlib` - Data visualization and plotting
  - `seaborn` - Statistical data visualization and styling
  - `scipy.stats` - Statistical tests (ttest_ind, chi2_contingency, skew)
- **Development Environment:**
  - Jupyter Notebook for interactive analysis
  - Tab-separated CSV file format for data input

## Project Structure

```
Supermarket Customer Analysis/
│
├── SupermarketCustomer.ipynb          # Main analysis notebook
├── SupermarketCustomers.csv          # Raw dataset (tab-separated)
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
   - Missing value handling (24 missing values in Income column, ~1.07% of data)
   - Duplicate checking (no duplicates found)
   - Date conversion (Dt_Customer to datetime format)
   - Outlier detection and handling (winsorization for Income using 95th percentile)
   - Feature engineering (9 new features created):
     - **TotalSpending**: Sum of all product category spending (MntWines, MntFruits, etc.)
     - **TotalPurchases**: Sum of purchases across all channels
     - **AvgTransactionValue**: Average spending per transaction
     - **Customer Tenure**: Days/Months/Years since first customer registration
     - **Customer Lifetime Value (CLV)**: Annualized spending per customer
     - **DominantChannel**: Primary purchase channel (Store/Web/Catalog)
     - **FavoriteCategory**: Most purchased product category
     - **RFM Segments**: Recency, Frequency, Monetary segmentation (R_Segment, F_Segment, M_Segment, RFM_Score)
     - **Campaign Engagement**: Total campaigns accepted and engagement rate

3. **Exploratory Data Analysis (EDA)**
   - Univariate analysis with descriptive statistics and skewness:
     - Income (mean: $51,482, median: $51,381)
     - MntWines (wine spending patterns)
     - Recency (days since last purchase)
     - NumDealsPurchases (promotion sensitivity)
     - NumWebVisitsMonth (digital engagement)
   - Categorical variable analysis:
     - Education distribution (Graduation: 50.4%, PhD: 21.7%, Master: 16.5%)
     - Marital_Status distribution (Married: 38.7%, Together: 25.9%, Single: 21.3%)
   - Response rate overview: **15.03%** (333 out of 2,216 customers)
   - Data visualization: Box plots, histograms, bar charts, count plots

4. **Inferential Analysis**
   - **Helper Functions Created:**
     - `ttest_with_effect_size()`: Performs t-test and calculates Cohen's d effect size
     - `chi2_with_effect_size()`: Performs chi-square test and calculates Cramer's V effect size
     - `compare_responders_vs_nonresponders()`: Creates side-by-side comparison visualizations
   - **Independent t-tests** for numeric variables:
     - Income vs Response
     - MntWines vs Response
     - Additional variables: TotalSpending, TotalPurchases, Recency, NumCatalogPurchases, NumWebPurchases, NumStorePurchases, CLV, AvgTransactionValue
   - **Chi-square tests** for categorical variables:
     - Education vs Response
     - Marital_Status vs Response
   - **Effect size calculations**: Cohen's d (for t-tests) and Cramer's V (for chi-square tests)
   - **Correlation analysis**: Correlation matrix heatmap showing relationships between all numeric variables and Response

5. **Business Insights & Recommendations**
   - Key findings summary
   - Actionable recommendations for campaign targeting

## Key Findings

### Response Rate
- **15.03%** of customers (333 out of 2,216) responded to the campaign

### Significant Predictors

1. **Income**
   - Responders have significantly higher income (USD 59,209 vs USD 50,116)
   - t-statistic = 7.10, p-value < 0.001
   - Effect size: Small-Medium (Cohen's d)
   - Percentage difference: 18.1% higher for responders

2. **Wine Spending (MntWines)**
   - Responders spend significantly more on wine (USD 502.62 vs USD 270.16)
   - t-statistic = 9.50, p-value < 0.001
   - Strong predictor of campaign response
   - Percentage difference: 86.0% higher for responders

3. **Education Level**
   - Significant association with campaign response (χ² = 23.15, p-value = 0.0001)
   - Higher education (Graduate, PhD) shows higher response rates

4. **Marital Status**
   - Significant association with campaign response (χ² = 53.51, p-value < 0.001)
   - Single (22.51%), Divorced (20.69%), and Widow (23.68%) have higher response rates
   - Married (11.44%) and Together (10.47%) have lower response rates

### Additional Significant Findings

5. **TotalSpending**
   - Strongest predictor (correlation: 0.264)
   - Responders: USD 985.66 vs Non-responders: USD 540.12
   - Effect size: Medium (Cohen's d = 0.77)

6. **Recency**
   - Negative correlation with response (-0.200)
   - Responders have lower recency (35.26 days vs 51.44 days)
   - More recent customers are more likely to respond

7. **NumCatalogPurchases**
   - Strong positive correlation (0.220)
   - Responders make more catalog purchases (4.20 vs 2.40)

### Customer Profile Most Likely to Respond
- Income > USD 60,000
- High wine spending (MntWines > USD 400)
- High total spending
- Higher education background (Graduate, PhD)
- Non-traditional marital status (Single, Divorced, Widow)
- Recent purchase activity (low recency)
- Frequent catalog purchases

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
2. Ensure `SupermarketCustomers.csv` is in the same directory (note: file is tab-separated)
3. Install required libraries:
   ```bash
   pip install pandas numpy matplotlib seaborn scipy jupyter
   ```
4. Open `SupermarketCustomer.ipynb` in Jupyter Notebook
5. Run all cells sequentially (the notebook is structured with clear sections)

```bash
jupyter notebook SupermarketCustomer.ipynb
```

**Note:** The CSV file uses tab-separated values (`sep='\t'`), not comma-separated.

### Output Files

- `cleaned_supermarket_data.csv` - Cleaned dataset with engineered features

## Statistical Methods Used

- **Descriptive Statistics:** 
  - Mean, median, quartiles, standard deviation
  - Skewness calculation for distribution analysis
  - Value counts and proportions for categorical variables
  
- **Inferential Statistics:**
  - **Independent t-test** (Welch's t-test with unequal variances) for numeric variables
  - **Chi-square test of independence** for categorical variables
  - **Effect size calculations:**
    - Cohen's d for t-tests (interpretation: <0.2 Negligible, <0.5 Small, <0.8 Medium, ≥0.8 Large)
    - Cramer's V for chi-square tests (interpretation: <0.1 Negligible, <0.3 Small, <0.5 Medium, ≥0.5 Large)
  - **Correlation analysis** (Pearson correlation matrix)
  
- **Data Visualization:**
  - Box plots (distribution and outliers)
  - Histograms with KDE (density estimation)
  - Bar charts (categorical distributions, response rates)
  - Stacked bar charts (proportion comparisons)
  - Correlation heatmaps (relationship visualization)
  - Side-by-side comparison plots (responders vs non-responders)

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

