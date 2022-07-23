```
Table: Employees
Employees table:
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| employee_id | int     |
| name        | varchar |
| salary      | int     |
+-------------+---------+
```
**employee_id** is the primary key for this table.

  Each row of this table indicates the employee ID, employee name, and salary.
  
Write an SQL query to calculate the bonus of each employee. The bonus of an employee is 100% of their salary if **the ID of the employee is an odd number** and the **employee name does not start with the character 'M'**. The bonus of an employee is 0 otherwise.

Return the result table ordered by employee_id.

Mu solution:
```
SELECT
  employee_id,
CASE
  WHEN employee_id%2 = 1 AND name NOT LIKE "M%"
  THEN salary
 ELSE 
 END AS bonus  
FROM
  Employees
```
Explaination: The question asks me to compute the employee whose ID number is odd, and names do start with M. Here we can compute the require columns' names are: employee_id and bonus.
We can compute the SELECT. But we do not have "bonus" in original table, so we need to add the requirement into the CASE to Alisa a column.
Then we can consider the Alisa. Consider the requirement in CASE. We need to familiar with the Query: CASE, WHEN(), THEN, ELSE, END AS.
Since the ID needs to be an odd number, hence we can have: 
```
CASE
  WHEN employee_id %2 = 1 # it means employee substract 2 has a remainder 1. Which means the id is an odd number.
  AND name NOT LIKE "M%" # it means the name does not start with letter M.
  THEN salart # then compute salary
 ELSE
 END AS bonus
 ```
