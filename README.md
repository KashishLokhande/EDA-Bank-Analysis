# Exploratory Data Analysis (EDA) in Banking Using Python

An exploratory analysis of bank telemarketing data to understand which clients subscribe to a term deposit, and what the bank can do better in its next campaign. Done in Python with Pandas, NumPy and Matplotlib.


## Table of Contents
- [Goals of the Project](#goals-of-the-project)
- [Materials and Methods](#materials-and-methods)
- [Libraries Used](#libraries-used)
- [Dataset Description](#dataset-description)
- [Key Business Questions](#key-business-questions)
- [Project Outline](#project-outline)
- [Key Findings](#key-findings)
- [Visualizations](#visualizations)
- [Recommendations](#recommendations)
- [Limitations](#limitations)
- [Project Structure](#project-structure)
- [Tasks Completed](#tasks-completed)
- [Future Improvements](#future-improvements)

## Goals of the Project

1. Explore a banking dataset with the Pandas framework
2. Check the quality of the data
3. Build pivot tables and crosstabs
4. Find which client segments are most likely to subscribe
5. Visualize the dataset with various plot types
6. Turn the results into recommendations for the next campaign

## Materials and Methods

The data is the open source Bank Marketing Data Set (with social and economic context) from the UCI ML repository: https://archive.ics.uci.edu/dataset/222/bank+marketing

> This dataset is publicly available for research. The details are described in [Moro et al., 2014].

The task is a preliminary analysis of positive responses (term deposits) to direct calls from a bank. In essence it is a bank scoring problem: the behavior of a client is studied through the characteristics of the client and the history of the campaign.

The first part of the notebook follows the structure of the IBM Skills Network guided lab on EDA with Pandas in Banking. The data quality checks, segment analysis, charts and recommendations are my own extension.

Dataset details:
- Source: UCI Machine Learning Repository, file `bank-additional-full.csv`
- Records: 41,188 calls, ordered by date (May 2008 to November 2010)
- Features: 21 (20 input features and 1 target)
- Target: term deposit subscription (yes/no)
- There are no null values, but missing information is coded as the text `unknown`

## Libraries Used

1. NumPy - numerical operations
2. Pandas - data manipulation, groupby and pivot tables
3. Matplotlib - plotting

Display settings used in the notebook:
```python
pd.set_option("display.precision", 2)
pd.options.display.float_format = '{:.2f}'.format
plt.rcParams["figure.figsize"] = (8, 6)
```

## Dataset Description

Input features (20):
- Client data: age, job, marital status, education
- Financial status: default, housing loan, personal loan
- Last contact: contact type, month, day of week, duration
- Campaign data: campaign, pdays, previous, poutcome
- Economic indicators: emp.var.rate, cons.price.idx, cons.conf.idx, euribor3m, nr.employed

Target feature:
- y: has the client subscribed to a term deposit? (yes/no)

Data types:
- 10 numerical features (int64 and float64)
- 11 categorical features (object)

## Key Business Questions

The analysis answers ten questions:

1. What is the share of clients attracted in the source data? 11.3% (4,640 of 41,188), so the target is imbalanced.
2. What are the mean values of numerical features among the attracted clients? Average age is 40.91 years and about 2 contacts (2.05).
3. What is the average call duration for the attracted clients? 553 seconds, about 9 min 13 sec.
4. What is the average age of attracted clients who are single? 31 years.
5. What is the average age and call duration for different types of employment? Age differs a lot by job (students about 26, retired about 62), call duration is similar for all jobs.
6. Does the data have quality problems? 12 duplicate rows, `unknown` values in 6 columns (most in `default`, about 21%), and `pdays = 999` for 96% of clients.
7. How do attracted clients differ from the others? They talked longer (553 vs 221 seconds), had more earlier contacts, and were reached when interest rates were lower.
8. Which client segments subscribe most? Covered in Key Findings.
9. Do repeated calls to the same client help? No, covered in Key Findings.
10. What should the bank change in the next campaign? Listed under Recommendations.

## Project Outline

1. General part
   - Libraries import: libraries and display settings
   - Dataset exploration: shape, types, `describe()`, `value_counts()`, sorting, `apply()` and `map()`, indexing
   - Data quality checks: duplicates, `unknown` values, special codes
   - Pivot tables: crosstabs of subscription by marital status, age and duration by job
   - Visualization in Pandas: scatter matrix, histograms, box plots
   - Segment analysis: subscription rate by job, education, age group, contact type, month, previous outcome and number of contacts
   - Insight charts: rate by job and month, duration by outcome, correlation with the target
2. Tasks
   - Top 10 clients by number of contacts
   - Median age and contacts by education level
   - Age distribution by education level
3. Conclusions and recommendations

## Key Findings

Client profile:
- Students (31.4%) and retired clients (25.2%) have the highest subscription rates. Blue-collar (6.9%) and services (8.1%) workers have the lowest.
- The rate is highest for clients aged 65 and older (46.8%) and for those 25 or younger (20.9%). Clients between 36 and 55 are under 9%, although they are the largest group.
- Clients with a university degree (13.7%) subscribe more often than those with basic education (7.8% to 10.2%).
- Clients who subscribed in an earlier campaign did so again in 65% of cases, against 8.8% for new clients.

Campaign effectiveness:
- Cellular contact converts at 14.7% against 5.2% for telephone, and it does better in every job group.
- The rate falls from 13% at the first contact to about 5% at the tenth.
- March, September, October and December have rates of 44% to 51%, but only about 2,000 calls in total. May has a third of all calls and the lowest rate (6.4%). This may also reflect which clients were called in each month.

Statistical insights:
- Most clients (about 80%) are between 25 and 50 years old, and about 61% are married.
- Call duration and number of contacts are strongly right-skewed: most calls are short and most clients are contacted only a few times.
- `duration` has the strongest correlation with the target (0.41), but it is known only after the call.
- The economic indicators `nr.employed`, `euribor3m` and `emp.var.rate` have correlations of about -0.3, so subscriptions were higher when interest rates and employment variation were low.

## Visualizations

The notebook contains these plots:
- Scatter matrix of age, duration and campaign, with the distribution of each feature on the diagonal
- Histogram of age, and histograms of all numerical features
- Box plots of age by marital status, by marital status and housing loan, and by education
- Bar charts of the subscription rate by job and by month
- Box plot of call duration for attracted and not attracted clients
- Chart of the correlation of numerical features with the target

## Recommendations

- Focus on students, retired and senior clients, and on clients from a successful previous campaign.
- Prefer cellular contact over telephone.
- Limit repeated attempts to about 3 or 4 per client.
- Test more calls outside May instead of putting so much of the effort there.
- Do not use `duration` to choose whom to call, since it is known only after the call. It can still be used as a quality signal for call agents.

## Limitations

- This is a descriptive analysis, so the results show relationships, not causes.
- The best segments (students, age 65+, and the high-rate months) are small and need to be confirmed on more data.
- `unknown` values were kept as a separate category and the duplicate rows were not removed.
- No predictive model has been built yet.

## Project Structure
```
EDA-Bank-Analysis/
│
├── bank-additional/
│   └── bank-additional-full.csv                # Main dataset
│
├── Proj1_EDA_Pandas_Banking (1).ipynb          # Main analysis notebook
└── README.md
```

## Tasks Completed

Task 1: Top 10 clients by number of contacts
- These clients were contacted from 37 to 56 times, and all of them refused.

Task 2: Education level analysis
- Pivot table of median age and number of contacts by education. The median number of contacts is 2 for every level, and the median age is lowest for university degree and high school (36) and highest for basic.4y (47).

Task 3: Age distribution by education
- Box plots show a similar age range for most levels, with basic.4y, unknown and illiterate older.

## Future Improvements

1. Predictive modeling: logistic regression or a tree-based model to predict subscription, without `duration`
2. Statistical testing of the differences between segments
3. An interactive dashboard (for example in Power BI or Tableau) to explore the segments
4. Cost-benefit analysis of different calling strategies
