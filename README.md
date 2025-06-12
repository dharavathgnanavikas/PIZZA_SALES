# <p align="center">PIZZA_SALES_PROJECT</p>
# <p align="center">![image](https://github.com/user-attachments/assets/fc6f85fb-10d5-4604-8123-7431500ea8e2)</p>

**Tools Used:** EXCEL, MySQL, POWER-BI

[Datasets Used](https://drive.google.com/file/d/145icXZlekozs9xTZoOZFvqL9wREm1xOj/view?usp=sharing)

[SQL Analysis (Code)](https://github.com/gnanavikas0112/PIZZA_SALES/blob/main/PIZZA_SALES_SQL_ANALYSIS)

[Pizza Sales Dashboard - Power-BI](https://drive.google.com/file/d/17t6Ev6uhLfJL07Erbl72UvFzeVVto-Qn/view?usp=sharing)




## Questions I Wanted To Answer From the Dataset:

## 1. What is the total revenue from pizza sales ?

- TOTAL REVENUE
```mysql
SELECT SUM(total_price) AS Total_Revenue FROM pizza_sales;
```
Result:

![Q1](https://github.com/gnanavikas0112/PIZZA_SALES/blob/00a1d8e72a2ff6bba9607157e1a4ea2bbff74710/Screenshot%202025-06-10%20194806.png)

## 2. What is the average order value from pizza sales ?
- AVERAGE ORDER VALUE
```mysql
SELECT (SUM(total_price) / COUNT(DISTINCT order_id)) AS Avg_order_Value FROM pizza_sales
```
Result:

![Q2](https://github.com/gnanavikas0112/PIZZA_SALES/blob/aee4cc6fdf0d13789286d59e75bc78c066cce878/Screenshot%202025-06-10%20195219.png)

## 3. What is the total pizzas sold from pizza sales ?
- TOTAL PIZZAS SOLD
```mysql
SELECT SUM(quantity) AS Total_pizza_sold FROM pizza_sales
```
Result: 

![Q3](https://github.com/gnanavikas0112/PIZZA_SALES/blob/49dbe1ccf056ddfcaae39c205497666b7b9ae750/Screenshot%202025-06-10%20195434.png)

## 4. What is the total orders from pizza sales ?
- TOTAL ORDERS
```mysql
SELECT COUNT(DISTINCT order_id) AS Total_Orders FROM pizza_sales
```

Result:

![Q4](https://github.com/gnanavikas0112/PIZZA_SALES/blob/afa7fe28ac8e9873bebe2dd8ae41472abf17bfce/Screenshot%202025-06-10%20195636.png)

## 5. What is the average pizzas per order from pizza sales ?
- AVERAGE PIZZAS PER ORDER
```mysql
SELECT CAST(CAST(SUM(quantity) AS DECIMAL(10,2)) / 
CAST(COUNT(DISTINCT order_id) AS DECIMAL(10,2)) AS DECIMAL(10,2))
AS Avg_Pizzas_per_order
FROM pizza.sales;
```

Result:

![Q5](https://github.com/gnanavikas0112/PIZZA_SALES/blob/619ce0573eeeafdb295e790caec852fcf3bc843b/Screenshot%202025-06-10%20200612.png)

## 6. What is the daily trend for total orders from pizza sales ?
- Daily trend for total orders
```mysql
SELECT DATENAME(DW, order_date) AS order_day, COUNT(DISTINCT order_id) AS total_orders 
FROM pizza_sales
GROUP BY DATENAME(DW, order_date)
```

Result:

![Q6](https://github.com/gnanavikas0112/PIZZA_SALES/blob/6fe610f5c13fe1f4659959625b88e5ef76a8153d/Screenshot%202025-06-11%20104838.png)

## 7. What is percentage of sales by pizza category from pizza sales ?
- % of sales by pizza category
```mysql
SELECT 
    PIZZA_CATEGORY AS CATEGORY, 
    CAST(SUM(TOTAL_PRICE) AS DECIMAL(10,2)) AS REVENUE,
    (SUM(TOTAL_PRICE) * 100.0) / SUM(SUM(TOTAL_PRICE)) OVER () AS PCT
FROM PIZZA.SALES
GROUP BY PIZZA_CATEGORY;
```

Result:

![Q7](https://github.com/gnanavikas0112/PIZZA_SALES/blob/9809d004ab78b332d81e1b7941dda37cbffc7276/Screenshot%202025-06-10%20204432.png)

## 8. What is the percentage of sales by pizza size from pizza sales ?
- % of sales by pizza size
```mysql
SELECT PIZZA_SIZE, SUM(TOTAL_PRICE) AS PRICE,
(SUM(TOTAL_PRICE)*100)/(select SUM(TOTAL_PRICE) from pizza.sales) AS PCT
FROM PIZZA.SALES
GROUP BY PIZZA_SIZE;
```

Result:

![Q8](https://github.com/gnanavikas0112/PIZZA_SALES/blob/b5d65a8cc4dcbdd9f3e913daa6c9dc1d74644123/Screenshot%202025-06-10%20212008.png)

## 9. What is the total pizzas sold by pizza category ?
- Total pizzas sold by pizza category
```mysql
SELECT pizza_category, SUM(quantity) as Total_Quantity_Sold
FROM pizza.sales
GROUP BY pizza_category
```

Result:

![Q8](https://github.com/gnanavikas0112/PIZZA_SALES/blob/00670bb576aabac3d16258d90ef44136e6e7d44f/Screenshot%202025-06-11%20112340.png)

## 10. What are the top 6 pizzas by total revenue ?
- Top 6 pizzas by revenue
```mysql
select pizza_name, sum(total_price) as total_revenue
from pizza.sales
group by pizza_name
order by total_revenue desc
limit 6;
```

Result:

![Q10](https://github.com/gnanavikas0112/PIZZA_SALES/blob/011bacf30ca2b15ae46e682034e34bcb82b2793f/Screenshot%202025-06-11%20113105.png)

## 11. What are the bottom 6 pizzas by total revenue ?
- Bottom 6 pizzas by revenue
```mysql
select pizza_name, sum(total_price) as total_revenue
from pizza.sales
group by pizza_name
order by total_revenue
limit 6;
```

Result:

![Q11](https://github.com/gnanavikas0112/PIZZA_SALES/blob/2659f634fdc575f0145bf86c231dfeeb426bb646/Screenshot%202025-06-11%20113148.png)

## 12. What are the top 6 pizzas by total quantity ?
- Top 6 pizzas by quantity
```mysql
select pizza_name, sum(quantity) as total_quantity
from pizza.sales
group by pizza_name
order by total_quantity desc
limit 6;
```

Result:

![Q12](https://github.com/gnanavikas0112/PIZZA_SALES/blob/6babdb271f6f514bf57325d40922fb092aef0a53/Screenshot%202025-06-11%20113312.png)

## 13. What are the bottom 6 pizzas by total quantity ?
- bottom 6 pizzas by quantity
```mysql
select pizza_name, sum(quantity) as total_quantity
from pizza.sales
group by pizza_name
order by total_quantity
limit 6;
```

Result:

![Q13](https://github.com/gnanavikas0112/PIZZA_SALES/blob/d1689a7b69d46419443ae130ef15063aff881bfd/Screenshot%202025-06-11%20113359.png)

## 14. What are the top 6 pizzas by total orders ?
- Top 6 pizzas by total orders
```mysql
select pizza_name, count(distinct order_id) as total_orders
from pizza.sales
group by pizza_name
order by total_orders desc
limit 6;
```

Result:

![Q14](https://github.com/gnanavikas0112/PIZZA_SALES/blob/fa8e9eaafbc8f908bc21210d52e5259a1cdf2986/Screenshot%202025-06-11%20113612.png)

## 15. What are the bottom 6 pizzas by total orders ?
- bottom 6 pizzas by total orders
```mysql
select pizza_name, count(distinct order_id) as total_orders
from pizza.sales
group by pizza_name
order by total_orders
limit 6;
```

Result:

![Q15](https://github.com/gnanavikas0112/PIZZA_SALES/blob/8e1afa029e4f72868720655cff2e807a1ed3e343/Screenshot%202025-06-11%20113657.png)






