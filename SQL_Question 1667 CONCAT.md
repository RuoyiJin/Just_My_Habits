```
Table: Users
+----------------+---------+
| Column Name    | Type    |
+----------------+---------+
| user_id        | int     |
| name           | varchar |
+----------------+---------+
+---------+-------+
| user_id | name  |
+---------+-------+
| 1       | aLice |
| 2       | bOB   |
+---------+-------+
```
**user_id** is the primary key for this table.

This table contains the ID and the name of the user. The name consists of only lowercase and uppercase characters

Write an SQL query to fix the names so that only the first character is uppercase and the rest are lowercase.

Return the result table ordered by user_id.

The query result format is in the following example.

My solution:
```
SELECT
  user_id,
  CONCAT(UPPER(SUBSTR(name,1,1)),LOWER(name,2)) AS name
FROM
  Users
ORDER BY
  user_id
```
Reason:

This question ask me to correct the format of the name, it requires me to output the user_id and name, hence we have SELECT part.

However, the name includes wrong format, so we need to rewrite it and recompute it AS name. So, we can use CONCAT to combine the upper letter to the lower letter.
The SUBSTR() is help for sepreating a string.
```
SUBSTR(A,index,length)
```
Then, we start to rewrite the format of each name by using UPPER() and LOWER(), and Concate them together.
```
CONCAT(A,B)
```
So, we can put them together and we can have:
```
  CONCATE(UPPER(SUBSTR(A,1,1)),LOWER(SUBSTR(A,2)))
```
Then we can add AS to give the correct fromat a name.
