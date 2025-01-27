**Step 4**: **Number of Movies and TV Shows by Decade**

Question 10: How many of Netflix's offered movies and TV shows are in each decade?

```sql
SELECT CONCAT(FLOOR(release_year/ 10) * 10, 's') AS decade,
COUNT(*) AS movies_shows_count
FROM titles
WHERE release_year >= 1940
GROUP BY CONCAT(FLOOR(release_year/ 10) * 10, 's')
ORDER BY decade;
```

![Step 4 Q10 Result](/Step_4_Q10_sql_result.jpg)

Examining this query's result provides valuable insight into the distribution of movies and shows across different decades in Netflix's 
library. There is a sizeable increase in the number of titles from the 2000s onwards. Netflix's collection from the earlier decades 
(1940s - 1980s) is clearly limited. The collection from the 1990s highlights an increase with 121 titles offered. The inflection point 
in the platform's offered content is present in the 2010s with a whopping combined 3,304 movies and shows from this decade. The 2020s 
offered content is still in progress yet still has a combined 1,972 movies and shows. This significant increase in content availability 
from the 2000s onwards indicates that there is a management-directed effort to offer a diverse selection of titles to their audience.
