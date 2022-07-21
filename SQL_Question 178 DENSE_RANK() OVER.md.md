```
Table: Scores:
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| id          | int     |
| score       | decimal |
+-------------+---------+
```
**id**  is the primary key for this table.
Each row of this table contains the score of a game. Score is a floating point value with two decimal places.
 

Write an SQL query to rank the scores. The ranking should be calculated according to the following rules:

The scores should be ranked from the highest to the lowest.
If there is a tie between two scores, both should have the same ranking.
After a tie, the next ranking number should be the next consecutive integer value. In other words, there should be no holes between ranks.
Return the result table ordered by score in descending order

My solution:
```
SELECT
    score,
    DENSE_RANK() OVER
        (ORDER BY score DESC) AS 'rank'
FROM
    Scores  
```
Reason: Consider what should we oupput. The score, and the rank of score.(By descending)
Then we need to figure out how to create ranks for different score.
We can apply the DENSE_RANK() OVER(   ) to create rank.
Attention: The syntax for this function should be:
```
DENSE_RANK() OVER (ORDER BY xxx DESC/ASC) AS rank_name
```
