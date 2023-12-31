This SQL query returns the most popular films, rental rates, and generated revenue ordered by the number of times rented.

Here is the SQL query:

```sql
SELECT
    C.title,
    COUNT(A.rental_id) AS number_of_rentals,
    C.rental_rate AS rental_price,
    C.rental_rate * COUNT(A.rental_id) AS rental_revenue,
    SUM(D.amount) - (C.rental_rate * COUNT(A.rental_id)) AS rental_fees,
    SUM(D.amount) AS total_revenue
FROM
    rental A
INNER JOIN
    inventory B ON A.inventory_id = B.inventory_id
INNER JOIN
    film C ON B.film_id = C.film_id
INNER JOIN
    payment D ON A.rental_id = D.rental_id
GROUP BY
    C.title,
    C.rental_rate
ORDER BY
    number_of_rentals DESC,
    rental_revenue DESC,
    total_revenue DESC
```
