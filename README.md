# Parliamentary Participation and Performance Indicators
## 17th Lok Sabha (2019–2024)

An exploratory data analysis of parliamentary participation indicators among members of the 17th Lok Sabha (2019–2024).

## Project Overview

This project examines participation patterns among representatives of the 17th Lok Sabha using indicators such as:

- Attendance
- Parliamentary questions
- Debate participation
- Private Member Bills
- Demographic characteristics
- Party and state representation

The project combines exploratory data analysis with unsupervised machine learning to identify broad participation profiles among representatives.

## Objectives

The analysis aims to:

1. Examine the demographic composition of the 17th Lok Sabha.
2. Analyze distributions of attendance and parliamentary participation.
3. Compare participation patterns across parties and states.
4. Examine relationships between different participation indicators.
5. Identify exploratory participation profiles using K-Means clustering.
6. Visualize the clustering structure using Principal Component Analysis (PCA).
7. Evaluate the clustering solutions using silhouette analysis.

## Dataset

The dataset used in this project is the `india-representatives-activity` dataset by Vonter, which compiles parliamentary activity data sourced from PRS India.

The raw dataset is stored in:

`data/raw/17th.csv`

The analysis uses parliamentary participation indicators reported for the 17th Lok Sabha, including attendance, debates, questions, and Private Member Bills.

### Data Sources

- Vonter — India Representatives Activity dataset
- PRS India — MP Track / 17th Lok Sabha
- Digital Sansad — Parliament of India

The Vonter dataset is used as the structured source for the initial analysis, while PRS India and Digital Sansad provide the underlying parliamentary context and authoritative reference sources.
## Methodology

### Data Preparation

The `01_Data_Preparation.ipynb` notebook covers:

- Dataset loading
- Data structure inspection
- Missing-value analysis
- Duplicate checks
- Data-type conversion
- Date processing
- Preparation of attendance and participation variables
- Final data-quality checks

### Exploratory Data Analysis

The `02_EDA.ipynb` notebook examines:

- Age distribution
- Gender representation
- Attendance
- Parliamentary questions
- Debate participation
- Private Member Bills
- Relationships between participation indicators
- Participation differences across ministers, parties and states
- Correlations between participation indicators

### Unsupervised Learning

K-Means clustering was applied to:

- Attendance
- Questions
- Debates
- Private Member Bills

The features were standardized before clustering.

PCA was then used to visualize the resulting cluster structure in two dimensions.

Silhouette analysis was performed for K values from 2 to 6.

## Key Findings

### Participation

Attendance and participation indicators showed different distributions. Questions, debates and Private Member Bills were strongly right-skewed, indicating that a relatively small number of representatives accounted for substantially higher levels of activity in these measures.

### Relationships

Attendance showed positive but relatively weak linear associations with:

- Questions: `r ≈ 0.15`
- Debates: `r ≈ 0.22`
- Private Member Bills: `r ≈ 0.23`

These relationships indicate that attendance alone does not strongly explain differences in other participation indicators.

### K-Means Clustering

An exploratory four-cluster solution revealed several participation profiles, including:

- A large group with relatively high attendance and moderate participation.
- A smaller group with higher levels of questions, debates and Private Member Bills.
- A group with comparatively lower attendance and participation.
- A very small group characterized by exceptionally high debate participation.

However, silhouette analysis showed that the two-cluster solution achieved the highest score among the tested configurations:

| Number of clusters | Silhouette score |
|---|---:|
| 2 | 0.517 |
| 3 | 0.339 |
| 4 | 0.350 |
| 5 | 0.337 |
| 6 | 0.304 |

This suggests that the data has a stronger broad two-group structure than a sharply separated four-group structure.

The four-cluster solution is therefore treated as an exploratory segmentation rather than an objective ranking of representatives.

## Technologies

- Python
- NumPy
- Pandas
- Matplotlib
- Scikit-learn
- Jupyter Notebook

## Project Structure

```text
17th_Lok_Sabha_Analysis/
│
├── data/
│   └── raw/
│       └── 17th.csv
│
├── notebooks/
│   ├── 01_Data_Preparation.ipynb
│   └── 02_EDA.ipynb
│
├── README.md
└── .gitignore