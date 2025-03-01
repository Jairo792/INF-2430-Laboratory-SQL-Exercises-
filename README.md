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
   
   
   
