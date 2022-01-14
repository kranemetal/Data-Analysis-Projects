# Crypto Currency Trading Analysis using MySQl
The schema consists of single database trading and three tables members, prices and transactions. <br>
Before beginning the project and running actual queries let us view the databases by running basic queries with LIMIT of 5 records. <br>
#### Members Table
SELECT * FROM members
LIMIT 5;

![image](https://user-images.githubusercontent.com/70786229/149507054-9e2a062a-3d70-46b4-a329-08b40a72a141.png)

#### Prices Table
SELECT * FROM prices
LIMIT 5;

![image](https://user-images.githubusercontent.com/70786229/149507226-e6a76852-97a6-458e-b97f-ab9a8fb44e7d.png)

#### Transactions Table
SELECT * FROM transactions
LIMIT 5;

![image](https://user-images.githubusercontent.com/70786229/149507426-1887e8aa-5428-48cd-b559-6f2841bfb9a3.png)

# Queries Part 1

### Question 1 
### Show only the top 5 rows from the trading.members table
SELECT * FROM members
LIMIT 5;

![image](https://user-images.githubusercontent.com/70786229/149512242-c4ff1dc9-af9e-4c4f-a8b3-5b65f9ca3c00.png)

### Question 2
### Sort all the rows in the table by first_name in alphabetical order and show the top 3 rows
SELECT * FROM members
ORDER BY first_name
LIMIT 3;

![image](https://user-images.githubusercontent.com/70786229/149512560-78c2f157-00ac-4e93-86a2-56b8bcd521f7.png)

### Question 3
### Which records from trading.members are from the United States region?
SELECT * FROM members
WHERE region = 'United States';

![image](https://user-images.githubusercontent.com/70786229/149512779-644ddfdd-6784-42e8-84e9-3f0c84a37cb3.png)

### Question 4
### Select only the member_id and first_name columns for members who are not from Australia
SELECT member_id, first_name FROM members
WHERE region != 'Australia';

![image](https://user-images.githubusercontent.com/70786229/149515129-fc4a5c18-03de-45b8-8e28-a4dcae380759.png)

### Question 5
### Return the unique region values from the trading.members table and sort the output by reverse alphabetical order
SELECT DISTINCT region FROM members
ORDER by region DESC;

![image](https://user-images.githubusercontent.com/70786229/149515376-3281068b-062c-42cc-a72d-90c8033c947c.png)

### Question 6
### How many mentors are there from Australia or the United States?
SELECT COUNT(*) AS mentor_count FROM members
WHERE region IN ('Australia', 'United States');

![image](https://user-images.githubusercontent.com/70786229/149518549-9c2a14ff-466b-4b6a-8556-74c59abbcaaa.png)

### Question 7
### How many mentors are not from Australia or the United States?
SELECT COUNT(*) AS mentor_count FROM members
WHERE region NOT IN ('Australia', 'United States');

![image](https://user-images.githubusercontent.com/70786229/149519035-da74466b-4a3c-4a0d-82dc-a3c9d65ed479.png)

### Question 8
### How many mentors are there per region? Sort the output by regions with the most mentors to the least
SELECT region, COUNT(*) AS mentor_count
FROM members
GROUP BY region
ORDER BY mentor_count DESC;

![image](https://user-images.githubusercontent.com/70786229/149519954-77c09368-0449-45a5-9cfe-f1110e8c5376.png)

### Question 9
### How many US mentors and non US mentors are there?
SELECT
	CASE
	WHEN region !='United States' THEN 'Non US'
	ELSE region
	END AS mentor_region,
COUNT(*) AS mentor_count
FROM members
GROUP BY mentor_region
ORDER BY mentor_count DESC;

![image](https://user-images.githubusercontent.com/70786229/149523282-4958211d-5435-4839-8236-36ed343e64bf.png)

### Question 10
### How many mentors have a first name starting with a letter before 'E'?
SELECT COUNT(*) AS mentor_count
FROM members
WHERE LEFT(first_name, 1) < 'E';

![image](https://user-images.githubusercontent.com/70786229/149523702-79e26046-4837-4ea3-9041-0d960e43dfa2.png)



