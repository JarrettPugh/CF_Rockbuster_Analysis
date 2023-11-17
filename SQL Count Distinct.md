This SQL query returns the different film genres, their revenues, the number of films in each genre, and average revenue per film ordered by total revenue amount.

Here is the SQL query:

```sql
SELECT
    E.name AS film_genre,
    SUM(A.amount) AS revenue_amount,
    COUNT(DISTINCT F.film_ID) AS number_of_films,
    ROUND(SUM(A.amount) / COUNT(DISTINCT F.film_ID), 2) AS revenue_per_film
FROM
    payment A
    INNER JOIN rental B ON A.rental_id = B.rental_id
    INNER JOIN inventory C ON B.inventory_id = C.inventory_id
    INNER JOIN film_category D ON C.film_id = D.film_id
    INNER JOIN category E ON D.category_id = E.category_id
    INNER JOIN film F ON C.film_id = F.film_id
GROUP BY
    film_genre
ORDER BY
    revenue_amount DESC
```
