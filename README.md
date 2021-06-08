| Id  | Title        | Director       | Year | Length |
| --- | ------------ | -------------- | ---- | ------ |
| 1   | Toy Story    | John Lasseter  | 1995 | 81     |
| 2   | Finding Nemo | Andrew Stanton | 2003 | 107    |
| 3   | Ratatouille  | Brad Bird      | 2007 | 115    |

---

SELECT
SELECT statement returns data from the table

```sql
SELECT title FROM movies;
SELECT director FROM movies;
SELECT title, director FROM movies;
SELECT title, year FROM movies;
SELECT * FROM movies;
```

---

WHERE
WHERE clause helps to filter the data returned from the table

```sql
SELECT id, title FROM movies  WHERE id = 6;
SELECT title, year FROM movies WHERE year BETWEEN 2000 AND 2010;
SELECT title, year FROM movies WHERE year < 2000 OR year > 2010;
SELECT title, year FROM movies WHERE year <= 2003;
SELECT title, year FROM movies WHERE year <= 2003;
SELECT title, director FROM movies  WHERE director = "John Lasseter";
SELECT title, director FROM movies  WHERE director != "John Lasseter";
SELECT * FROM movies WHERE title LIKE "WALL-%";
```

---

ORDER BY
It orders the column alphabetically by ascending or descending order

```sql
SELECT Director FROM movies ORDER BY director ASC;

SELECT Title FROM movies ORDER BY director DESC;
```

---

Distinct
Removes duplicate rows from the result

```sql
SELECT DISTINCT Year From movies;
```

---

LIMIT & OFFSET
Limits the number of result returned from the table
Offset will specify where to begin counting the number rows from.

```sql
SELECT * from movies LIMIT 5;

SELECT * from movies ORDER BY Title ASC LIMIT 5;

SELECT * from movies ORDER BY Year DESC LIMIT 5;

SELECT DISTINCT year from movies ORDER BY Title ASC LIMIT 5;

SELECT title FROM movies ORDER BY title ASC LIMIT 5 OFFSET 5;
```

---

| City        | Country       | Population | Latitude  | Longitude   |
| ----------- | ------------- | ---------- | --------- | ----------- |
| Guadalajara | Mexico        | 1500800    | 20.659699 | -103.349609 |
| Toronto     | Canada        | 2795060    | 43.653226 | -79.383184  |
| Houston     | United States | 2195914    | 29.760427 | -95.369803  |
| Havana      | Cuba          | 2106146    | 23.05407  | -82.345189  |

List all the Canadian cities and their populations

```sql
SELECT * FROM north_american_cities WHERE country = "Canada"
```

Order all the cities in the United States by their latitude from north to south

```sql
SELECT * FROM north_american_cities WHERE country = "United States" ORDER BY Latitude DESC;
```

List all the cities west of Chicago, ordered from west to east

```sql
SELECT city, longitude FROM north_american_cities WHERE longitude < -87.629798 ORDER BY longitude ASC;
```

List the two largest cities in Mexico (by population)

```sql
SELECT * FROM north_american_cities WHERE Country="Mexico" ORDER BY Population DESC LIMIT 2;
```

List the third and fourth largest cities (by population) in the United States and their population

```sql
SELECT * FROM north_american_cities WHERE Country="United States" ORDER BY Population DESC LIMIT 2 OFFSET 2;
```

---

JOIN
combines row data across two separate tables using this unique key

```sql
SELECT
bld.*, emp.years_employed FROM buildings AS bld LEFT JOIN employees AS emp ON bld.building_name = emp.building;
```

Find the domestic and international sales for each movie

```sql
SELECT * FROM movies INNER JOIN BoxOffice on movies.id = BoxOffice.Movie_id ORDER BY id;
```

Show the sales numbers for each movie that did better internationally rather than domestically

```sql
SELECT * FROM movies INNER JOIN BoxOffice on movies.id = BoxOffice.Movie_id WHERE domestic_sales < international_sales ORDER BY international_sales DESC;
```

List all the movies by their ratings in descending order

```sql
SELECT * FROM movies INNER JOIN BoxOffice on movies.id = BoxOffice.Movie_id ORDER BY rating DESC;
```

---
