NULL Checks
```sql
SELECT name, role FROM employees WHERE building IS NULL;
SELECT * from buildings LEFT JOIN employees ON building_name=building WHERE building IS NULL;
```
___
Expressions in query
```sql
SELECT title, 
(domestic_sales + international_sales) / 1000000 AS gross_sales_millions 
FROM movies JOIN boxoffice 
ON movies.id = boxoffice.movie_id;
```
```sql
SELECT title, rating * 10 AS rating_percent
FROM movies JOIN boxoffice
ON movies.id = boxoffice.movie_id;
```
```sql
SELECT title, (year%2) AS even_year
FROM movies JOIN boxoffice
ON movies.id = boxoffice.movie_id
WHERE even_year = 0;
```
___

Aggregates Functions
Find the longest time that an employee has been at the studio
```sql
SELECT MAX(years_employed) FROM employees;
```
For each role, find the average number of years employed by employees in that role
```sql
SELECT role, AVG(years_employed)FROM employees GROUP BY role;
```
Find the total number of employee years worked in each building
```sql
SELECT building, SUM(years_employed) AS Total_Years
FROM employees 
GROUP BY building;
```
Find the number of Artists in the studio (without a **HAVING** clause
```sql
SELECT role, COUNT(*) as Number_of_artists
FROM employees
WHERE role = "Artist";
```
Find the number of Employees of each role in the studio
```sql
SELECT role, COUNT(*) as Number_of_artists
FROM employees GROUP BY Role;
```
Find the total number of years employed by all Engineers
```sql
SELECT role, SUM(years_employed) AS total_years 
FROM employees 
GROUP BY Role HAVING role="Engineer";
```
___

ORDER OF EXECUTION
1. `FROM` and `JOIN`s
2. `WHERE`
3. `GROUP BY`
4.  `HAVING`
5.  `SELECT`
6.  `DISTINCT`
7.  `ORDER BY`
8. `LIMIT` / `OFFSET`
___
Find the number of movies each director has directed
```sql
SELECT Title, Director, COUNT(*) AS Number_of_movies 
FROM movies GROUP BY director 
ORDER BY Number_of_movies DESC;
```
Find the total domestic and international sales that can be attributed to each director
```sql
SELECT director, 
SUM(domestic_sales + international_sales) as 
Cumulative_sales_from_all_movies
FROM movies INNER JOIN boxoffice ON id = movie_id
GROUP BY director;
```
___
