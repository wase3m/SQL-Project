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
US
India 
Canada



Question 2: 

What channelgrouping drives in most sales?

SQL Queries:

Answer:
Top 3 are 
Referral, Referral and Organic Search

SELECT
    als.country,
    als.channelgrouping,
    revenue
FROM all_sessions as als
JOIN analytics
USING (visitid)
GROUP BY als.country, als.channelgrouping, revenue
ORDER BY revenue DESC

Question 3: 

Which is the most ordered product?

Answer: 22oz water bottle

SELECT 
    sku,
    name,
    orderedquantity
FROM products
ORDER BY stocklevel DESC


Question 4: 

 Which is the most expensive product we have?
 
SELECT 
    v2productname,
    unit_price
FROM analytics
JOIN all_sessions USING(visitid)
ORDER BY unit_price DESC
Limit 100
SQL Queries:

Answer:
Lip balm SPF15


Question 5: 

SQL Queries:

Answer:
