```
Table: Employee:
+----+--------+
| Id | Salary |
+----+--------+
| 1  | 100    |
| 2  | 200    |
| 3  | 300    |
+----+--------+
```
  **Id** is the primary key column for this table.
  Each row of this table contains information about the salary of an employee.
 

  Write an SQL query to report the nth highest salary from the Employee table. If there is no nth highest salary, the query should report null.

  The query result format is in the following example.
```
Input: 
Employee table:
+----+--------+
| id | salary |
+----+--------+
| 1  | 100    |
| 2  | 200    |
| 3  | 300    |
+----+--------+
n = 2
Output: 
+------------------------+
| getNthHighestSalary(2) |
+------------------------+
| 200                    |
+------------------------+
```
My solotion:
```
CREATE FUNCTION getNthHighestSalary(N INT) RETURNS INT
BEGIN
SET N = N - 1;
  RETURN (
      SELECT
      # Write your MySQL query statement below.
        (SELECT
            DISTINCT(salary)
        FROM
            Employee  
        ORDER BY
            salary DESC
        LIMIT 1
            OFFSET N)
      AS NthHighesSalary 
  );
END
```
Reason:
Consider the initial, the second Highest Salary.
Because the subquery will run first, and we only want to show one variable in output, hence, using 
```
LIMIT 1
OFFSET N
```
Since I don't need other variable, i.e we need to filter them.
Here, we can go run the subquery with Alias and finish the  function.
