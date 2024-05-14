<p align="center">
  <img src="https://github.com/KwasekM/SQL/assets/120929766/5dceb698-be53-42f7-87a5-5b398895bf14" />
</p>
<p align="center">
 <a href="https://pl.freepik.com/darmowe-wektory/recznie-rysowane-ilustracja-plaska-konstrukcja-sql_21901980.htm#fromView=search&page=1&position=0&uuid=102afa6a-6594-46f0-88ca-31fc63a26c0c">Image by freepik</a>
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

## <a name="subtask2"> SQL tasks from coderwars solved by me 👩‍💻 </a>
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
![Zrzut ekranu 2024-05-09 000819](https://github.com/KwasekM/SQL/assets/120929766/4bd16cbf-7b6b-4b50-a937-e55e2b5be42e)

2. Return the list of films that have not been rented out at all in the past month, but have been rented at least 10 times in total. Include the film_id, title of the film and in the brackets, its rating, rental count, and the date of the most recent rental. Since the business is in America, please use American date notation (for example, 'April 09, 2023').

```sql
SELECT 
  film.film_id, 
  CONCAT(film.title, ' (',film.rating, ')' )AS film_title, 
  COUNT(rental.inventory_id) AS rental_count,
  TO_CHAR(MAX(rental.rental_date), 'FMMonth DD, YYYY') AS last_rental_date 
FROM 
  film
INNER JOIN
  inventory ON film.film_id=inventory.film_id
INNER JOIN 
  rental ON inventory.inventory_id=rental.inventory_id
GROUP BY  
  film.film_id
HAVING 
  COUNT(rental.inventory_id) >=10 AND  MAX(rental.rental_date) < CURRENT_DATE - INTERVAL '1 month'
ORDER BY 
  rental_count DESC, 
  last_rental_date DESC, 
  film.title
```
![Zrzut ekranu 2024-05-09 001452](https://github.com/KwasekM/SQL/assets/120929766/1f7db226-d7ec-45ba-9e9b-3b1932a09c99)

