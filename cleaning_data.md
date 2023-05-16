What issues will you address by cleaning the data?

Type errors
Incosistent data
Undefined data
Unnessary column
Address Missing values

Queries:
Below, provide the SQL queries you used to clean your data.

--Drop  Sentimentsore and sentimentmagnitude From product Table due to Unwanted or Irrelavent Observations
ALTER TABLE products
DROP COLUMN sentimentscore;

ALTER TABLE products
DROP COLUMN sentimentmagnitude;

--Drop Userid From analytics table due to NULL values
ALTER TABLE analytics
DROP COLUMN userid;

--UPDATE analytics table to convert NULL values to zero values on units_sold
UPDATE analytics
SET units_sold = 0
WHERE units_sold IS NULL;

-- Convert visitstatrttime column  to TO_Timestamp data type
ALTER TABLE analytics
ALTER COLUMN visitstarttime TYPE timestamp
USING To_timestamp(visitstarttime);

--Convert Timeonsite to Integer
ALTER TABLE analytics ALTER COLUMN timeonsite TYPE integer USING (timeonsite::integer);

--Drop socialengagementtype From analytics table
ALTER TABLE analytics
DROP COLUMN socialengagementtype

--Drop rows where country or/and city are '(not set)' or 'not available in demo dataset' from all_sessions table

DELETE FROM all_sessions
WHERE city = 'not available in demo dataset'

DELETE FROM all_sessions
WHERE city = '(not set)'

DELETE FROM all_sessions
WHERE country = '(not set)'

-- DROP transactionid from all_sessions due to NULL value
ALTER TABLE all_sessions
DROP COLUMN transactionid

-- DROP itemrevenue from all_sessions due to NULL value
ALTER TABLE all_sessions
DROP COLUMN itemrevenue

-- Divide unit_price/1000000 as per instructions
select 
CAST((unit_price / 1000000.) AS DECIMAL (10,2))
from analytics


