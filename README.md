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





