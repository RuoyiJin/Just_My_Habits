```
Table: Employees

+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| employee_id | int     |
| name        | varchar |
+-------------+---------+

+-------------+----------+
| employee_id | name     |
+-------------+----------+
| 2           | Crew     |
| 4           | Haven    |
| 5           | Kristian |
+-------------+----------+
employee_id is the primary key for this table.
```
```
Table: Salaries

+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| employee_id | int     |
| salary      | int     |
+-------------+---------+
+-------------+--------+
| employee_id | salary |
+-------------+--------+
| 5           | 76071  |
| 1           | 22517  |
| 4           | 63539  |
+-------------+--------+
employee_id is the primary key for this table.
```
Write an SQL query to report the IDs of all the employees with missing information. The information of an employee is missing if:

The employee's **name** is missing, or the employee's **salary** is missing.

Return the result table ordered by employee_id in **ascending order**.

My solution:
```
SELECT
  employee_id
FROM
  Employees AS E
LEFT JOIN
  Salaries AS S
USING
  (employee_id)
WHERE
  S.salary IS NULL
UNION
SELECT
  employee_id
FROM
  Employees AS E
RIGHT JOIN
  Salaries AS S
USING
  (employee_id)
WHERE
  E.name IS NULL
ORDER BY
  employee_id
 ```
 MySQL does not support FULL JOIN, so you have to combine LEFT JOIN, UNION and RIGHT JOIN to get an equivalent. 
 
 It gives the results of A union B. It returns all records from both tables. Those columns which exist in only one table will contain NULL in the opposite table.
