This SQL query returns the min, max, and avg of all quantitative fields and the mode of all qualitative fields of the film table.

Here is the SQL query:

```sql
SELECT	
	MIN(rental_duration) AS min_rental_duration,
	MAX(rental_duration) AS max_rental_duration,
	AVG(rental_duration) AS avg_rental_duration,
	MIN(rental_rate) AS min_rental_rate,
	MAX(rental_rate) AS max_rental_rate,
	AVG(rental_rate) AS avg_rental_rate,
	MIN(length) AS min_length,
	MAX(length) AS max_length,
	AVG(length) AS avg_length,
	MIN(replacement_cost) AS min_replacement_cost,
	MAX(replacement_cost) AS max_replacement_cost,
	AVG(replacement_cost) AS avg_replacement_cost,
	MODE() WITHIN GROUP (ORDER BY film_id) AS modal_film_id_value,
	MODE() WITHIN GROUP (ORDER BY title) AS modal_title_value,
	MODE() WITHIN GROUP (ORDER BY description) AS modal_description_value,
	MODE() WITHIN GROUP (ORDER BY release_year) AS modal_release_year_value,
	MODE() WITHIN GROUP (ORDER BY language_id) AS modal_language_id_value,
	MODE() WITHIN GROUP (ORDER BY rating) AS modal_rating_value,
	MODE() WITHIN GROUP (ORDER BY last_update) AS modal_last_update_value,
	MODE() WITHIN GROUP (ORDER BY special_features) AS modal_special_features_value,
	MODE() WITHIN GROUP (ORDER BY fulltext) AS modal_fulltext_value
FROM film	
```
