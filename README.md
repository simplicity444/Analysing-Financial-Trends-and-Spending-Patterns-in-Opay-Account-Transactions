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

- Data Loading and Inspection: Loaded the Opay statement of account PDF file into Power BI by selecting Get Data and connecting to the PDF file. Selected all tables and initiated Transform Data to activate the Power Query Editor.

- Handling Account Details and Table Structure: Deleted the first three tables containing account owner details. Reviewed each table to ensure consistent column structure and data types.

- Data Cleaning and Formatting:
  
- Appending Tables: Combined all tables into a single comprehensive table.

- Creating Debit and Credit Columns: Used conditional formulas to separate amounts into Debit and Credit columns: Debit: = if [Amount] < 0 then [Amount] else null
Credit: = if [Amount] > 0 then [Amount] else null


- Replaced null values in the new columns with 0.

- Extracting Date Information: Extracted Month and Day of the Week from the transaction date to facilitate analysis.

- Cleaning Description Column: Standardized transaction descriptions by categorizing them. Used a formula to classify descriptions into categories like "Transfer," "Mobile Data," "Electricity," etc., based on specific keywords.


- Finalizing and Saving Data: Disabled all tables from loading except the appended table, applied changes, and saved the cleaned dataset.

### Exploratory Data Analysis (EDA)

- To understand the overall transactions made both credit and debit.
- To determine the total and average credit transactions 
- To determine the total and average debit transactions 
- To ascertain the highest and lowest monthly transactions.
- To ascertain the highest and lowest daily transactions 
- To identify the transaction category with the highest bonus 
- To ascertain the most preferred transaction 

### Data Analysis 

1. Understand the Overall Transactions (Credit and Debit)
Measure: Create a measure to sum both credit and debit transactions to get the overall transaction value.
```
Total Transactions =
SUM('Opay Satement'[Credit]) +
SUM('YourTable'[Debit])
```

2. Determine the Total and Average Credit TransactionsMeasures:
Total Credit: Sum of all credit transactions.

Total Credit = 
```
SUM('Opay Statement'[Credit])
```
Average Credit: Average of credit transactions.

Average Credit =
```
AVERAGE('Opay Statement'[Credit])
```

3. Determine the Total and Average Debit Transactions
Measures:
Total Debit =
```
SUM('Opay Statement'[Debit])
```
Average Debit: Average of debit transactions.
Average Debit = 
```
AVERAGE('Opay Statement'[Debit])
```

4. Ascertain the Highest and Lowest Monthly Transactions

Measure:
Used Month from date column to create monthly aggregated totals.
Highest Monthly  Transaction:
Highest Monthly Transaction = 
```
MAXX(SUMMARIZE('YourTable', 'Opay Statement'[Month], "MonthlyTotal",
SUM('Opay Statement'[Credit] + 'Opay Statement'[Debit])), [MonthlyTotal])
```

Lowest Monthly Transaction:
Lowest Monthly Transaction = 
```
MINX(SUMMARIZE('Opay Statement', 'Opay Statement'[Month], "MonthlyTotal", SUM('Opay Statement'[Credit] + 'Opay Statement'[Debit])), [MonthlyTotal])
```

5. Ascertain the Highest and Lowest Daily Transactions

Measure:
Used Date from table for daily aggregated totals.

Highest Daily Transaction:
```
Highest Daily Transaction = 
MAXX(SUMMARIZE('Opay Statement', 'Opay Statement'[Date], "DailyTotal", SUM('Opay Statement'[Credit] + 'Opay Statement'[Debit])), [DailyTotal])
```
Lowest Daily Transaction:
```
Lowest Daily Transaction = MINX(SUMMARIZE('Opay Statement', 'Opay Statement'[Date], "DailyTotal", SUM('Opay Statement'[Credit] + 'Opay Statement'[Debit])), [DailyTotal])
```

6. Identify the Transaction Category with the Highest Bonus

Measure:
```
Category with Highest Bonus = 
CALCULATE(MAX('YourTable'[Bonus]), ALLEXCEPT('YourTable', 'YourTable'[Transaction Category]))
```

7. Ascertain the Most Preferred Transaction

Measure:
```
Most Preferred Transaction = 
CALCULATE(MAXX(SUMMARIZE('Opay Statement', 'Opay Statement'[Transaction Category], "Count", COUNT('Opay Statement'[Transaction ID])), [Count]))
```
