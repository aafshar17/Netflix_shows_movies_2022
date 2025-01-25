# **Netflix_shows_movies_2022**

# **Languages/Tools used**: PostgreSQL, Power Query, Power BI (Visuals and Dashboard) 
# [Datasets referenced](https://www.kaggle.com/datasets/victorsoeiro/netflix-tv-shows-and-movies?select=titles.csv)
# PostgreSQL Data Analysis Code
# Netflix Shows and Movies Power BI Dashboard 

* Purpose of this analysis: Devise a scalable and high-quality analytical method to accomodate this extensive amount of data (over 80k rows of data in combined datasets). PostgreSQL and Power BI Visuals are being used to pull out meaningful information and present them in an easy to understand format using a mobile-friendly Power BI Dashboard. Key metrics including but not limited to genre preferences, movie rankings, viewership patterns, viewer ratings, and top actors/actresses can be explored using SQL queries and subqueries as needed. Power BI Service's dashboard sharing feature is particularly useful since it enables interactive exploration of the data which allows Netflix stakeholders to pursue actionable insights via visually appealing charts, graphs, and interactive data visualizations.

# <ins> Questions to explore based on this Netflix Movies and TV Shows Dataset  </ins>

# 1. How many movies and shows are in this dataset?
```sql 
SELECT COUNT(*) AS movie_count
FROM titles
WHERE type = 'MOVIE';
```

Result: 

