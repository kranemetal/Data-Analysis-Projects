# Crypto Currency Trading Analysis using MySQL
# Queries Part  2

### Before we begin working on actual queries for this part..
### Viewing prices table for Bitcoin, sample 5 rows
SELECT * FROM trading.prices WHERE ticker = 'BTC' LIMIT 5;

![image](https://user-images.githubusercontent.com/70786229/149525278-b6670d27-28a0-4955-bfab-3f88ee03891c.png)

### Viewing prices table for Ethereum, sample 5 rows
SELECT * FROM trading.prices WHERE ticker = 'ETH' LIMIT 5;

![image](https://user-images.githubusercontent.com/70786229/149525421-6ff64540-6384-45cd-93d1-815e3deb037f.png)

### Question 1
### How many total records do we have in the trading.prices table?
SELECT COUNT(*) AS total_records FROM prices;

![image](https://user-images.githubusercontent.com/70786229/149525756-7fb4a120-b4f1-4e99-b023-34603f6dbc2c.png)

### Question 2
### How many records are there per ticker value?
SELECT ticker, COUNT(*) AS record_count
FROM prices
GROUP BY ticker; 

![image](https://user-images.githubusercontent.com/70786229/149526356-25686248-14d7-48f1-92f6-55048703cff4.png)

### Question 3
### What is the minimum and maximum market_date values?
SELECT MIN(market_date) AS min_date,
MAX(market_date) AS max_date
FROM prices;
select * FROM prices
LIMIT 1;

![image](https://user-images.githubusercontent.com/70786229/149530686-d890de02-3ec4-4cb7-a91e-9fb423f70049.png)

### Question 4
### Are there differences in the minimum and maximum market_date values for each ticker?
SELECT ticker, MIN(market_date) AS min_date,
MAX(market_date) AS max_date
FROM prices
GROUP BY ticker;
##### Min and Max date for both are same

![image](https://user-images.githubusercontent.com/70786229/149532377-ab75dfe9-90c2-448f-9e4e-c794ddd13093.png)

### Question 5
### What is the average of the price column for Bitcoin records during the year 2020?
SELECT AVG(price) as bitcoin_avg_price_2020
FROM prices
WHERE ticker = 'BTC' 
AND market_date BETWEEN ('2020-01-01') and ('2020-12-31');

![image](https://user-images.githubusercontent.com/70786229/149539773-ca812134-bdfd-468f-80b9-5516f25c780b.png)

### Question 6
### What is the monthly average of the price column for Ethereum in 2020?
### Sort the output in chronological order and also round the average price value to 2 decimal places
-- working on solution

### Question 7
### Are there any duplicate market_date values for any ticker value in our table?
SELECT ticker,
COUNT(market_date) AS total_records,
COUNT(DISTINCT market_date) AS unique_records
FROM prices
GROUP BY ticker;

![image](https://user-images.githubusercontent.com/70786229/149547881-a8f9ba3b-f48d-4f53-af6e-53fa68ae0026.png)

### Question 8
### How many days from the trading.prices table exist where the high price of Bitcoin is over $30,000?
SELECT COUNT(market_date) as no_days
FROM prices
WHERE ticker = 'BTC'
AND high >30000;

![image](https://user-images.githubusercontent.com/70786229/149555593-c3059365-87df-44df-bf8e-e49786b409ab.png)

### Question 9
### How many "breakout" days were there in 2020 where the price column is greater than the open column for each ticker?
SELECT ticker,
COUNT(*)
FROM prices
WHERE market_date BETWEEN ('2020-01-01') and ('2020-12-31')
AND price > open
GROUP BY ticker;

![image](https://user-images.githubusercontent.com/70786229/149556245-26c18f03-24ff-4f21-b295-8163f86a4cb1.png)

### Question 10
### How many "non_breakout" days were there in 2020 where the price column is less than the open column for each ticker?
SELECT ticker,
COUNT(*) AS non_breakout_days
FROM prices
WHERE market_date BETWEEN ('2020-01-01') and ('2020-12-31')
AND price < open
GROUP BY ticker;

![image](https://user-images.githubusercontent.com/70786229/149556513-d109b8b1-2842-4dbd-a065-e886d198f292.png)

### Question 11
### What percentage of days in 2020 were breakout days vs non-breakout days? Round the percentages to 2 decimal places
-- Working on solution

