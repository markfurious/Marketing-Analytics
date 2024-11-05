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
