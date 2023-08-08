# MySQL
This is a project to learning for using Strutured Query Language. The data used is Pakistan's Largest E-Commerce Dataset obtain from Kaggle.
You can use the data by click this link
https://drive.google.com/drive/folders/1oYnl_GqEPFh0-WSrEokZJWuHV3qxsIrp?usp=sharing

From the data i used SQL to obtain information :
1. Transactions that occurred during 2021, in which month was the total number of customers (unique), total orders (unique) and total number of product quantities the most?
2. Transactions that occurred during 2022, which category generated the most transaction value?

To solve the question 1, i make query below.

SELECT
DATE_FORMAT(order_date, '%M') AS month_2021,
COUNT(DISTINCT customer_id) as total_pelanggan,
COUNT(DISTINCT id) AS total_pesanan,
SUM(qty_ordered) AS total_kuantitas
FROM order_detail 
WHERE
is_valid = 1 AND YEAR(order_date)=2021
GROUP BY 1
ORDER BY 2 DESC

![image](https://github.com/agilsafrudin/MySQL/assets/141690907/efbc73b4-23ff-41da-bd59-90a9ea60b30f)


For the other question (number 2), i make this query.

SELECT
sd.category,
SUM(od.after_discount) total_sales
FROM order_detail AS od
LEFT JOIN sku_detail AS sd ON sd.id = od.sku_id
WHERE
is_valid = 1 AND YEAR(od.order_date)=2021
GROUP BY 1
ORDER BY 2 DESC

![image](https://github.com/agilsafrudin/MySQL/assets/141690907/dcc63591-ba37-4deb-8c47-61cd955156b2)

This project is still in development, and there are many more things I can explore using this dataset. I plan to continue updating the results I obtain in the future. Such is the project I have created.

Regards,
Agil Safrudin
