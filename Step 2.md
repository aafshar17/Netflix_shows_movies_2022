**Step 2**: **Top 10 and Worst 10 Movies and TV Shows**

Question 3: What are the top 10 movies based on IMDB score?

```sql
SELECT title, type, imdb_score
FROM titles
WHERE type = 'MOVIE' AND imdb_score >= 8.0
ORDER BY imdb_score DESC
LIMIT 10;
```

![Step 2 Q3 Result](/Step_2_Q3_sql_result.jpg)

Question 4: What are the worst 10 movies based on IMDB score?

```sql
SELECT title, type, imdb_score
FROM titles
WHERE type = 'MOVIE'
ORDER BY imdb_score ASC
LIMIT 10;
```

![Step 2 Q4 Result](/Step_2_Q4_sql_result.jpg)

Question 5: What are the top 10 TV shows based on IMDB score?

```sql
SELECT title, type, imdb_score
FROM titles
WHERE type = 'SHOW' AND imdb_score >= 8.0
ORDER BY imdb_score DESC
LIMIT 10;
```

![Step 2 Q5 Result](/Step_2_Q5_sql_result.jpg)

Question 6: What are the worst 10 TV shows based on IMDB score?

```sql
SELECT title, type, imdb_score
FROM titles
WHERE type = 'SHOW'
ORDER BY imdb_score ASC
LIMIT 10;
```

![Step 2 Q6 Result](/Step_2_Q6_sql_result.jpg)

These top 10 movies and shows stood out for their exceptional IMDB scores, which signals that they are highly regarded by viewers. This means that these particular titles comparatively attained significant praise and number of positive reviews which has propelled them to the top rankings in the Netflix library. Therefore, viewers that want high quality and popular content would likely want to view these movies and they should be marketed as such. In contrast, the worst 10 movies and shows had much lower IMDB scores which signals that audience members did not care for these titles. It would be impossible to know the exact reason simply from the score but some contributing factors could be poor acting, weak plot, individual preferences, or a combination of all of the above. Finding the top 10 and bottom 10 performing content in the library can serve as a solid starting point for further analysis and decision-making for Netflix's audience recommendations system.
