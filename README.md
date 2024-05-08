<p align="center">
  <img src="https://github.com/KwasekM/SQL/assets/120929766/e375926b-f505-4309-9a70-a58d09357861" />
</p>


# 🚀 Summary and demonstration of my SQL skills 🚀

1. [Summary of my skills](#subtask1)
2. [SQL tasks](#subtask2)


   
## <a name="subtask1">My SQL skills</a>
* Using SELECT sql command to query one and multiple tables.
* Using SELECT sql command with WHERE clauses to filter and refine queries.
* Using SELECT sql command with WHERE clauses and boolean operators (AND, OR, NOT, LIKE, IN, BETWEEN) to filter and refine queries.
* Using JOIN sql command and understand variants (INNER, OUTER) to create table relationships.
* Using aggregate functions (SUM, MIN, MAX, AVG) to restrict returned data set.
* Using HAVING clause to restrict returned data set.
* Using GROUP BY clause to organize returned data set.
* Using string, date, and time functions.
* Using the CREATE TABLE command to design data tables.
* Using the ALTER TABLE command to modify a table.

### <a name="subtask2"> SQL tasks from coderwars solved by me 👩‍💻 </a>

1. Write an SQL query that selects the names of the opinion giver and receiver(opinion_giver and opinion_receiver), along with their current (current_opinion) and previous (previous_opinion) opinions. Include only records where the current opinion differs from the previous opinion. Sort the results first by the name of the opinion giver and then by the name of the opinion receiver - both in ascending alphabetical order.

```sql
SELECT
    giver.name AS opinion_giver,
    receiver.name AS opinion_receiver,
    current_opinion,
    previous_opinion
FROM
    people_opinions
INNER JOIN
    people AS giver ON people_opinions.opinion_giver_id = giver.person_id
INNER JOIN
    people AS receiver ON people_opinions.person_id = receiver.person_id
WHERE
    current_opinion != previous_opinion
OR  (current_opinion IS NULL and previous_opinion IS NOT null)
OR  (current_opinion IS NOT NULL and previous_opinion IS NULL)
ORDER BY opinion_giver, opinion_receiver
```

