# SQL Exercises LABO INF 2430
 These are the SQL query exercises done in the LAB class - INF2430.
 ---
 ## **1. SQL INTRO**
 - **Exercise INTRO 1** :
 ```
 SELECT user_id, stars FROM reviews WHERE stars =3;
 ```
 ## **2. SQL SELECT**
  - **Exercise SELECT 1:**
   Your given a products table, which contains data about different Microsoft Azure cloud products.
   Solution:
  ```
  SELECT * FROM products;
  ```
 ## **3. SQL WHERE**
  - **Exercise WHERE 1:**
  Given the reviews table, write a query to retrieve all 3-star reviews using the SQL WHERE clause. Only display the user_id and stars columns. 
  Solution:
  ```
  SELECT user_id, stars FROM reviews WHERE stars =3;
  ```
 ## **4. SQL AND,OR,NOT**
  - **Exercise AND,OR,NOT 1:**
  Let's practice using AND along with WHERE to filter Amazon reviews based on all 4 of these conditions:
   the review should have 4 or more stars
   the review ID is less than 6000
   the review ID is more than 2000
   the review can't come from user 142
   
   Solution:
   ```
   SELECT * FROM reviews WHERE stars >= 4 AND review_id < 6000 AND review_id > 2000 AND user_id != 142;
   ```
  - **Exercise AND,OR,NOT 2:**
  Let's practice using AND along with WHERE to filter Amazon reviews based on these two conditions:
   the start count is greater than 2, and less than or equal to 4
   the review must come from either user 123, 265, or 362
   
   Solution:
   ```
   SELECT * FROM reviews WHERE user_id = 123 OR user_id = 265 OR user_id = 362 AND stars > 2 AND stars  <= 4;
   ```
 ## **5. SQL BETWEEN**
  - **Exercise BETWEEN 1:**
  Imagine you are a Data Analyst working at CVS Pharmacy, and you had access to pharmacy sales data. Use the BETWEEN SQL command to find data on medicines:
  
   which sold between 100,000 units and 105,000 units 
   AND were manufactured by either Biogen, AbbVie, or Eli Lilly
   Output the manufacturer name, drug name, and the # of units sold.
   
   Solution:
   ```
   SELECT manufacturer, drug, units_sold FROM pharmacy_sales WHERE( manufacturer = 'Biogen' OR manufacturer = 'AbbVie' OR manufacturer = 'Eli Lilly') AND ( units_sold BETWEEN 100000 AND 105000);
   ```
 ## **6. SQL IN**
  - **Exercise IN 1:**
  Imagine you are a Data Analyst working at CVS Pharmacy, and you had access to pharmacy sales data. Use the IN SQL command to find data on medicines:

   which were manufactured by either Roche, Bayer, or AstraZeneca
   and did not sell between 55,000 and 550,000 units
   Output the manufacturer name, drug name, and the # of units sold. for all the medicines which match that criteria.
  
   Solution:
   ```
   SELECT manufacturer, drug, units_sold FROM pharmacy_sales WHERE ( manufacturer IN ('Roche', 'Bayer','AstraZeneca')) AND (NOT( units_sold BETWEEN 55000 AND 550000));
   ```
 ## **7. SQL LIKE**
  - **Exercise LIKE 1:**  
  You have a table of 1000 customer records from a small-business based in Australia.
  Find all customers whose first name starts with "F" and the last letter in their last name is "ck".
  
  
  Solution:
   ```
    SELECT * FROM customers WHERE customer_name LIKE 'F%ck';
   ```
  - **Exercise LIKE 2:**
  You have a table of 1000 customer records from a small-business based in Australia.
  Find all customers where the 2nd and 3rd letter in their name is "e". 

  
  Solution:
   ```
    SELECT * FROM customers WHERE customer_name LIKE ('_ee%');
   ```
 ## **8. SQL FILTERING REVIEW**
  - **Exercise FILTERING REVIEW 1:** 
  You have a table of 1000 customer records from a small-business based in Australia.
  Find all customers who are between the ages of 18 and 22 (inclusive), live in either Victoria, Tasmania, Queensland, their gender isn't "n/a", and their name starts with either 'A' or 'B'.


  Solution:
  ```
   SELECT * FROM customers WHERE (state IN('Victoria' , 'Tasmania', 'Queensland'))  AND (age BETWEEN 18 AND 22) AND (gender != 'n/a') AND ( (customer_name LIKE ('A%')) OR ( customer_name LIKE ('B%')));
  ```
