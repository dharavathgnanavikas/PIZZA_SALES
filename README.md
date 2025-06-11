# PIZZA_SALES
# <p align="center">PIZZA_SALES PROJECT</p>
# <p align="center">![image](https://github.com/user-attachments/assets/fc6f85fb-10d5-4604-8123-7431500ea8e2)</p>

**Tools Used:** EXCEL, MySQL, POWER-BI

[Datasets Used](https://drive.google.com/file/d/145icXZlekozs9xTZoOZFvqL9wREm1xOj/view?usp=sharing)



## Questions I Wanted To Answer From the Dataset:

## 1. What is the total revenue from pizza sales?

--> TOTAL REVENUE
```mysql
SELECT SUM(total_price) AS Total_Revenue FROM pizza_sales;
```
Result:

![Q1](https://github.com/gnanavikas0112/PIZZA_SALES/blob/00a1d8e72a2ff6bba9607157e1a4ea2bbff74710/Screenshot%202025-06-10%20194806.png)

## 2. What is the average order value from pizza sales?
--> AVERAGE ORDER VALUE
```mysql
SELECT (SUM(total_price) / COUNT(DISTINCT order_id)) AS Avg_order_Value FROM pizza_sales
```
Result:

![Q2](https://github.com/gnanavikas0112/PIZZA_SALES/blob/aee4cc6fdf0d13789286d59e75bc78c066cce878/Screenshot%202025-06-10%20195219.png)

## 3. What is the total pizzas sold from pizza sales?
--> TOTAL PIZZAS SOLD
```mysql
SELECT SUM(quantity) AS Total_pizza_sold FROM pizza_sales
```
Result: 

![Q3](https://github.com/gnanavikas0112/PIZZA_SALES/blob/49dbe1ccf056ddfcaae39c205497666b7b9ae750/Screenshot%202025-06-10%20195434.png)

## 4. What is the total orders from pizza sales?
--> TOTAL ORDERS
```mysql
SELECT COUNT(DISTINCT order_id) AS Total_Orders FROM pizza_sales
```

Result:

![Q4](https://github.com/gnanavikas0112/PIZZA_SALES/blob/afa7fe28ac8e9873bebe2dd8ae41472abf17bfce/Screenshot%202025-06-10%20195636.png)

## 5. What is the average pizzas per order from pizza sales?
--> AVERAGE PIZZAS PER ORDER
```mysql
SELECT CAST(CAST(SUM(quantity) AS DECIMAL(10,2)) / 
CAST(COUNT(DISTINCT order_id) AS DECIMAL(10,2)) AS DECIMAL(10,2))
AS Avg_Pizzas_per_order
FROM pizza.sales;
```

Result:

![Q5]()





