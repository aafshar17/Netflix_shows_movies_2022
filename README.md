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

Result:

![worst_10_TV_shows_sql_result](https://github.com/user-attachments/assets/a7c3fd57-30b4-4176-b84a-e58f204d1420)

These top 10 movies and shows stood out for their exceptional IMDB scores, which signals that they are highly regarded by viewers. This means that these particular titles comparatively attained significant praise and number of positive reviews which has propelled them to the top rankings in the Netflix library. Therefore, viewers that want high quality and popular content would likely want to view these movies and they should be marketed as such. In contrast, the worst 10 movies and shows had much lower IMDB scores which signals that audience members did not care for these titles. It would be impossible to know the exact reason simply from the score but some contributing factors could be poor acting, weak plot, individual preferences, or a combination of all of the above. Finding the top 10 and bottom 10 performing content in the library can serve as a solid starting point for further analysis and decision-making for Netflix's audience recommendations system.

# 4. Which genres had the most movies? 

'''sql
SELECT genres, 
COUNT(*) AS number_of_titles
FROM titles 
WHERE type = 'MOVIE'
GROUP BY genres
ORDER BY number_of_titles DESC
LIMIT 10;
'''

Result:

![genre_with_most_movies_sql_result](https://github.com/user-attachments/assets/477f57c7-7bb9-4318-8ffa-5232798a722a)

# 5. WHich genres had the most TV shows?

'''sql
SELECT genres, 
COUNT(*) AS number_of_titles
FROM titles 
WHERE type = 'SHOW'
GROUP BY genres
ORDER BY number_of_titles DESC
LIMIT 10;
'''

Result:

![genre_with_most_TV_shows_sql_result](https://github.com/user-attachments/assets/dddd06f0-2e3d-4d0b-8832-c7892be200f2)

# 6. What are the top 3 most common genres overall?

'''sql
SELECT genres, 
COUNT(*) AS genre_title_count
FROM titles as t 
WHERE t.type = 'MOVIE' OR t.type = 'SHOW'
GROUP BY genres
ORDER BY genre_title_count DESC
LIMIT 3;
'''

Result:

![top_3_genres_sql_result](https://github.com/user-attachments/assets/1600fa27-f26d-4b2e-b142-2525bb222a98)

