# Analysing Financial Trends and Spending Patterns in Opay Account Transactions

## Project Title 

Analysing Financial Trends and Spending Patterns in Opay Account Transactions Between July 2023 and July 2024: A Data-Driven Approach to Personal Finance Optimization

## Project Overview 

In today’s digital economy, financial management is crucial for maintaining stability and achieving long-term goals. Through detailed visualization and analysis, the project aims to uncover spending patterns, income trends and the impact of high-value transactions. By leveraging these insights, the study offers actionable strategies for optimizing personal finance, ensuring better budgeting, and enhancing overall financial health.

## Data sources

This project analyses a comprehensive dataset derived from Opay account statements spanning from July 2023- July 2024. The dataset includes over 1,600 transactions categorized type such as transfers, airtime purchases, data and utility payments, date of transactions, transaction ID, credit and debit transactions.

### Tools Used
- Power BI 
   1. For Data Cleaning 
   2. For Data Analysis 
   3. For Data Visualization 

### Data Cleaning and Preparation

In the initial phase of data cleaning and preparations, I performed the following actions:

### Data Loading and Inspection: Loaded the Opay statement of account PDF file into Power BI by selecting Get Data and connecting to the PDF file. Selected all tables and initiated Transform Data to activate the Power Query Editor.

- Handling Account Details and Table Structure: Deleted the first three tables containing account owner details. Reviewed each table to ensure consistent column structure and data types.

Data Cleaning and Formatting:

Appending Tables: Combined all tables into a single comprehensive table.

Creating Debit and Credit Columns: Used conditional formulas to separate amounts into Debit and Credit columns:

Debit: = if [Amount] < 0 then [Amount] else null

Credit: = if [Amount] > 0 then [Amount] else null


Replaced null values in the new columns with 0.

Extracting Date Information: Extracted Month and Day of the Week from the transaction date to facilitate analysis.

Cleaning Description Column: Standardized transaction descriptions by categorizing them. Used a formula to classify descriptions into categories like "Transfer," "Mobile Data," "Electricity," etc., based on specific keywords.


Finalizing and Saving Data: Disabled all tables from loading except the appended table, applied changes, and saved the cleaned dataset.