![movie_count_sql_result](https://github.com/user-attachments/assets/5caf77f0-ab3a-43ca-a4ac-1f586ba59ccd)

```sql 
SELECT COUNT(*) AS TV_show_count
FROM titles
WHERE type = 'SHOW';
```

![TV_show_count_sql_result](https://github.com/user-attachments/assets/4e352ae8-1534-4a63-b208-28130eecb67a)

There are 3,744 movies and 2,106 TV shows present in this dataset. 

# 2. What are the top 10 and worst 10 movies based on IMDB score?

```sql 
SELECT title, type, imdb_score
FROM titles
WHERE type = 'MOVIE' AND imdb_score >= 8.0
ORDER BY imdb_score DESC
LIMIT 10;
```

Result: 

![top_10_movies_sql_result](https://github.com/user-attachments/assets/61339d08-79b7-4174-badc-96aede118b8c)

```sql 
SELECT title, type, imdb_score
FROM titles
WHERE type = 'MOVIE'
ORDER BY imdb_score ASC
LIMIT 10;
```

Result:

![worst_10_movies_sql_result](https://github.com/user-attachments/assets/9fbabaf1-0c09-4d7d-999f-42c20b455639)

# 3. What are the top 10 and worst 10 TV shows based on IMDB score?

```sql 
SELECT title, type, imdb_score
FROM titles
WHERE type = 'SHOW' AND imdb_score >= 8.0
ORDER BY imdb_score DESC
LIMIT 10;
```

Result:

![top_10_TV_shows_sql_result](https://github.com/user-attachments/assets/25f8bc9a-317e-4032-bd47-5f9d8bb9fec2)

```sql 
SELECT title, type, imdb_score
FROM titles
WHERE type = 'SHOW'
ORDER BY imdb_score ASC
LIMIT 10;
```

Result:

![worst_10_TV_shows_sql_result](https://github.com/user-attachments/assets/a7c3fd57-30b4-4176-b84a-e58f204d1420)

These top 10 movies and shows stood out for their exceptional IMDB scores, which signals that they are highly regarded by viewers. This means that these particular titles comparatively attained significant praise and number of positive reviews which has propelled them to the top rankings in the Netflix library. Therefore, viewers that want high quality and popular content would likely want to view these movies and they should be marketed as such. In contrast, the worst 10 movies and shows had much lower IMDB scores which signals that audience members did not care for these titles. It would be impossible to know the exact reason simply from the score but some contributing factors could be poor acting, weak plot, individual preferences, or a combination of all of the above. Finding the top 10 and bottom 10 performing content in the library can serve as a solid starting point for further analysis and decision-making for Netflix's audience recommendations system.

# 4. Which genres had the most movies? 

```sql 
SELECT genres, 
COUNT(*) AS number_of_titles
FROM titles 
WHERE type = 'MOVIE'
GROUP BY genres
ORDER BY number_of_titles DESC
LIMIT 10;
``` 

Result:

![genre_with_most_movies_sql_result](https://github.com/user-attachments/assets/477f57c7-7bb9-4318-8ffa-5232798a722a)

# 5. Which genres had the most TV shows?

```sql
SELECT genres, 
COUNT(*) AS number_of_titles
FROM titles 
WHERE type = 'SHOW'
GROUP BY genres
ORDER BY number_of_titles DESC
LIMIT 10;
```

Result:

![genre_with_most_TV_shows_sql_result](https://github.com/user-attachments/assets/dddd06f0-2e3d-4d0b-8832-c7892be200f2)

# 6. What are the top 3 most common genres overall?

```sql
SELECT genres, 
COUNT(*) AS genre_title_count
FROM titles as t 
WHERE t.type = 'MOVIE' OR t.type = 'SHOW'
GROUP BY genres
ORDER BY genre_title_count DESC
LIMIT 3;
```

Result:

![top_3_genres_sql_result](https://github.com/user-attachments/assets/1600fa27-f26d-4b2e-b142-2525bb222a98)

The first query in #4 shows the top 10 most common movie genres. Comedy ends up being the most popular genre with a total of 384 movies. Not far behind are Documentation with 230 movies and Drama with 224 movies. It's also interesting to note that combination of genres feature are quite popular since comedy + documentation and comedy + drama are also in the top 5 genres. It's clear that there is a wide, varied selection of movie genres available on the Netflix platform. This reflects its commitment to serving the diverse audience that consumes the available content. 

The second query in #5 displays the top 10 most common TV show genres. Reality is the most popular with 113 shows and Drama is next with 104 shows. As was the case with movies, combination of genres such as combinations of genres such as comedy + drama and drama + romance hint at viewer interest in multi-genre shows. 

The third query in #6 combines the results of #4 and #5 to give an overview of the top three most common genres overall. Comedy is the most popular amongst viewers with 484 entries total and Documentation and Drama are fairly close with 329 and 328 entries respectively. This is important since it showcases the platform's efforts to cater to a diverse range of viewer preferences. 

# 7. How many of Netflix's offered movies and TV shows are in each decade?

```sql
SELECT CONCAT(FLOOR(release_year/ 10) * 10, 's') AS decade,
COUNT(*) AS movies_shows_count
FROM titles
WHERE release_year >= 1940
GROUP BY CONCAT(FLOOR(release_year/ 10) * 10, 's')
ORDER BY decade;
```

Result:

![Netflix_content_in_each_decade_sql_result](https://github.com/user-attachments/assets/52519441-3c48-4d51-89d4-3fb44977c796)

Examining this query's result provides valuable insight into the distribution of movies and shows across different decades in Netflix's library. There is a sizeable increase in the number of titles from the 2000s onwards. Netflix's collection from the earlier decades (1940s - 1980s) is clearly limited. The collection from the 1990s highlights an increase with 121 titles offered. The inflection point in the platform's offered content is present in the 2010s with a whopping combined 3,304 movies and shows from this decade. The 2020s offered content is still in progress yet still has a combined 1,972 movies and shows. This significant increase in content availability from the 2000s onwards indicates that there is a management-directed effort to offer a diverse selection of titles to their audience. 

# 8. What were the total number of titles for each release year? 

```sql
SELECT CONCAT(FLOOR(release_year/ 10) * 10, 's') AS decade,
COUNT(*) AS movies_shows_count
FROM titles
WHERE release_year >= 1940
GROUP BY CONCAT(FLOOR(release_year/ 10) * 10, 's')
ORDER BY decade;
```

Result:

![titles_total_per_release_year_result](https://github.com/user-attachments/assets/a128defc-bce3-4a92-b124-c030cecf7906)

Which leads to a natural follow-up question of... 

# 9. Which release year had the greatest number of titles?

```sql
SELECT release_year, 
COUNT(*) AS title_count
FROM titles as t 
GROUP BY release_year
ORDER BY title_count DESC
LIMIT 1;
```

Result:

![release_year_with_most_titles_result](https://github.com/user-attachments/assets/b6318c32-bdac-437c-9b08-c9fdffaaf250)

We can see that the year 2019 had the greatest number of titles released with 836 combined movie and TV show titles. 
