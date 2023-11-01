# Week 2 Case Study: Pizza_Runner
<a href="https://8weeksqlchallenge.com/case-study-2/"> <img src= "https://8weeksqlchallenge.com/images/case-study-designs/2.png" width="500" height="520" alt="image" target="_blank"> </a>
## Pizza Metrics
### Question 1: How many pizzas were ordered?

#### SQL Query
````sql
SELECT
    COUNT(order_id) AS total_pizza_orders
FROM pizza_runner.customer_orders
````
#### Answer
| total_pizza_orders |
|--------------------|
| 14                 |

### Question 2: How many unique customer orders were made?
#### SQL Query
````sql
SELECT
    COUNT(DISTINCT order_id) AS unique_orders
FROM pizza_runner.customer_orders
````
#### Answer
| unique_orders      |
|--------------------|
| 10                 |
### Question 3: How many successful orders were delivered by each runner?
#### SQL Query
````sql
SELECT 
    runner_id, 
    COUNT(order_id) AS order_count
FROM pizza_runner.runner_orders
WHERE pickup_time IS NOT NULL
GROUP BY runner_id;
````
#### Answer
| runner_id      | order_count |
|--------------------|-------------|
| 1                  | 4           |
| 2                  | 3           |
| 3                  | 1           |
### Question 4: How many of each type of pizza was delivered?
#### SQL Query
````sql

````
#### Answer

### Question 5: How many Vegetarian and Meatlovers were ordered by each customer?
#### SQL Query
````sql

````
#### Answer

### Question 6: What was the maximum number of pizzas delivered in a single order?
#### SQL Query
````sql

````
#### Answer

### Question 7: For each customer, how many delivered pizzas had at least 1 change and how many had no changes?
#### SQL Query
````sql

````
#### Answer

### Question 8: How many pizzas were delivered that had both exclusions and extras?
#### SQL Query
````sql

````
#### Answer

### Question 9: What was the total volume of pizzas ordered for each hour of the day?
#### SQL Query
````sql

````
#### Answer

### Question 10: What was the volume of orders for each day of the week?
#### SQL Query
````sql

````
#### Answer

## Runner and Cx Experience

