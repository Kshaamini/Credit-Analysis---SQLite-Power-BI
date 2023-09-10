# Credit Analysis - SQLite & Power BI
Capstone project under NUS Analytics Program
| Summary | 
| ----------- | 
| The is a project I did as part of the NUS Advanced Computing for Executives, School of Computing's Analytics: From Data to Insights programme I had undertaken. The scenario is to assist a credit analyst who wants to gather, organise and analyse data on credit card transactions and customers in order to identify fraudulent information.|
|The dataset is an excel workbook that contains data on credit card transactions and customers in the year 2016|

## SQLite
- **The total number of customers with multiple cards**
SELECT
  COUNT (DISTINCT Cust_ID) as 'No. of Cust with multiple cards'
FROM
  (SELECT DISTINCT Cust_ID, count (DISTINCT Card_Number )as cards from Cardbase
GROUP BY
Cust_ID
HAVING
 count(distinct card_number)>1)

- **The average sales for each customer segment**
SELECT
 Cu.Customer_Segment as [Customer Segment],
 avg (T.Transaction_Value) as [Average Sales]
FROM
 Cardbase as 'Ca'
Left JOIN
 CustomerBase as 'Cu'
ON
 Ca.Cust_ID = Cu.Cust_ID
Left JOIN
 TransactionBase as 'T'
ON
 T.Credit_Card_ID = Ca.Card_Number
GROUP BY
 Customer_Segment;

- **Find the total number of fraudulent transactions with their respective amount**
SELECT
 T.Credit_Card_ID as [No.of fraudulent transactions],
 T.Transaction_Value as [Transaction Amount]
FROM
 Fraud as 'F'
Left JOIN
 TransactionBase as 'T'
ON
 F.Transaction_ID = T.Transaction_ID

## Power BI Dashboard

<img width="595" alt="image" src="https://github.com/Kshaamini/DataAnalysis-PowerBI/assets/139740694/5ba6899d-2a4b-4ffa-a627-86043cf9decf">

| Analysis | 
| ----------- | 
| |
||
