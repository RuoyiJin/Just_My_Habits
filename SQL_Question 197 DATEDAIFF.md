```
Table: Weather
+---------------+---------+
| Column Name   | Type    |
+---------------+---------+
| id            | int     |
| recordDate    | date    |
| temperature   | int     |
+---------------+---------+
+----+------------+-------------+
| id | recordDate | temperature |
+----+------------+-------------+
| 1  | 2015-01-01 | 10          |
| 2  | 2015-01-02 | 25          |
| 3  | 2015-01-03 | 20          |
| 4  | 2015-01-04 | 30          |
+----+------------+-------------+
TO:
+----+
| id |
+----+
| 2  |
| 4  |
+----+
```
**id** is the primary key for this table.

This table contains information about the temperature on a certain day.
 

Write an SQL query to find all dates' Id with higher temperatures compared to its previous dates (yesterday).

Return the result table in any order.

My solution:
```
SELECT
  A.id
FROM
  Weather A, Weather B
WHERE
  A.temperature > B.temperature
  AND
  DATEDIFF(A.recordDate, B.recordDate) = 1
```
Reason:

  This question ask to find the id which has a temp higher than last day. That is clearly we need to add id under the select part.
  
  So the problem is how can we compare the temp.
  
  We can consider to use the Table1.A to compare Table1.copy. and we can use datediff to compare the date.
  
  In my solution, I use ```DATEDIFF(A.recordDate, B.recordDate) = 1``` Since I need to let the diff between two dates in 1. 
  
  It means that the difference between 2 dates should be 1 day as it is asked in the question so datediff function will take difference between 2 dates and =1 means there difference should be 1
