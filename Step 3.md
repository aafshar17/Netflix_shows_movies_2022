**Step 3**: **Top Genres for Movies and TV Shows**

Question 7: Which genres have the most movies in this dataset?

```sql
SELECT genres, 
COUNT(*) AS number_of_titles
FROM titles 
WHERE type = 'MOVIE'
GROUP BY genres
ORDER BY number_of_titles DESC
LIMIT 10;
```

![Step 3 Q7 Result](/Step_3_Q7_sql_result.jpg)

Question 8: Which genres have the most TV shows in this dataset?

```sql
SELECT genres, 
COUNT(*) AS number_of_titles
FROM titles 
WHERE type = 'SHOW'
GROUP BY genres
ORDER BY number_of_titles DESC
LIMIT 10;
```

![Step 3 Q8 Result](/Step_3_Q8_sql_result.jpg)

Question 9: What are the top 3 most common genres?

```sql
SELECT genres, 
COUNT(*) AS genre_title_count
FROM titles as t 
WHERE t.type = 'MOVIE' OR t.type = 'SHOW'
GROUP BY genres
ORDER BY genre_title_count DESC
LIMIT 3;
```

![Step 3 Q9 Result](/Step_3_Q9_sql_result.jpg)

The result of the first query shows the top 10 most common movie genres. Comedy ends up being the most popular genre with a total of 384 movies. Not far behind are 
Documentation with 230 movies and Drama with 224 movies. It's also interesting to note that combination of genres feature are quite popular since comedy + documentation 
and comedy + drama are also in the top 5 genres. It's clear that there is a wide, varied selection of movie genres available on the Netflix platform. This reflects its 
commitment to serving the diverse audience that consumes the available content. 

The result of the second query displays the top 10 most common TV show genres. Reality is the most popular with 113 shows and Drama is next with 104 shows. As was the case
with movies, combination of genres such as combinations of genres such as comedy + drama and drama + romance hint at viewer interest in multi-genre shows. 

The result of the third query combines the results of #4 and #5 to give an overview of the top three most common genres overall. Comedy is the most popular 
amongst viewers with 484 entries total and Documentation and Drama are fairly close with 329 and 328 entries respectively. This is important since it showcases the 
platform's efforts to cater to a diverse range of viewer preferences.
