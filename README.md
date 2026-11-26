# Financial Profile & Loan Default Analysis Dashboard
An end-to-end data analytics project using Excel, SQL Server, Power Query, Power BI Desktop, and Power BI Service to analyse loan distribution, applicant demographics, financial profiles, and loan default patterns.

Author: Prema Chowdhury | Data Analyst

# Disclaimer

This project is created for educational and portfolio purposes to demonstrate practical data analytics skills. The analysis is intended to explore applicant demographics, loan characteristics, and default patterns. The findings should not be considered financial advice or used as the sole basis for actual lending decisions.

# Project Overview

The Financial Profile & Loan Default Analysis Dashboard is an end-to-end business intelligence project developed using Power BI. The primary objective is to analyse loan-related data, understand applicant financial profiles, and identify patterns associated with loan distribution and default rates.

The project involves data extraction, cleaning, transformation, analysis, and visualization using multiple tools. Excel was used as the initial data source, while SQL Server was used for data cleaning and preparation. Further data transformation was performed using Power Query Editor before developing a two-page interactive dashboard in Power BI Desktop.

The completed report was published to Power BI Service, where a Dataflow was also created to support data preparation and management within the Power BI cloud environment.

# My Thinking Process

My approach was to understand the business requirements first and then organize the analysis around two major areas:

**Loan Default & Overview:** Analyse loan distribution across different purposes, employment categories, and age groups while examining default rates to identify potential patterns in loan repayment behaviour.

**Applicant Demographics & Financial Profile:** Understand the characteristics of loan applicants by analysing age groups, credit scores, education levels, marital status, mortgage status, and loan amounts.

I focused on presenting the information through clear visualizations and meaningful KPIs so that business users could understand the overall loan portfolio and make data-driven decisions.

# Business Problem

Financial institutions need to understand their loan portfolios, applicant profiles, and repayment behaviour to monitor lending performance and identify potential credit risks.

However, analysing large volumes of loan data can be challenging without proper data cleaning, transformation, and visualization.

This project addresses the following business needs:

- Understand the demographic and financial characteristics of loan applicants.

- Analyse loan amounts across different credit score categories.

- Identify loan distribution patterns across age groups and employment types.

- Examine loan default rates across employment categories.

- Understand the relationship between applicant characteristics and loan distribution.

- Present key financial and lending insights through an interactive dashboard.

# Business Questions Answered

- What is the median loan amount across different credit score categories?

- How does the average loan amount vary across age groups and marital statuses?

- What is the total loan amount for adult applicants across credit score categories?

- How do mortgage and dependent statuses relate to loan amounts for middle-aged applicants?

- How are loans distributed across different education levels?

- Which loan purposes account for the highest loan amounts?

- How does average income vary across employment types?

- Which employment category has the highest loan default rate?

- How does the average loan amount vary across different age groups?

- What patterns can be observed in applicant demographics and loan distribution?

# Key Findings

Based on the dashboard analysis:

**Credit Score:** The median loan amount is highest in the Low credit score category at approximately 128.4K and lowest in the High category at approximately 127.1K.

**Age Group:** Adults have the highest average loan amount at approximately 127.9K, while teenagers have the lowest at approximately 126.7K.

**Loan Purpose:** Home loans account for the highest loan amount at approximately 6,545M, followed by Business and Education loans.

**Employment Type:** Full-time employees have the highest average income at approximately 82,890, while unemployed applicants have the lowest at approximately 82,272.

**Default Rate:** Unemployed applicants have the highest default rate at approximately 3.89%, while full-time employees have the lowest at approximately 2.36%.


# Data Source

**Source:** Excel dataset containing applicant demographic, financial, and loan-related information.

**Format:** Microsoft Excel (.xlsx)

**Data Preparation:** Initial data cleaning and preparation were performed using SQL Server, followed by additional transformations in Power Query Editor.


# Tools and Tech Stack

| Tool | Purpose |
|---|---|
| Excel | Initial dataset and source data |
| SQL Server | Data cleaning and preparation |
| Power Query | Data transformation |
| Power BI Desktop | Data modelling and dashboard development |
| Power BI Service | Publishing and sharing reports |
| Dataflows | Cloud-based data preparation |


# Core Concepts Demonstrated

- Data Cleaning and Preprocessing

- SQL Queries and Data Manipulation

- Data Transformation using Power Query

- Data Modelling

- DAX Measures and Calculations

- Data Visualization

- KPI Analysis

- Demographic and Financial Analysis

- Loan Default Analysis

- Interactive Dashboard Development

- Power BI Service Publishing

- Power BI Dataflows

# Project Workflow

The project followed a structured end-to-end data analytics workflow:

## 1. Data Collection

Imported the loan and applicant dataset from an Excel file.

## 2. Data Cleaning using SQL Server

- Connected and worked with the dataset in SQL Server.

- Performed data cleaning and preparation.

- Addressed data quality issues and prepared the data for analysis.

## 3. Data Transformation using Power Query

