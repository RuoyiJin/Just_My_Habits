```
Table: Patients
+--------------+---------+
| Column Name  | Type    |
+--------------+---------+
| patient_id   | int     |
| patient_name | varchar |
| conditions   | varchar |
+--------------+---------+
+------------+--------------+--------------+
| patient_id | patient_name | conditions   |
+------------+--------------+--------------+
| 1          | Daniel       | YFEV COUGH   |
| 2          | Alice        |              |
| 3          | Bob          | DIAB100 MYOP |
| 4          | George       | ACNE DIAB100 |
| 5          | Alain        | DIAB201      |
+------------+--------------+--------------+
```
patient_id is the primary key for this table.

'conditions' contains 0 or more code separated by spaces. 

This table contains information of the patients in the hospital.

Write an SQL query to report the patient_id, patient_name all conditions of patients who have Type I Diabetes. Type I Diabetes always starts with ```DIAB1``` prefix

Return the result table in any order.

My solution:
```
SELECT
  patient_id,
  patient_name,
  conditions
FROM
  Patients
WHERE
  conditions LIKE 'DIAB1'
  OR
  conditions LIKE '%DIAB1%'
  OR
  conditions LIKE '%DIAB1'
  OR
  conditions LIKE 'DIAB1%'
```
Reason:

This question is easy, first we can know the SELECT part and the FROM part are clearly shown in the table.
So, we only need to think how to get a filter for the table which the conditions need to conatins "DIAB1".

Hence, we can add filter query, WHERE.

Hence, we have:
```
WHERE
  conditions LIKE 'DIAB1'
  OR
  conditions LIKE '%DIAB1%'
  OR
  conditions LIKE '%DIAB1'
  OR
  conditions LIKE 'DIAB1%'
```
