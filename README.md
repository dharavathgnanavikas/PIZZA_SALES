# PIZZA_SALES
# <p align="center">PIZZA_SALES PROJECT</p>
# <p align="center">![image](https://github.com/user-attachments/assets/fc6f85fb-10d5-4604-8123-7431500ea8e2)</p>

**Tools Used:** EXCEL, MySQL, POWER-BI

[Datasets Used](https://drive.google.com/file/d/145icXZlekozs9xTZoOZFvqL9wREm1xOj/view?usp=sharing)



## Questions I Wanted To Answer From the Dataset:

## 1. what is the total revenue from pizza sales?

-TOTAL REVENUE
```mysql
SELECT SUM(total_price) AS Total_Revenue FROM pizza_sales;
```
Result:
![Q1](https://github.com/gnanavikas0112/PIZZA_SALES/blob/00a1d8e72a2ff6bba9607157e1a4ea2bbff74710/Screenshot%202025-06-10%20194806.png)

## 2. what is the average order value from pizza sales?
-AVERAGE ORDER VALUE
```mysql
SELECT (SUM(total_price) / COUNT(DISTINCT order_id)) AS Avg_order_Value FROM pizza_sales
```
Result:
![Q2]()

