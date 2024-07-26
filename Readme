## README.md

# Bank Loan Data Analysis

This project involves creating and analyzing a database for bank loan data. The data includes various attributes related to loan applications, such as borrower information, loan details, and loan status. The project aims to provide insights into the bank's lending activities and assess the quality of loans issued.

## Table of Contents
- [Project Overview](#project-overview)
- [Database Schema](#database-schema)
- [Data Loading](#data-loading)
- [Queries](#queries)
  - [Overview Queries](#overview-queries)
  - [Monthly Comparison Queries](#monthly-comparison-queries)
  - [Loan Quality Analysis](#loan-quality-analysis)
  - [Breakdown by Attributes](#breakdown-by-attributes)

## Project Overview
The purpose of this project is to analyze the bank loan data to gain insights into loan applications, funded amounts, interest rates, debt-to-income ratios (DTI), and the quality of loans issued. The analysis includes an overview of total loans, monthly comparisons, and breakdowns by various attributes like state, term, employee length, purpose, and home ownership.

## Database Schema
The database `bank` contains a single table `bank_loan_data` with the following schema:

| Column                  | Data Type |
|-------------------------|-----------|
| `id`                    | INT       |
| `address_state`         | TEXT      |
| `application_type`      | TEXT      |
| `emp_length`            | TEXT      |
| `emp_title`             | TEXT      |
| `grade`                 | TEXT      |
| `home_ownership`        | TEXT      |
| `issue_date`            | TEXT      |
| `last_credit_pull_date` | TEXT      |
| `last_payment_date`     | TEXT      |
| `loan_status`           | TEXT      |
| `next_payment_date`     | TEXT      |
| `member_id`             | INT       |
| `purpose`               | TEXT      |
| `sub_grade`             | TEXT      |
| `term`                  | TEXT      |
| `verification_status`   | TEXT      |
| `annual_income`         | DOUBLE    |
| `dti`                   | DOUBLE    |
| `installment`           | DOUBLE    |
| `int_rate`              | DOUBLE    |
| `loan_amount`           | INT       |
| `total_acc`             | INT       |
| `total_payment`         | INT       |

## Data Loading
The data is loaded into the `bank_loan_data` table from a CSV file named `financial_loan_no_duplicates.csv`. The data is loaded using the following command:

```sql
LOAD DATA INFILE '/Users/rashmithayellareddy/Desktop/financial_loan_no_duplicates.csv'
INTO TABLE bank_loan_data
FIELDS TERMINATED BY ','
ENCLOSED BY '"'
LINES TERMINATED BY '\n'
IGNORE 1 ROWS;
```

## Queries
### Overview Queries
1. **Select All Data**: Retrieve all records from the `bank_loan_data` table.
   ```sql
   SELECT * FROM bank_loan_data;
   ```

2. **Total Loan Applications**: Count the total number of loan applications.
   ```sql
   SELECT COUNT(id) AS Total_Applications FROM bank_loan_data;
   ```

3. **Total Funded Amount**: Calculate the total amount funded by the bank.
   ```sql
   SELECT SUM(loan_amount) AS Total_Funded_Amount FROM bank_loan_data;
   ```

4. **Total Amount Received**: Calculate the total amount received by the bank.
   ```sql
   SELECT SUM(total_payment) AS Total_Amount_Collected FROM bank_loan_data;
   ```

5. **Average Interest Rate**: Calculate the average interest rate.
   ```sql
   SELECT AVG(int_rate)*100 AS Avg_Int_Rate FROM bank_loan_data;
   ```

6. **Average DTI**: Calculate the average debt-to-income ratio.
   ```sql
   SELECT AVG(dti)*100 AS Avg_DTI FROM bank_loan_data;
   ```

### Monthly Comparison Queries
1. **MTD (Month-To-Date) Loan Applications**: Count the loan applications for the current month (example: December).
   ```sql
   SELECT COUNT(id) AS MTD_Total_Applications FROM bank_loan_data
   WHERE MONTH(issue_date) = 12;
   ```

2. **PMTD (Previous Month-To-Date) Loan Applications**: Count the loan applications for the previous month (example: November).
   ```sql
   SELECT COUNT(id) AS PMTD_Total_Applications FROM bank_loan_data
   WHERE MONTH(issue_date) = 11;
   ```

3. **MTD Total Funded Amount**: Calculate the total funded amount for the current month.
   ```sql
   SELECT SUM(loan_amount) AS MTD_Total_Funded_Amount FROM bank_loan_data
   WHERE MONTH(issue_date) = 12;
   ```

4. **PMTD Total Funded Amount**: Calculate the total funded amount for the previous month.
   ```sql
   SELECT SUM(loan_amount) AS PMTD_Total_Funded_Amount FROM bank_loan_data
   WHERE MONTH(issue_date) = 11;
   ```

5. **MTD Total Amount Received**: Calculate the total amount received for the current month.
   ```sql
   SELECT SUM(total_payment) AS MTD_Total_Amount_Collected FROM bank_loan_data
   WHERE MONTH(issue_date) = 12;
   ```

6. **PMTD Total Amount Received**: Calculate the total amount received for the previous month.
   ```sql
   SELECT SUM(total_payment) AS PMTD_Total_Amount_Collected FROM bank_loan_data
   WHERE MONTH(issue_date) = 11;
   ```

7. **MTD Average Interest Rate**: Calculate the average interest rate for the current month.
   ```sql
   SELECT AVG(int_rate)*100 AS MTD_Avg_Int_Rate FROM bank_loan_data
   WHERE MONTH(issue_date) = 12;
   ```

8. **PMTD Average Interest Rate**: Calculate the average interest rate for the previous month.
   ```sql
   SELECT AVG(int_rate)*100 AS PMTD_Avg_Int_Rate FROM bank_loan_data
   WHERE MONTH(issue_date) = 11;
   ```

9. **MTD Average DTI**: Calculate the average DTI for the current month.
   ```sql
   SELECT AVG(dti)*100 AS MTD_Avg_DTI FROM bank_loan_data
   WHERE MONTH(issue_date) = 12;
   ```

10. **PMTD Average DTI**: Calculate the average DTI for the previous month.
    ```sql
    SELECT AVG(dti)*100 AS PMTD_Avg_DTI FROM bank_loan_data
    WHERE MONTH(issue_date) = 11;
    ```

### Loan Quality Analysis
1. **Good Loan Percentage**: Calculate the percentage of good loans (Fully Paid or Current).
   ```sql
   SELECT
       (COUNT(CASE WHEN loan_status = 'Fully Paid' OR loan_status = 'Current' THEN id END) * 100.0) / 
       COUNT(id) AS Good_Loan_Percentage
   FROM bank_loan_data;
   ```

2. **Good Loan Applications**: Count the number of good loan applications.
   ```sql
   SELECT COUNT(id) AS Good_Loan_Applications FROM bank_loan_data
   WHERE loan_status = 'Fully Paid' OR loan_status = 'Current';
   ```

3. **Good Loan Funded Amount**: Calculate the funded amount for good loans.
   ```sql
   SELECT SUM(loan_amount) AS Good_Loan_Funded_amount FROM bank_loan_data
   WHERE loan_status = 'Fully Paid' OR loan_status = 'Current';
   ```

4. **Good Loan Amount Received**: Calculate the amount received for good loans.
   ```sql
   SELECT SUM(total_payment) AS Good_Loan_amount_received FROM bank_loan_data
   WHERE loan_status = 'Fully Paid' OR loan_status = 'Current';
   ```

5. **Bad Loan Percentage**: Calculate the percentage of bad loans (Charged Off).
   ```sql
   SELECT
       (COUNT(CASE WHEN loan_status = 'Charged Off' THEN id END) * 100.0) / 
       COUNT(id) AS Bad_Loan_Percentage
   FROM bank_loan_data;
   ```

6. **Bad Loan Applications**: Count the number of bad loan applications.
   ```sql
   SELECT COUNT(id) AS Bad_Loan_Applications FROM bank_loan_data
   WHERE loan_status = 'Charged Off';
   ```

7. **Bad Loan Funded Amount**: Calculate the funded amount for bad loans.
   ```sql
   SELECT SUM(loan_amount) AS Bad_Loan_Funded_amount FROM bank_loan_data
   WHERE loan_status = 'Charged Off';
   ```

8. **Bad Loan Amount Received**: Calculate the amount received for bad loans.
   ```sql
   SELECT SUM(total_payment) AS Bad_Loan_amount_received FROM bank_loan_data
   WHERE loan_status = 'Charged Off';
   ```

9. **Loan Status Breakdown**: Group loans by status and calculate counts, total amounts received, total funded amounts, interest rates, and DTI.
   ```sql
   SELECT
       loan_status,
       COUNT(id) AS LoanCount,
       SUM(total_payment) AS Total_Amount_Received,
       SUM(loan_amount) AS Total_Funded_Amount,
       AVG(int_rate * 100) AS Interest_Rate,
       AVG(dti * 100) AS DTI
   FROM
       bank_loan_data
   GROUP BY
