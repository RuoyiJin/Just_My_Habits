```
Table: Person
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| id          | int     |
| email       | varchar |
+-------------+---------+
```
**id** is the primary key column for this table.

Each row of this table contains an email. The emails will not contain uppercase letters.

Write an SQL query to delete all the duplicate emails, keeping only one unique email with the smallest id. Note that you are supposed to write a DELETE statement and not a SELECT one.

My Solution:
```
DELETE P1
FROM 
  Person AS P1
JOIN
  Person AS P2
ON 
  P1.email = P2.email
WHERE
  P1.id > P2.id
```

Explaination: 
This question is tricky...(I think) It asks me to delete the dupicate email. 
The output should looks like this, (see below)
```
FROM:
+----+------------------+
| id | email            |
+----+------------------+
| 1  | john@example.com |
| 2  | bob@example.com  |
| 3  | john@example.com |
+----+------------------+
TO:
+----+------------------+
| id | email            |
+----+------------------+
| 1  | john@example.com |
| 2  | bob@example.com  |
+----+------------------+
```
Here we can use DELETE() FROM().
First, my method is using JOIN itself to compute the solution, so we use JOIN:
```
FROM 
  person AS P1 # (Set itself P1 and P2)
JOIN 
  person AS P2
ON 
  P1.email = P2.email
```

Then we need to delect the duplicate email, and change the id. So, we add a filter:
```
WHERE
  P1.id > P2.id # (Because we want to remove the larger  id.)
```
**Why we DELETE P1?**

Because we set a filter that P1.id > P2.id. And since we want to remove the higher id, so we set a filter liks this.

**We also can remove the P2**

If we want to remove P2, it means P2.id needs to be a higher id, hence we can change the filter from P1.id > P2.id to P1.id < P2.id.
Here, the syntax should be:
```
DELETE P2
FROM
  person AS P1
JOIN
  person AS P2
ON
  P1.email = P2.email
WHERE
  P1.id < P2.id
```
  
