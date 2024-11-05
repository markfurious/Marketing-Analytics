
# Marketing Campaign Analysis

## Project Overview
This project involves analyzing customer data to evaluate the effectiveness of recent marketing campaigns for a fictional company. The primary goal is to understand which factors drive campaign success, identify customer segments, and recommend data-driven solutions to enhance future campaigns.

## Table of Contents
- [Project Overview](#project-overview)
- [Data](#data)
- [Project Structure](#project-structure)
- [Objectives](#objectives)
- [Setup and Installation](#setup-and-installation)
- [Methodology](#methodology)
  - [1. Data Cleaning and Preprocessing](#1-data-cleaning-and-preprocessing)
  - [2. Exploratory Data Analysis (EDA)](#2-exploratory-data-analysis-eda)
  - [3. Statistical Analysis](#3-statistical-analysis)
  - [4. Data Visualization](#4-data-visualization)
- [Results and Insights](#results-and-insights)
- [Conclusion](#conclusion)
- [Usage](#usage)
- [Requirements](#requirements)
- [Acknowledgements](#acknowledgements)

## Data
The dataset used in this analysis contains customer demographic information, purchasing behavior, and campaign engagement data. Key columns include:
- **Demographics**: Age, income, education, marital status, country.
- **Purchasing Behavior**: Amounts spent on various products (wine, meat, fish, etc.), number of purchases by channel.
- **Campaign Responses**: Whether a customer accepted each of five recent campaigns.

## Project Structure
The project is organized as follows:
- **data/**: Folder containing the `marketing_data.csv` file.
- **notebooks/**: Jupyter notebooks used for analysis.
  - `main.ipynb`: The primary notebook, including data cleaning, EDA, statistical analysis, and visualizations.
- **README.md**: Project documentation.
- **requirements.txt**: Dependencies required for this project.

## Objectives
1. **Exploratory Data Analysis (EDA)**:
   - Identify null values and outliers, handle missing data, and detect patterns in the data.
   - Assess variables for potential transformations.
   - Engineer useful features.
   - Detect and visualize any patterns or anomalies.

2. **Statistical Analysis**:
   - Perform statistical tests and regressions to understand the impact of various factors on campaign success.
   - Answer questions such as:
     - What factors are related to the number of store purchases?
     - Does the US perform better than other regions in terms of total purchases?
     - Are customers who spend on gold more conservative?
     - Do “Married PhD candidates” spend more on fish?

3. **Data Visualization**:
   - Visualize key insights, including:
     - The most successful marketing campaign.
     - Profile of the average customer.
     - Top-performing products and underperforming channels.

## Setup and Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/marketing-campaign-analysis.git
   ```
2. Install the required packages:
   ```bash
   pip install -r requirements.txt
   ```
3. Open the main notebook:
   ```bash
   jupyter notebook notebooks/main.ipynb
   ```

## Methodology

### 1. Data Cleaning and Preprocessing
   - **Remove Null Values**: Missing values in the `Income` column are filled with the median income.
   - **Convert Income to Numeric**: Remove dollar signs and commas to ensure `Income` is numeric.
   - **Date Conversion**: Convert `Dt_Customer` to datetime format to calculate customer tenure.
   - **Feature Engineering**: Created new columns for `CustomerTenure`, `TotalSpending`, `TotalPurchases`, and `FamilySize`.

**Example Code**:
```python
# Convert 'Income' to numeric and fill missing values
marketing_data['Income'] = marketing_data['Income'].replace('[\$,]', '', regex=True).astype(float)
marketing_data['Income'].fillna(marketing_data['Income'].median(), inplace=True)

# Convert 'Dt_Customer' to datetime and calculate tenure
marketing_data['Dt_Customer'] = pd.to_datetime(marketing_data['Dt_Customer'])
reference_date = pd.to_datetime('2024-01-01')
marketing_data['CustomerTenure'] = (reference_date - marketing_data['Dt_Customer']).dt.days
```

### 2. Exploratory Data Analysis (EDA)
   - **Null Value and Outlier Detection**: Identified missing values and extreme values in the data.
   - **Feature Exploration**: Examined distributions of key variables and correlations between them.
   - **Pattern Detection**: Looked for any seasonal trends or anomalies in purchasing behavior.

**Example Code**:
```python
import seaborn as sns
import matplotlib.pyplot as plt

# Visualize correlations with a heatmap
plt.figure(figsize=(12, 8))
sns.heatmap(marketing_data.corr(), annot=True, fmt=".2f", cmap='coolwarm')
plt.title("Correlation Heatmap of Numerical Features")
plt.show()
```

### 3. Statistical Analysis
   - **Regression Analysis**: Ran multiple regressions to determine factors associated with store purchases.
   - **Hypothesis Testing**: Used t-tests and ANOVA to analyze differences in purchasing behavior by demographics and geography.

**Example Code**:
```python
import statsmodels.api as sm

# Factors Related to Store Purchases
X = marketing_data[['Income', 'FamilySize', 'CustomerTenure', 'TotalAcceptedCampaigns']]
y = marketing_data['NumStorePurchases']
X = sm.add_constant(X)
model = sm.OLS(y, X).fit()
print(model.summary())
```

### 4. Data Visualization
   - **Campaign Performance**: Visualized campaign acceptance rates to identify the most successful campaign.
   - **Customer Profile**: Displayed the characteristics of the average customer.
   - **Product and Channel Performance**: Plotted spending on products and usage of purchasing channels.

**Example Code**:
```python
# Plot the most successful campaign
campaign_columns = ['AcceptedCmp1', 'AcceptedCmp2', 'AcceptedCmp3', 'AcceptedCmp4', 'AcceptedCmp5']
acceptance_rates = marketing_data[campaign_columns].mean()
acceptance_rates.plot(kind='bar')
plt.title("Campaign Acceptance Rates")
plt.xlabel("Campaign")
plt.ylabel("Acceptance Rate")
plt.show()
```

## Results and Insights
- **Campaign Success**: Certain campaigns showed higher acceptance among specific demographics, suggesting targeted messaging could enhance engagement.
- **Customer Profile**: The typical customer profile shows middle-aged individuals with moderate income, purchasing products like wine and meat.
- **Product Preferences**: Wine and meat are the most popular products, indicating strong customer interest in these categories.
- **Channel Performance**: Online channels may be underutilized, presenting an opportunity to improve digital engagement.

## Conclusion
This analysis provides valuable insights into campaign effectiveness and customer behavior. By focusing on high-engagement segments, optimizing underperforming channels, and tailoring campaigns based on customer demographics, the company can enhance future marketing efforts.

## Usage
This notebook can be used as a reference for similar marketing analyses, especially for:

- Analyzing customer demographics and purchasing behavior.
- Conducting exploratory data analysis and feature engineering.
- Running statistical tests and visualizations to derive actionable insights.

## Requirements
- Python 3.6+
- Required packages: See `requirements.txt`

## Acknowledgements
This project was created for a marketing analytics assignment. The dataset and analysis techniques are for educational purposes only.
