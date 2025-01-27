**Step 5**: **Release Year - Number of Titles and which one has the most titles**

Question 11: What were the total number of titles for each release year?

```sql
SELECT release_year, 
COUNT(*) AS title_count
FROM titles as t 
GROUP BY release_year
ORDER BY release_year DESC
```

![Step 5 Q11 Result](/Step_5_Q11_sql_result.jpg)

Question 12: Which release year had the greatest number of titles? 

```sql
SELECT release_year, 
COUNT(*) AS title_count
FROM titles as t 
GROUP BY release_year
ORDER BY title_count DESC
LIMIT 1;
```

![Step 5 Q12 Result](/Step_5_Q12_sql_result.jpg)

We can see that the year 2019 had the greatest number of titles released with 836 combined movie and TV show titles. Let's examine this release year 2019 in more detail now
such as which genre had the most titles and which titles along with their respective types were classified in this genre. 
