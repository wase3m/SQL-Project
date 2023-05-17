Question 1: 

SQL Queries:

 Which countries do we get the most visiors from visitors?
SELECT 
    country,
    COUNT(fullvisitorid) as num_visitor
FROM all_sessions
GROUP BY country
ORDER BY num_visitor DESC
Limit 3

Answer: 

Top 3 are :



Question 2: 

SQL Queries:

Answer:



Question 3: 

SQL Queries:

Answer:



Question 4: 

SQL Queries:

Answer:



Question 5: 

SQL Queries:

Answer:
