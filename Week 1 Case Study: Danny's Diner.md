# Week 1 Case Study: Danny's Diner
<a href="https://8weeksqlchallenge.com/case-study-1/"> <img src= "https://8weeksqlchallenge.com/images/case-study-designs/1.png" width="500" height="520" alt="image" target="_blank"> </a>

## Question 1: What is the total amount each customer spent at the restaurant?

#### SQL Query
````sql
SELECT 
  sales.customer_id, 
  SUM(menu.price) AS total_sales
FROM dannys_diner.sales
JOIN dannys_diner.menu
  ON sales.product_id = menu.product_id
GROUP BY sales.customer_id
ORDER BY sales.customer_id ASC;
````
#### Answer
| customer_id | total_sales |
|-------------|-------------|
| A           | 76          |
| B           | 74          |
| C           | 36          |

## Question 2: How many days has each customer visited the restaurant?
````sql
SELECT
  sales.customer_id,
  COUNT(DISTINCT order_date) AS Total_days_visted
FROM dannys_diner.sales
GROUP by sales.customer_id
ORDER BY total_days_visted DESC;
````
#### Answer
| customer_id | total_days_visted |
|-------------|-------------------|
| B           | 6                 |
| A           | 4                 |
| C           | 2                 |

## Question 3: What was the first item from the menu purchased by each customer?
````sql
WITH order_cte AS
(
SELECT
	sales.customer_id,
    sales.order_date,
    menu.product_name,
    DENSE_RANK() OVER(
      PARTITION BY sales.customer_id
      ORDER BY sales.order_date) AS RANK
FROM dannys_diner.sales
LEFT JOIN dannys_diner.menu
ON sales.product_id = menu.product_id
)

SELECT 
	DISTINCT customer_id,
    product_name
FROM order_cte
WHERE rank= 1;
````
#### Answer
| customer_id | product_name |
|-------------|-------------------|
| A           | curry             |
| A           | sushi             |
| B           | curry             |
| C           | ramen             |

*Customer A ordered twice at the same time
## Question 4: What is the most purchased item on the menu and how many times was it purchased by all customers?
````sql
SELECT
    menu.product_name,
	COUNT(customer_id) AS Total_Orders
FROM dannys_diner.sales
JOIN dannys_diner.menu
	ON sales.product_id = menu.product_id
GROUP BY menu.product_name
ORDER BY total_orders DESC
LIMIT 1
````
#### Answer
| product_name | total_orders     |
|-------------|-------------------|
| ramen       | 8                 |

## Question 5: Which item was the most popular for each customer?
````sql
WITH most_popular_item_cte AS
(
  SELECT 
  	sales.customer_id,
  	menu.product_name,
  	COUNT(menu.product_id) AS number_ordered,
  	RANK() OVER (
  		PARTITION BY sales.customer_id 
  		ORDER BY COUNT(menu.product_id) DESC) AS popularity_rank
  	FROM dannys_diner.sales
  JOIN dannys_diner.menu
  ON sales.product_id = menu.product_id
  GROUP BY sales.customer_id,menu.product_name
)
SELECT
  customer_id,
  product_name,
  number_ordered
FROM most_popular_item_cte
WHERE popularity_rank = 1
````
####Answer
| customer_id | product_name      | number_ordered|
|-------------|-------------------|---------------|
| A           | ramen             | 3             |
| B           | ramen             | 2             |
| B           | curry             | 2             |
| B           | sushi             | 2             |
| C           | ramen             | 3             |
Customer B had a tie for 3 of the products
## Question 6: Which item was purchased first by the customer after they became a member?
````sql

````
## Question 7: Which item was purchased just before the customer became a member?
````sql

````
## Question 8: What is the total items and amount spent for each member before they became a member?
````sql

````
## Question 9: If each $1 spent equates to 10 points and sushi has a 2x points multiplier - how many points would each customer have?
````sql

````
## Question 10: In the first week after a customer joins the program (including their join date) they earn 2x points on all items, not just sushi - how many points do customer A and B have at the end of January?
````sql

````
