# Week 2 Case Study: Foodie_Fi
<a href="https://8weeksqlchallenge.com/case-study-3/"> <img src= "https://8weeksqlchallenge.com/images/case-study-designs/3.png" width="500" height="520" alt="image" target="_blank"> </a>
## A. Customer Journey
### Based off the 8 sample customers provided in the sample from the subscriptions table, write a brief description about each customer’s onboarding journey.

#### SQL Query
````sql
SELECT
  s.customer_id,
  p.plan_name,
  s.start_date
FROM foodie_fi.subscriptions s
JOIN foodie_fi.plans p
USING (plan_id)
WHERE s.customer_id IN (1,2,11,13,15,16,18,19)
ORDER BY s.customer_id, s.start_date ASC;
````
#### Answer
| customer_id | plan_name     | start_date               |
| ----------- | ------------- | ------------------------ |
| 1           | trial         | 2020-08-01T00:00:00.000Z |
| 1           | basic monthly | 2020-08-08T00:00:00.000Z |
| 2           | trial         | 2020-09-20T00:00:00.000Z |
| 2           | pro annual    | 2020-09-27T00:00:00.000Z |
| 11          | trial         | 2020-11-19T00:00:00.000Z |
| 11          | churn         | 2020-11-26T00:00:00.000Z |
| 13          | trial         | 2020-12-15T00:00:00.000Z |
| 13          | basic monthly | 2020-12-22T00:00:00.000Z |
| 13          | pro monthly   | 2021-03-29T00:00:00.000Z |
| 15          | trial         | 2020-03-17T00:00:00.000Z |
| 15          | pro monthly   | 2020-03-24T00:00:00.000Z |
| 15          | churn         | 2020-04-29T00:00:00.000Z |
| 16          | trial         | 2020-05-31T00:00:00.000Z |
| 16          | basic monthly | 2020-06-07T00:00:00.000Z |
| 16          | pro annual    | 2020-10-21T00:00:00.000Z |
| 18          | trial         | 2020-07-06T00:00:00.000Z |
| 18          | pro monthly   | 2020-07-13T00:00:00.000Z |
| 19          | trial         | 2020-06-22T00:00:00.000Z |
| 19          | pro monthly   | 2020-06-29T00:00:00.000Z |
| 19          | pro annual    | 2020-08-29T00:00:00.000Z |

#### Customer 1
| customer_id | plan_name     | start_date               |
| ----------- | ------------- | ------------------------ |
| 1           | trial         | 2020-08-01T00:00:00.000Z |
| 1           | basic monthly | 2020-08-08T00:00:00.000Z |

<p> Customer 1 started their free trial on the 1st of August, 2020. They later upgraded to a basic monthly plan after the 7-day trial ended.</p>

#### Customer 2
| customer_id | plan_name     | start_date               |
| ----------- | ------------- | ------------------------ |
| 2           | trial         | 2020-09-20T00:00:00.000Z |
| 2           | pro annual    | 2020-09-27T00:00:00.000Z |

<p> Customer 2 started their free trial on the 20th of September, 2020. They later upgraded to a pro annual plan after the 7-day trial ended.</p>

#### Customer 11
| customer_id | plan_name     | start_date               |
| ----------- | ------------- | ------------------------ |
| 11          | trial         | 2020-11-19T00:00:00.000Z |
| 11          | churn         | 2020-11-26T00:00:00.000Z |

<p> Customer 11 started their free trial on the 19th of November, 2020. They churned after the 7-day trial ended.</p>

#### Customer 13
| customer_id | plan_name     | start_date               |
| ----------- | ------------- | ------------------------ |
| 13          | trial         | 2020-12-15T00:00:00.000Z |
| 13          | basic monthly | 2020-12-22T00:00:00.000Z |
| 13          | pro monthly   | 2021-03-29T00:00:00.000Z |

<p> Customer 13 started their free trial on the 15th of December, 2020. They signed up for a basic monthly plan after the 7-day trial ended and later to a pro monthly plan 3 months later.</p>

#### Customer 15
| customer_id | plan_name     | start_date               |
| ----------- | ------------- | ------------------------ |
| 15          | trial         | 2020-03-17T00:00:00.000Z |
| 15          | pro monthly   | 2020-03-24T00:00:00.000Z |
| 15          | churn         | 2020-04-29T00:00:00.000Z |

<p> Customer 15 started their free trial on the 17th of March, 2020. They signed up for a pro monthly plan after the 7-day trial ended and churned around a month later.</p>

#### Customer 16
| customer_id | plan_name     | start_date               |
| ----------- | ------------- | ------------------------ |
| 16          | trial         | 2020-05-31T00:00:00.000Z |
| 16          | basic monthly | 2020-06-07T00:00:00.000Z |
| 16          | pro annual    | 2020-10-21T00:00:00.000Z |

<p> Customer 16 started their free trial on the 31st of May, 2020. They signed up for a pro monthly plan after the 7-day trial ended and then to a pro annual plan around 4 months later.</p>

#### Customer 18
| customer_id | plan_name     | start_date               |
| ----------- | ------------- | ------------------------ |
| 18          | trial         | 2020-07-06T00:00:00.000Z |
| 18          | pro monthly   | 2020-07-13T00:00:00.000Z |

