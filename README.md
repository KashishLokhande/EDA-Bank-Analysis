```markdown
# Exploratory-Data-Analysis-EDA-in-Banking-Using-Python

A comprehensive exploratory data analysis of bank marketing campaign data to understand factors influencing term deposit subscriptions and optimize future marketing strategies using Python's Pandas framework.

## 📋 Table of Contents
- [Goals of the Project](#goals-of-the-project)
- [Materials and Methods](#materials-and-methods)
- [Libraries Used](#libraries-used)
- [Dataset Description](#dataset-description)
- [Key Business Questions](#key-business-questions)
- [Project Outline](#project-outline)
- [Key Findings](#key-findings)
- [Visualizations](#visualizations)
- [Installation & Usage](#installation--usage)
- [Project Structure](#project-structure)
- [Tasks Completed](#tasks-completed)
- [Future Improvements](#future-improvements)

## 🎯 Goals of the Project

1. **Explore a banking dataset with Pandas framework** - Master data manipulation and analysis techniques
2. **Build pivot tables** - Create multi-dimensional analysis for business insights
3. **Visualize the dataset with various plot types** - Develop comprehensive visual representations of patterns

## 📊 Materials and Methods

The data used is a subset of an open source **Bank Marketing Data Set** from the UCI ML repository: https://archive.ics.uci.edu/ml/citation_policy.html

> This dataset is publicly available for research. The details are described in [Moro et al., 2014].

The project addresses the task of preliminary analysis of positive responses (term deposits) to direct bank calls. This is essentially a bank scoring problem - predicting client behavior (loan default, deposit subscription, etc.) based on client characteristics.

### Dataset Details:
- **Source**: UCI Machine Learning Repository
- **Records**: 41,188 observations
- **Features**: 21 (20 input features + 1 target variable)
- **Target**: Term deposit subscription (yes/no)
- **No missing values** - Complete dataset

## 🛠️ Libraries Used

1. **NUMPY** - Numerical computations and array operations
2. **PANDAS** - Data manipulation, analysis, and pivot tables
3. **MATPLOTLIB** - Data visualization and plotting

### Additional Configuration:
```python
# Display settings for better readability
pd.set_option("precision", 2)
pd.options.display.float_format = '{:.2f}'.format
plt.rcParams["figure.figsize"] = (8, 6)
```

## 📁 Dataset Description

### Features Overview:
**Input Features (20):**
- **Demographics**: age, job, marital status, education
- **Financial Status**: default, housing loan, personal loan
- **Contact Information**: contact type, month, day of week, duration
- **Campaign Data**: campaign, pdays, previous, poutcome
- **Economic Indicators**: emp.var.rate, cons.price.idx, cons.conf.idx, euribor3m, nr.employed

**Target Feature:**
- **y**: Has the client subscribed to a term deposit? (binary: yes/no)

### Data Types:
- **Numerical Features**: 10 (int64 and float64)
- **Categorical Features**: 11 (object type)

## ❓ Key Business Questions

The analysis addresses five critical questions:

1. **What is the share of clients attracted in our source data?**
   - **Answer**: 11.3% (4,640 out of 41,188 clients)

2. **What are the mean values of numerical features among the attracted clients?**
   - **Average age**: 40.91 years
   - **Average campaign contacts**: 2.05

3. **What is the average call duration for the attracted clients?**
   - **Answer**: 9 minutes 13 seconds (553 seconds)

4. **What is the average age among the attracted and unmarried clients?**
   - **Answer**: 31 years

5. **What is the average age and call duration for different types of client employment?**
   - Detailed pivot tables reveal job-specific patterns

## 📋 Project Outline

### 1. General Part
   
#### i) Libraries Import
- Data downloading using wget
- Essential libraries configuration
- Display settings optimization

#### ii) Dataset Exploration
- **Data shape**: 41,188 × 21
- **Statistical summaries** using `describe()`
- **Value counts** for categorical variables
- **Data sorting** by single and multiple columns
- **Function applications** using `apply()` and `map()`
- **Advanced indexing** for targeted analysis

#### iii) Pivot Tables
- **Cross tabulations** of deposit subscription by marital status
- **Multi-dimensional analysis** of age and duration by job type
- **Normalized frequency tables** for percentage insights

#### iv) Visualization in Pandas
- **Scatter matrices** for numerical features relationships
- **Histograms** for distribution analysis
- **Box plots** for outlier detection and group comparisons

### 2. Tasks
- Top 10 clients by contact frequency
- Median age and contact analysis by education level
- Age distribution visualization by education

## 📈 Key Findings

### Client Profile Analysis:
- **Overall subscription rate**: Only 11.3% - significant improvement potential
- **Typical subscriber**: ~41 years old, requires ~2 contacts
- **Marital status impact**: 61% of clients are married
- **Age distribution**: Most clients between 25-50 years (active working population)

### Campaign Effectiveness:
- **Optimal call duration**: ~9-10 minutes for conversions
- **Best days**: Mondays and Thursdays show higher engagement
- **Peak months**: November and August
- **Longest calls**: Over 1 hour, primarily for engaged prospects

### Statistical Insights:
- **Age distribution**: Near-normal
- **Duration/Campaign**: Geometric distribution pattern
- **Outliers**: Married/divorced clients over 70, unmarried over 50

## 📊 Visualizations

### 1. Scatter Matrix
```python
pd.plotting.scatter_matrix(df[["age", "duration", "campaign"]], 
                          figsize=(15, 15), diagonal="kde")