- Imported the prepared data into Power BI.

- Used Power Query Editor for additional data transformations.

- Applied necessary data type changes, filtering, and preprocessing.

## 4. Data Modelling and DAX

- Prepared the data model for reporting.

- Created the required calculations and measures using DAX.

- Developed analytical metrics for loan amounts, average income, loan distribution, and default rates.

## 5. Dashboard Development

- Created a two-page interactive report in Power BI Desktop.

- Used appropriate visualizations to present demographic and financial insights.

## 6. Publishing to Power BI Service

- Published the completed Power BI report to Power BI Service.

- Created a Dataflow in the Power BI Service environment for cloud-based data preparation and management.

## 7. Reporting and Insights

- Presented the findings through interactive visualizations.

- Used the dashboard to explore loan distribution, applicant characteristics, and default patterns.

- Education: Bachelor's degree holders account for the highest number of loans, followed by High School, Master's, and PhD holders.


# Dashboard Structure

The Power BI report consists of two analytical pages.

## Page 1: Applicant Demographics & Financial Profile

This page focuses on understanding applicant characteristics and their financial profiles.

Visualizations included:

- Median Loan Amount by Credit Score Category.

- Average Loan Amount by Age Group and Marital Status.

- Total Loans (Adult) by Credit Score Bins.

- Loan Distribution for Middle-Aged Adults by Mortgage and Dependents.

- Number of Loans by Education Type.


## Page 2: Loan Default & Overview

This page provides an overview of loan distribution, employment characteristics, and default patterns.

Visualizations included:

- Loan Amount by Purpose.

- Average Income by Employment Type.

- Default Rate (%) by Employment Type.

- Average Loan Amount by Age Group.


# Features / Highlights

- Two-page interactive Power BI dashboard.

- Comprehensive applicant demographic analysis.

- Loan amount and credit score analysis.

- Employment and income comparison.

- Loan default rate analysis across employment categories.

- Multiple chart types, including area charts, line charts, bar charts, doughnut charts, and combination visualizations.

- End-to-end data cleaning and transformation workflow.

- Cloud publishing through Power BI Service.

- Data preparation using Power BI Dataflows.


# Sample Measures

The following are examples of DAX measures relevant to the analysis:

## Average Income By Employment Type
```Average Income By Employment Type = CALCULATE(AVERAGE(Loan_default[Income]), ALLEXCEPT(Loan_default, Loan_default[EmploymentType]))```

## Default Rate by Employment type
```Default Rate by Employment type = 
VAR totalrecords = COUNTROWS(ALL('Loan_default'))

VAR DefaultCases =
    COUNTROWS(
        FILTER(
            'Loan_default',
            'Loan_default'[Default] = 1
        )
    )

RETURN
CALCULATE(
    DIVIDE(DefaultCases, totalrecords),
    ALLEXCEPT(
        'Loan_default',
        'Loan_default'[EmploymentType]
    )
) * 100
```
## Loan Amount By Purpose
```Loan Amount By Purpose = SUMX(FILTER(Loan_default, NOT(ISBLANK(Loan_default[LoanAmount]))), Loan_default[LoanAmount])```

## Average Loan Amt (High Credit)
```Average Loan Amt (High Credit) = AVERAGEX(FILTER(Loan_default, Loan_default[Credit Score Bins] = "High"), Loan_default[LoanAmount])```

## Total Loan (Credit Bins)
```Total Loan (Credit Bins) = CALCULATE(SUM(Loan_default[LoanAmount]), Loan_default[Age Group] = "Adults", ALLEXCEPT(Loan_default, Loan_default[Age], Loan_default[Age Group], Loan_default[CreditScore], Loan_default[Credit Score Bins]))```

## Total Loans (Middle Age Adults)
```Total Loans (Middle Age Adults) = SUMX(FILTER(Loan_default, Loan_default[Age Group] = "Middle Aged Adults"), Loan_default[LoanAmount])```


# Screenshots / Demos

## Page 1: Loan Default & Overview



## Page 2: Applicant Demographics & Financial Profile


# How to Reproduce This Project

Follow these steps to explore and reproduce the project:

- Clone or download this GitHub repository.

- Download the Excel dataset provided in the repository.

- Import the dataset into SQL Server.

- Perform the required data cleaning and preparation using SQL queries.

- Open Power BI Desktop and connect to the prepared dataset.

- Perform additional transformations using Power Query Editor.

- Create the data model and required DAX measures.

- Develop the two-page dashboard using Power BI Desktop.

- Publish the report to Power BI Service.

- Configure the required Dataflow and data preparation process in Power BI Service.


# Requirements:

- Microsoft Excel

- SQL Server

- Power BI Desktop

- Power BI Service account

# Connect

I am continuously developing my skills in Data Analytics, Business Intelligence, and Data Visualization.

Feel free to explore this project, share your feedback, or connect with me.

**LinkedIn:** www.linkedin.com/in/prema-chowdhury-aab8483a6

**GitHub:** [Add your GitHub Profile URL]