<p> Customer 18 started their free trial on the 6th of July, 2020. They signed up for a pro monthly plan after the 7-day trial ended.</p>

#### Customer 19
| customer_id | plan_name     | start_date               |
| ----------- | ------------- | ------------------------ |
| 19          | trial         | 2020-06-22T00:00:00.000Z |
| 19          | pro monthly   | 2020-06-29T00:00:00.000Z |
| 19          | pro annual    | 2020-08-29T00:00:00.000Z |

<p> Customer 19 started their free trial on the 22st of June, 2020. They signed up for a pro monthly plan after the 7-day trial ended and then to a pro annual plan 2 months later.</p>


## B. Data Analyst Questions
### 1. How many customers has Foodie-Fi ever had?
#### SQL Query
````sql
SELECT 
  COUNT(DISTINCT customer_id) AS total_unique_customers
FROM foodie_fi.subscriptions s
````
#### Answer
| total_unique_customers |
| ---------------------- |
| 1000                   |
### 2. What is the monthly distribution of trial plan start_date values for our dataset - use the start of the month as the group by value
#### SQL Query
````sql
SELECT
  EXTRACT(MONTH FROM start_date) AS month,
  COUNT(customer_id) AS trial_count
FROM foodie_fi.subscriptions s
WHERE plan_id = 0
GROUP BY month
````
#### Answer
| month | trial_count |
| ----- | ----------- |
| 1     | 88          |
| 2     | 68          |
| 3     | 94          |
| 4     | 81          |
| 5     | 88          |
| 6     | 79          |
| 7     | 89          |
| 8     | 88          |
| 9     | 87          |
| 10    | 79          |
| 11    | 75          |
| 12    | 84          |

### 3. What plan start_date values occur after the year 2020 for our dataset? Show the breakdown by count of events for each plan_name
#### SQL Query
````sql
SELECT
  s.plan_id,
  p.plan_name,
  count(s.plan_id)
FROM foodie_fi.subscriptions s
JOIN foodie_fi.plans p
USING(plan_id)
WHERE start_date >= '01/01/2021'
GROUP BY s.plan_id, p.plan_name
ORDER BY s.plan_id ASC
````
#### Answer
| plan_id | plan_name     | count |
| ------- | ------------- | ----- |
| 1       | basic monthly | 8     |
| 2       | pro monthly   | 60    |
| 3       | pro annual    | 63    |
| 4       | churn         | 71    |

### 4. What is the customer count and percentage of customers who have churned rounded to 1 decimal place?
````sql
SELECT
  COUNT(DISTINCT customer_id) AS total_customers,
  SUM(CASE WHEN plan_id = 4 THEN 1 ELSE NULL END) AS total_churned,
  ROUND(CAST(SUM(CASE WHEN plan_id = 4 THEN 1 ELSE NULL END) AS DECIMAL(5,1))/CAST(COUNT(DISTINCT customer_id) AS DECIMAL(5,1)) * 100,1) AS churn_rate
FROM foodie_fi.subscriptions
````
#### Answer
| total_customers | total_churned | churn_rate |
| --------------- | ------------- | ---------- |
| 1000            | 307           | 30.7       |

### 5. How many customers have churned straight after their initial free trial - what percentage is this rounded to the nearest whole number?
````sql
WITH ranking AS (
  SELECT
  *,
  RANK() OVER(PARTITION BY customer_id ORDER BY start_date)
  FROM foodie_fi.subscriptions
  )

SELECT
COUNT(CASE WHEN plan_id = 4 and rank = 2 THEN 1 END) as churn_count,
  ROUND(
  COUNT(CASE WHEN plan_id = 4 AND rank = 2 THEN 1 END)::numeric / COUNT(DISTINCT customer_id) * 100
  ) AS churn_rate
FROM ranking
````
#### Answer
| churn_count | churn_rate |
| ----------- | ---------- |
| 92          | 0          |

### 6. What is the number and percentage of customer plans after their initial free trial?
````sql
WITH rank AS
(
  SELECT
  *,
  RANK() OVER(PARTITION BY customer_id ORDER BY start_date)
  FROM foodie_fi.subscriptions
)
  
SELECT
  plan_id,
  plan_name,
  COUNT(plan_id) as conversions,
  ROUND(COUNT(plan_id)::NUMERIC / (SELECT COUNT(plan_id) from rank where rank = 2) * 100, 1) as conversion_percentage
FROM rank
JOIN foodie_fi.plans
USING(plan_id)
WHERE rank = 2
GROUP BY plan_id, plan_name
ORDER BY plan_id
````

#### Answer
| plan_id | plan_name     | conversions | conversion_percentage |
| ------- | ------------- | ----------- | --------------------- |
| 1       | basic monthly | 546         | 54.6                  |
| 2       | pro monthly   | 325         | 32.5                  |
| 3       | pro annual    | 37          | 3.7                   |
| 4       | churn         | 92          | 9.2                   |

### 7. What is the customer count and percentage breakdown of all 5 plan_name values at 2020-12-31?
### 8. How many customers have upgraded to an annual plan in 2020?
### 9. How many days on average does it take for a customer to an annual plan from the day they join Foodie-Fi?
### 10. Can you further breakdown this average value into 30 day periods (i.e. 0-30 days, 31-60 days etc)
### 11. How many customers downgraded from a pro monthly to a basic monthly plan in 2020?