```
- Shows pairwise relationships between numerical features
- Diagonal KDE plots reveal distribution types

### 2. Histograms
- Individual age histogram shows 25-50 year concentration
- Combined histograms for all numerical features

### 3. Box Plots
- Age by marital status
- Age by education level
- Combined analysis of age by marital status and housing loan

## 🚀 Installation & Usage

### Prerequisites:
```bash
pip install pandas numpy matplotlib jupyter wget
```

### Running the Analysis:

1. **Clone the repository**
```bash
git clone https://github.com/Strik3r10/Exploratory-Data-Analysis-EDA-in-Banking-Using-Python.git
cd Exploratory-Data-Analysis-EDA-in-Banking-Using-Python
```

2. **Download the dataset**
```bash
wget https://archive.ics.uci.edu/ml/machine-learning-databases/00222/bank-additional.zip
# Alternative URL:
# wget https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/EDA_Pandas_Banking_L1/bank-additional.zip
unzip -o -q bank-additional.zip
```

3. **Run the analysis**
```bash
jupyter notebook banking_eda_analysis.ipynb
```

## 📁 Project Structure
```
Exploratory-Data-Analysis-EDA-in-Banking-Using-Python/
│
├── bank-additional/
│   └── bank-additional-full.csv          # Main dataset
│
├── notebooks/
│   └── banking_eda_analysis.ipynb        # Main analysis notebook
│
├── visualizations/                       # Generated plots
│   ├── scatter_matrix.png
│   ├── age_histogram.png
│   └── boxplots/
│
├── README.md
└── requirements.txt
```

## ✅ Tasks Completed

### Task 1: Top 10 Clients by Contact Frequency
- Identified clients with campaign contacts ranging from 35-56 attempts
- Revealed persistence patterns in customer outreach

### Task 2: Education Level Analysis
- Created comprehensive pivot tables showing median age and contact patterns
- Segmented by education categories (basic.4y through university.degree)

### Task 3: Age Distribution by Education
- Generated box plots revealing age patterns across education levels
- Identified outliers and typical age ranges for each segment

## 🔄 Future Improvements

1. **Predictive Modeling**
   - Implement machine learning models to predict term deposit likelihood
   - Feature engineering based on EDA insights

2. **Advanced Analytics**
   - Time series analysis of economic indicators
   - Correlation analysis between features
   - Statistical hypothesis testing

3. **Interactive Dashboards**
   - Create Plotly/Dash dashboards for real-time exploration
   - Implement filters for dynamic analysis

4. **Business Strategy**
   - Cost-benefit analysis of different campaign approaches
   - ROI calculations for targeted segments
   - A/B testing framework development

## 👥 Contributors
This project demonstrates advanced EDA techniques for banking data analysis and strategic marketing insights.

## 📄 License & Citation
The dataset is publicly available from UCI ML Repository. Please cite:
> [Moro et al., 2014] S. Moro, P. Cortez and P. Rita. A Data-Driven Approach to Predict the Success of Bank Telemarketing. Decision Support Systems, Elsevier, 62:22-31, June 2014.


