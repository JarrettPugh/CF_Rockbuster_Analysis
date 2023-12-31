This SQL query returns all countries, the number of customers, and the total revenue earned from each country ordered by total revenue

Here is the SQL query:

```sql
SELECT
    E.country,
    COUNT(DISTINCT B.customer_id) AS customer_numbers,
    SUM(A.amount) AS revenue_amount
FROM
    payment A
    INNER JOIN customer B ON A.customer_id = B.customer_id
    INNER JOIN address C ON B.address_id = C.address_id
    INNER JOIN city D ON C.city_id = D.city_id
    INNER JOIN country E ON D.country_id = E.country_id
GROUP BY
    E.country
ORDER BY
    revenue_amount DESC
```
