**Step 6**: **Release Year 2019 Deeper Dive**

Question 13: For release year 2019, which genre had the most titles released?

```sql
SELECT genres, title, COUNT(*) as title_count
FROM titles as t
WHERE release_year = '2019'
GROUP BY genres
ORDER BY title_count DESC
LIMIT 1;
```

![Step 6 Q13 Result](/Step_6_Q13_sql_result.jpg)

Question 14: What were the titles and types for the titles in this genre released in 2019?

```sql
SELECT title, type
FROM titles as t
WHERE release_year = '2019' AND t.genres IN
(SELECT genres
FROM titles as t
WHERE release_year = '2019'
GROUP BY genres
ORDER BY COUNT(title) DESC
LIMIT 1)
ORDER BY title ASC; 
```

![Step 6 Q14 Result](/Step_6_Q14_sql_result.jpg)

The comedy genre had the most titles in 2019 with 79 total titles released. This validates our early finding that 
the Comedy genre is overall the most popular genre on Netflix.   

Question 15: Which of the titles in the Comedy genre for 2019 had the highest IMDB score?

```sql
SELECT title, imdb_score
FROM titles
WHERE release_year = 2019
AND SUBSTRING(genres,3,6) = 'comedy' 
AND SUBSTRING(genres,10,2) = ']' 
AND imdb_score IS NOT NULL
ORDER BY imdb_score DESC
LIMIT 1;
```

![Step 6 Q15 Result](/Step_6_Q15_sql_result.jpg)

Dave Chappelle's comedy special Sticks & Stones had the highest IMDB score with a score of 8.4 for the 
Comedy titles released in 2019. 

