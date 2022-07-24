```
Table: Activities:
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| sell_date   | date    |
| product     | varchar |
+-------------+---------+
+------------+------------+
| sell_date  | product    |
+------------+------------+
| 2020-05-30 | Headphone  |
| 2020-06-01 | Pencil     |
| 2020-06-02 | Mask       |
| 2020-05-30 | Basketball |
| 2020-06-01 | Bible      |
| 2020-06-02 | Mask       |
| 2020-05-30 | T-Shirt    |
+------------+------------+
```
There is no primary key for this table, it may contain duplicates.

Each row of this table contains the product name and the date it was sold in a market.

Write an SQL query to find for each date the number of different products sold and their names.

The sold products names for each date should be sorted lexicographically.

Return the result table ordered by sell_date.

My solution:
```
SELECT
  sell_date,
  COUNT(DISTINCT(product)) AS num_sold,
  GROUP_CONCAT(DISTINCT(product)) AS product
FROM
  Activities
GROUP BY
  sell_date
```
Reason:

This question asks me to group product by data, and show the num_sold totally.
Clearly, we can compute the SELECT part.

But, we need to think how to combine the product together, so we can use the GROUP_CONCAT()

See clear defination by here. 

![GROUP_CONCATE](https://www.w3resource.com/mysql/Mysql-pics/mysql-group-concat-example1.gif)

After we add the GROUP_CONCAT(), we need to add GROUP BY.
