```
Table: Tree
+-------------+------+
| Column Name | Type |
+-------------+------+
| id          | int  |
| p_id        | int  |
+-------------+------+
Tree table:
+----+------+
| id | p_id |
+----+------+
| 1  | null |
| 2  | 1    |
| 3  | 1    |
| 4  | 2    |
| 5  | 2    |
+----+------+
TO:
+----+-------+
| id | type  |
+----+-------+
| 1  | Root  |
| 2  | Inner |
| 3  | Leaf  |
| 4  | Leaf  |
| 5  | Leaf  |
+----+-------+
```
![pic](https://assets.leetcode.com/uploads/2021/10/22/tree1.jpg)

Each node in the tree can be one of three types:

* "Leaf": if the node is a leaf node.

* "Root": if the node is the root of the tree.

* "Inner": If the node is neither a leaf node nor a root node.

Write an SQL query to report the type of each node in the tree.

Return the result table ordered by id in ascending order.

My solution:
```
SELECT
  id,
CASE
  WHEN p_id IS NULL
  THEN "Root"
  WHEN  id IN (SELECT p_id FROM Tree) 
  THEN "Inner"
ELSE "Leaf"
END AS type
FROM
  Tree
```
