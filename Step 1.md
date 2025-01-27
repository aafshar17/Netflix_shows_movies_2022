**Step 1**: **Explore the dataset**

Question 1: How many movies are in this dataset?

```sql
SELECT COUNT(*)
FROM titles
WHERE type = 'MOVIE';
```

![Step 1 Q1 Result](/Step_1_Q1_sql_result.jpg)

Question 2: How many TV shows are in this dataset?

```sql
SELECT COUNT(*)
FROM titles
WHERE type = 'SHOW';
```

![Step 1_Q2_Result](/Step_1_Q2_sql_result.jpg)
