What issues will you address by cleaning the data?

Type errors
Incosistent data
Undefined data
Unnessary column
Address Missing values

Queries:
Below, provide the SQL queries you used to clean your data.

--Drop Sentimentsore and sentimentmagnitude From product Table due to Unwanted or Irrelevant Observations
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
ALTER TABLE analytics 
ALTER COLUMN timeonsite TYPE integer USING (timeonsite::integer);

--Drop Userid From analytics table due to NULL values
ALTER TABLE analytics
DROP COLUMN userid;

--UPDATE analytics table to convert NULL values to zero values on units_sold
UPDATE analytics
SET units_sold = 0
WHERE units_sold IS NULL;


-- Convert visitstatrttime column to TO_Timestamp data type
ALTER TABLE analytics
ALTER COLUMN visitstarttime TYPE timestamp
USING To_timestamp(visitstarttime);

--Convert Timeonsite to Integer
ALTER TABLE analytics ALTER COLUMN timeonsite TYPE integer USING (timeonsite::integer);

--Drop socialengagementtype From analytics table
ALTER TABLE analytics
DROP COLUMN socialengagementtype
--Drop transactionid and itemrevenue From all_sessions table
ALTER TABLE all_sessions
DROP COLUMN transactionid

ALTER TABLE all_sessions
DROP COLUMN itemrevenue

--Convert varchar to Numeric data types
ALTER TABLE all_sessions 
ALTER COLUMN totaltransactionrevenue 
SET DATA TYPE numeric
USING totaltransactionrevenue::numeric

--Convert Null with 0 for revenue from analytics
UPDATE analytics
SET revenue = 0
WHERE revenue IS NULL
