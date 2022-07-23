```
Table: Salary
+-------------+----------+
| Column Name | Type     |
+-------------+----------+
| id          | int      |
| name        | varchar  |
| sex         | ENUM     |
| salary      | int      |
+-------------+----------+
```
**id** is the primary key for this table. 
The sex column is ENUM value of type ('m', 'f').

The table contains information about an employee.

Write an SQL query to swap all 'f' and 'm' values (i.e., change all 'f' values to 'm' and vice versa) with a single update statement and no intermediate temporary tables.

Note that you must write a single update statement, do not write any select statement for this problem.

The query result format is in the following example.

My solution:
```
UPDATA Salary
SET sex = sex
CASE sex
  WHEN 'm'
  THEN 'f'
 ELSE 'm'
 END
 ```
 Explaination: This question ask me to conver the sex, for example, if the gender is F, change it to M. (If the gender if M, change it to F)
 Hence, we need to rewrite the information of the table. When we need to rewrite(correct) the table, we can use: 
 ```
 UPDATE(*Table name*) 
 SET(*original column name* = *new column name*).
 ```
 Since this question is depending on different conditions. ie.the gender.
 We need to use CASE WHEN
 Here we have:
 ```
 CASE sex # (only focus on column 'sex')
  WHEN 'm' # (when the sex column has a cell m) THEN 'f' # (then chenge it to f)
 ELSE 'm'# (other cells except m change to m)
 END
 ```
 
