# Week 4 Case Study: Data Bank
<a href="https://8weeksqlchallenge.com/case-study-4/"> <img src= "https://8weeksqlchallenge.com/images/case-study-designs/4.png" width="500" height="520" alt="image" target="_blank"> </a>
## A. Customer node exploration
### 1. How many unique nodes are there on the Data Bank system?
````sql
SELECT
  COUNT(DISTINCT node_id) as total_nodes
FROM data_bank.customer_nodes
#### SQL Query
````
#### Answer
| total_nodes |
| ----------- |
| 5           |

### 2. What is the number of nodes per region?
````sql
SELECT
  region_id,
  region_name,
  COUNT(node_id) AS total_nodes
FROM data_bank.customer_nodes
JOIN data_bank.regions
USING(region_id)
GROUP BY region_id, region_name
ORDER BY region_id ASC
````
#### Answer
| region_id | region_name | total_nodes |
| --------- | ----------- | ----------- |
| 1         | Australia   | 770         |
| 2         | America     | 735         |
| 3         | Africa      | 714         |
| 4         | Asia        | 665         |
| 5         | Europe      | 616         |

### 3. How many customers are allocated to each region?
````sql
SELECT
  region_id,
  region_name,
  COUNT(DISTINCT customer_id) AS total_customers
FROM data_bank.customer_nodes
JOIN data_bank.regions
USING(region_id)
GROUP BY region_id, region_name
ORDER BY region_id ASC
````
#### Answer
| region_id | region_name | total_customers |
| --------- | ----------- | --------------- |
| 1         | Australia   | 110             |
| 2         | America     | 105             |
| 3         | Africa      | 102             |
| 4         | Asia        | 95              |
| 5         | Europe      | 88              |

### 4. 
````sql
SELECT
AVG(DATEDIFF(DAY, start_date, end_date)) as avg_number_of_days
FROM data_bank.customer_nodes
````
#### Answer
| avg_number_of_days |
| ------------------ |
| 14                 |

## B. Customer transactions
### 1. What is the unique count and total amount for each transaction type?
````sql
SELECT
txn_type,
COUNT(txn_type) AS total_transactions,
SUM(txn_amount) AS total_tansaction_amount
FROM data_bank.customer_transactions
GROUP BY txn_type
ORDER BY txn_type
````

#### Answer
| txn_type   | total_transactions | total_tansaction_amount |
| ---------- | ------------------ | ----------------------- |
| deposit    | 2671               | 1359168                 |
| purchase   | 1617               | 806537                  |
| withdrawal | 1580               | 793003                  |

### 2. What is the average total historical deposit counts and amounts for all customers?
````sql

````
#### Answer


### 3. For each month - how many Data Bank customers make more than 1 deposit and either 1 purchase or 1 withdrawal in a single month?
````sql

````
