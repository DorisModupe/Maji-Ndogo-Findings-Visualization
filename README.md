# Maji-Ndogo-Findings-Visualization

## Table of Contents
1. [Project Overview](#project-overview)
2. [Data Sources](#data-sources)
3. [Tools](#tools)
4. [Data Cleaning and Preparation](#data-cleaning-and-preparation)
5. [Exploratory Data Analysis](#exploratory-data-analysis)
6. [Data Analysis](#data-analysis)
7. [Findings](#findings)
8. [Recommendations](#recommendations)
9. [Limitations](#limitations)
10. [References](#references)

    
### Project Overview
---
Maji Ndogo used to be a flourishing country but now,they experience draught and lack of access to clean water. This project using Power BI helps to communicate issues and solutions to concerned stakeholders.
![MajiNdogoScrnsht](https://github.com/user-attachments/assets/d459f8ed-31aa-46b7-b0c6-02a07d54d05e)


### Data Sources
The primary dataset used for this analysis is the "Md_water_services_data.xlsx" file, containing detailed information about water related issues. The original dataset used is in the file upload section as 'Md_water_services_data (2).xlsx'

### Tools
- SQL - Data Cleaning
- Power BI -  Data Analysis and Reporting

### Data Cleaning and Preparation
In the initial phase preparing the data, I performed the following task
1. Data loading and inspection.
2. Handling null and missing values.
3. Data cleaning and formatting.

### Exploratory Data Analysis
EDA involved exploring the datasets to answer these key questions:
1. How far is the project?
2. How much money has been spent so far?
3. Where was the money spent?
4. What the money was spent on?
5. Will we have enough money to complete the project?
6. Where can we cut costs?
7. I want to see data at the national, provincial and town level

### Data Analysis
Interesting DAX used either to create new columns or new measures
  ```
  cumulative_budget = CALCULATE(
  SUM('project_progress'[Budgeted_improvements_costs]),
    FILTER( ALL('project_progress'), 'project_progress'[date_of_completion] <= MAX('project_progress'[date_of_completion]) &&
    NOT(ISBLANK('project_progress'[date_of_completion])) ) )
```

```
  Aggregated_improvements = IF( CONTAINSSTRING
  ( 'project_progress'[improvement], "taps" ), "Install public tap(s)*",
  IF( 'project_progress'[improvement] == "Diagnose local infrastructure", "Repair infrastructure", 'project_progress'[improvement] ) )
```

### Findings
The key questions served as guide to the results which influenced the visualizations provided. Some of the findings can be summarised as:
- About 25 000 projects location is still backlogged.
- Basic water is now accessible to 24 project location this shows there is still a long way to go.
- We are 2.7% over the estimated budget of 128.45 USD.
- Sokoto has the highest budget which can be attributed the installation of RO filters which is quite expensive and it is the only province that has a negative KPI

### Recommendations
Based on the analysis, the following recommendation was made: 
- Introduce a robust project management system to track progress and allocate resources efficiently. 

### Limitations
Due to insufficient data, the question 'Where can we cut costs?' was left unanswered. Once the project fully commence, we will have sufficient data to answser this question.

### References
- I used ChatGPT in reviewing some of the DAX expression and it provided insightful feedbacks.
- ALX learn
    - ExploreAI
