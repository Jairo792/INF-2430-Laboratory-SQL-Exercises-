# SQL Exercises LABO INF 2430
 ## SQL BASICS
 These are the SQL query exercises done in the LAB class - INF2430.
 ---
 ### **1. SQL INTRO**
 - **Exercise INTRO 1** :
 ```
 SELECT user_id, stars FROM reviews WHERE stars =3;
 ```
 ### **2. SQL SELECT**
  - **Exercise SELECT 1:**
   Your given a products table, which contains data about different Microsoft Azure cloud products.
   Solution:
  ```
  SELECT * FROM products;
  ```
 ### **3. SQL WHERE**
  - **Exercise WHERE 1.1:**
  Given the reviews table, write a query to retrieve all 3-star reviews using the SQL WHERE clause. Only display the user_id and stars columns. 
  Solution:
  ```
  SELECT user_id, stars FROM reviews WHERE stars =3;
  ```
 ### **4. SQL AND,OR,NOT**
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
 ### **5. SQL BETWEEN**
  - **Exercise BETWEEN 1:**
  Imagine you are a Data Analyst working at CVS Pharmacy, and you had access to pharmacy sales data. Use the BETWEEN SQL command to find data on medicines:
  
   which sold between 100,000 units and 105,000 units 
   AND were manufactured by either Biogen, AbbVie, or Eli Lilly
   Output the manufacturer name, drug name, and the # of units sold.
   
   Solution:
   ```
   SELECT manufacturer, drug, units_sold FROM pharmacy_sales WHERE( manufacturer = 'Biogen' OR manufacturer = 'AbbVie' OR manufacturer = 'Eli Lilly') AND ( units_sold BETWEEN 100000 AND 105000);
   ```
 ### **6. SQL IN**
  - **Exercise IN 1:**
  Imagine you are a Data Analyst working at CVS Pharmacy, and you had access to pharmacy sales data. Use the IN SQL command to find data on medicines:

   which were manufactured by either Roche, Bayer, or AstraZeneca
   and did not sell between 55,000 and 550,000 units
   Output the manufacturer name, drug name, and the # of units sold. for all the medicines which match that criteria.
  
   Solution:
   ```
   SELECT manufacturer, drug, units_sold FROM pharmacy_sales WHERE ( manufacturer IN ('Roche', 'Bayer','AstraZeneca')) AND (NOT( units_sold BETWEEN 55000 AND 550000));
   ```
 ### **7. SQL LIKE**
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
 ### **8. SQL FILTERING REVIEW**
  - **Exercise FILTERING REVIEW 1:** 
  You have a table of 1000 customer records from a small-business based in Australia.
  Find all customers who are between the ages of 18 and 22 (inclusive), live in either Victoria, Tasmania, Queensland, their gender isn't "n/a", and their name starts with either 'A' or 'B'.


  Solution:
  ```
   SELECT * FROM customers WHERE (state IN('Victoria' , 'Tasmania', 'Queensland'))  AND (age BETWEEN 18 AND 22) AND (gender != 'n/a') AND ( (customer_name LIKE ('A%')) OR ( customer_name LIKE ('B%')));
  ```
 ## SQL INTERMEDIATE
 ### **1. COUNT,SUM,AVG**
  - **Exercise COUNT 1:**
  Output the number of rows in the pharmacy_sales table.
  
  Solution:
  ```
   SELECT COUNT(*) FROM pharmacy_sales;
  ```
  - **Exercise SUM 2:**   
  Imagine you are a Data Analyst working at CVS Pharmacy, and you had access to pharmacy sales data.
  Output the total number of drugs manufactured by Pfizer, and output the total sales for all the Pfizer drugs.
  
  
  Solution:
  ```
   SELECT COUNT(*) , SUM(total_sales) FROM pharmacy_sales WHERE manufacturer = 'Pfizer';
  ```
  - **Exercise AVG 3:**
  Write a SQL query using AVG to find the average open price for Google stock (which has a stock ticker symbol of 'GOOG').
  
  
  Solution:
  ```
   SELECT AVG(open) FROM stock_prices WHERE ticker = 'GOOG';
  ```
  - **Exercise MIN 4:**
  Use SQL's MIN command in this practice exercise, to find the lowest Microsoft stock (MSFT) ever opened at.
  
  
  Solution:
  ```
  SELECT MIN(open) FROM stock_prices WHERE ticker = 'MSFT';
  ```
  - **Exercise MAX 5:**
  Use SQL's MAX command in this practice exercise, to find the highest Netflix stock (NFLX) ever opened at.
  
  
  Solution:
  ```
   SELECT MAX(open) FROM stock_prices WHERE ticker = 'NFLX';
  ```
 ### **2. SQL GROUP BY**
  - **Exercise 1 GROUP BY:**
  For every FAANG stock in the stock_prices dataset, write a SQL query to find the lowest price each stock ever opened at? Be sure to also order your results by price, in descending order.
  
  
  Solution:
  ```
   SELECT MIN(open), ticker FROM stock_prices GROUP BY ticker ORDER BY min DESC;
  ```
  - **Exercise 2 GROUP BY:**
  Suppose you are given a table of candidates and their skills. How many candidates possess each of the different skills? Sort your answers based on the count of candidates, from highest to lowest.
  
  
  Solution:
  ```
  SELECT COUNT(candidate_id),skill FROM candidates GROUP BY skill ORDER BY count DESC; 
  ```
 ### **2. SQL HAVING** 
  - **Exercise 1 SQL HAVING:**
  Use SQL's HAVING & MIN commands to find all FAANG stocks whose open share price was always greater than $100.
  
  
  Solution:
  ```
   SELECT MIN(open), ticker FROM stock_prices GROUP BY ticker HAVING MIN(open) >= 101;
  ```
  - **Exercise 2 SQL HAVING:**
  Given a table of candidates and their technical skills, list the candidate IDs of candidates who have more than 2 technical skills.
  
  
  Solution:
  ```
   SELECT candidate_id FROM candidates GROUP BY candidate_id HAVING COUNT (candidate_id) >= 3;
  ```
 ### **2. SQL DISTINCT**
  - **Exercise 1 SQL DISTINCT:**
  Assume you're given a table containing data on Amazon customers and their spending on products in different category. Write a query using COUNT DISTINCT to identify the number of unique products within each product category.
  
  
  Solution:
  ```
   SELECT COUNT(DISTINCT product), category FROM product_spend GROUP BY category;
  ```
  ### **3. SQL ARITHMETIC OPERATIONS**
  - **Exercise 1 Substraction:** 
  CVS Health is trying to better understand its pharmacy sales, and how well different products are selling. Each drug can only be produced by one manufacturer.
  Write a query to find the top 3 most profitable drugs sold, and how much profit they made. Assume that there are no ties in the profits. Display the result from the highest to the lowest total profit.
  
  
  Solution :
  ```
   SELECT drug, (total_sales - cogs) AS total_profit FROM pharmacy_sales ORDER BY total_profit DESC LIMIT 3;
  ```
  - **Exercise 2:**
  Your team at JPMorgan Chase is preparing to launch a new credit card, and to gain some insights, you're analyzing how many credit cards were issued each month.
  Write a query that outputs the name of each credit card and the difference in the number of issued cards between the month with the highest issuance cards and the lowest issuance. Arrange the results based on the largest disparity.
  
  
  Solution:
  ```
   SELECT card_name, (MAX(issued_amount) - MIN(issued_amount)) AS difference FROM monthly_cards_issued GROUP BY card_name ORDER BY difference DESC;
  ```
  - **Exercise 3:**
  Netflix stock had a big-mover month in April 2022 in the reverse direction. That month, Netflix reported that the company lost 200k subscribers in Q1, and expected to lose another two million subs in Q2. In Apr'22, Netflix stock opened that month at $376.80 per share, but closed at $190.36, representing a 49.5% loss – yikes!
  
  
  Solution:
  ```
   SELECT ticker, COUNT(ticker) FROM stock_prices WHERE (close - open)/open > 0.10 OR (close - open)/open < -0.10 GROUP BY ticker ORDER BY count DESC;
  ```
 ### **4. SQL MATH FUNCTIONS**
  - **Exercise 1 Math Functions:**
  Imagine you are a Data Analyst working at CVS Pharmacy, and you had access to pharmacy sales data.
  For all Merck drugs, output the drug name, and the unit cost for each drug, rounded up to the nearest dollar. Order it from cheapest to most expensive drug
  
  
  Solution:
  ```
   SELECT drug, CEIL(total_sales / units_sold) AS unit_cost FROM pharmacy_sales WHERE manufacturer = 'Merck' ORDER BY unit_cost;
--como en C++ xdxd
  ```
 ### **5. SQL DIVISION**
   - **Exercise 1 Math Functions:**
   This exercise isn’t free, lol
     
 ### **6. SQL NULL**
   - **Exercise 1 SQL Null:**
   Tesla is investigating production bottlenecks and they need your help to extract the relevant data. Write a query to determine which parts have begun the assembly process but are not yet finished.
   Assumptions:
    parts_assembly table contains all parts currently in production, each at varying stages of the assembly process.
    An unfinished part is one that lacks a finish_date.
   This question is straightforward, so let's approach it with simplicity in both thinking and solution.
   Effective April 11th 2023, the problem statement and assumptions were updated to enhance clarity.
   
   
   Solution:
   
   ```
    SELECT part, assembly_step FROM parts_assembly WHERE finish_date IS NULL  
   ```
 ### **7. SQL CASE**
   - **Exercise 1 SQL Case:**
    Explore the Marvel Avengers dataset and write a query to categorize superheroes based on their average likes as follows:
    Super Likes: Superheroes with an average likes count greater than or equal to 15,000.
    Good Likes: Superheroes with an average likes count between 5,000 and 14,999 (inclusive).
    Low Likes: Superheroes with an average likes count less than 5,000.
    Display the actor and character's name, platform, average likes, and the corresponding likes category. Sort the results by average likes.
   
   
   Solution:
   
   ```
      SELECT actor, character, platform, avg_likes, 
     CASE 
      WHEN avg_likes > 14999 THEN 'Super Likes'
      WHEN avg_likes > 4999 THEN 'Good Likes'
      ELSE 'Low Likes'
     END AS likes_category
     FROM marvel_avengers
     ORDER BY avg_likes DESC;
 
   ```
   - **Exercise 2 SQL Case:**
   This is the same question as problem #3 in the SQL Chapter of Ace the Data Science Interview!
   Assume you're given the table on user viewership categorised by device type where the three types are laptop, tablet, and phone.
   Write a query that calculates the total viewership for laptops and mobile devices where mobile is defined as the sum of tablet and phone viewership. Output the total viewership for laptops as laptop_reviews and the total viewership for mobile devices as mobile_views.
   Effective 15 April 2023, the solution has been updated with a more concise and easy-to-understand approach.
   
   
   Solution:
   
   
   ```
    SELECT 
      SUM(CASE WHEN device_type = 'laptop' THEN 1 ELSE 0 END) AS laptop_views,
      SUM(CASE WHEN device_type IN ('tablet', 'phone') THEN 1 ELSE 0 END) AS mobile_views
    FROM viewership;
   ```
 ### **7. SQL JOINS**
 
   - **Exercise 1 SQL Join:**
   
   Assume you're given the tables containing info about Robinhood users, and the stock trades they placed.
   Use a JOIN to output all the information from the trades table joined to the users table.
 
   
   Solution:
   
   ```
    SELECT * FROM trades INNER JOIN users ON trades.user_id = users.user_id;
   ```
   - **Exercise 2 SQL Join:**
   
   Assume you're given the tables containing completed trade orders and user details in a Robinhood trading system.
   Write a query to retrieve the top three cities that have the highest number of completed trade orders listed in descending order. Output the city name and the corresponding number of completed trade orders.
   
   
   Solution:
   
   ```
    SELECT u.city, COUNT(t.order_id) AS total_orders FROM trades t JOIN users u ON t.user_id = u.user_id WHERE t.status = 'Completed' GROUP BY u.city ORDER BY total_orders DESC LIMIT 3;
   ```
   - **Exercise 3 SQL Join:**
   
   Assume you're given two tables containing data about Facebook Pages and their respective likes.
   Write a query to return the IDs of the Facebook pages that have zero likes. The output should be sorted in ascending order based on the page IDs.

   
	Solution:
   
   ```
    SELECT p.page_id
    FROM pages p
    WHERE NOT EXISTS (
      SELECT 1
      FROM page_likes pl
      WHERE p.page_id = pl.page_id
    )
    ORDER BY p.page_id ASC;
   ```
 ### **8. SQL DATE-FUNCTIONS**
   - **Exercise 1 Date-Functions:**
   
   Given a table of Facebook posts, for each user who posted at least twice in 2021, write a query to find the number of days between each user’s first post of the year and last post of the year in the year 2021. Output the user and number of the days between each user's first and last post.
   p.s. If you've read the Ace the Data Science Interview and liked it, consider writing us a review?
   
   
   Solution:
   
   ```
    SELECT user_id, MAX(post_date::DATE) - MIN(post_date::DATE) AS days_between
    FROM posts WHERE DATE_PART('year', post_date::DATE) = 2021 GROUP BY user_id HAVING COUNT(post_id)>1;
   ```
   - **Exercise 2 Date-Functions:**
   
   Assume you're given tables with information about TikTok user sign-ups and confirmations through email and text. New users on TikTok sign up using their email addresses, and upon sign-up, each user receives a text message confirmation to activate their account.
   Write a query to display the user IDs of those who did not confirm their sign-up on the first day, but confirmed on the second day.
   
   Solution:
   
   ```
    SELECT DISTINCT user_id
    FROM emails 
    INNER JOIN texts
      ON emails.email_id = texts.email_id
    WHERE texts.action_date = emails.signup_date + INTERVAL '1 day'
      AND texts.signup_action = 'Confirmed';
   ```
   
   - **Exercise 3 Date-Functions:**
   
   Given a table of Facebook posts, for each user who posted at least twice in 2021, write a query to find the number of days between each user’s first post of the year and last post of the year in the year 2021. Output the user and number of the days between each user's first and last post.
   p.s. If you've read the Ace the Data Science Interview and liked it, consider writing us a review?

   
   Solution:
   
   ```
    SELECT user_id, MAX(post_date::DATE) - MIN(post_date::DATE) AS days_between
    FROM posts WHERE DATE_PART('year', post_date::DATE) = 2021 GROUP BY user_id HAVING COUNT(post_id)>1;
   ```
  ## SQL ADVANCED
  ### **1. CTE vs. SUBQUERY**
   - **Exercise 1 CTE vs. SUBQUERY:**

   As the lead data analyst for a prominent music event management company, you have been entrusted with a dataset containing concert revenue and detailed information about various artists.

   Your mission is to unlock valuable insights by analyzing the concert revenue data and identifying the top revenue-generating artists within each music genre.

   Write a query to rank the artists within each genre based on their revenue per member and extract the top revenue-generating artist from each genre. Display the output of the artist name, genre, concert revenue, number of members, and revenue per band member, sorted by the highest revenue per member within each genre.
   ```
    WITH RevenuePerMember AS (
    SELECT 
        artist_name,
        genre,
        concert_revenue,
        number_of_members,
        concert_revenue / number_of_members AS revenue_per_member,
        RANK() OVER (PARTITION BY genre ORDER BY concert_revenue / NULLIF(number_of_members, 0) DESC) AS rank_genre
     FROM concerts
    ) 
    SELECT 
     artist_name,
     concert_revenue,
     genre,
     number_of_members,
     revenue_per_member
    FROM RevenuePerMember
    WHERE rank_genre = 1
    ORDER BY revenue_per_member DESC;
   ```
   - **Exercise 2 CTE vs. SUBQUERY:**
  A Microsoft Azure Supercloud customer is defined as a customer who has purchased at least one product from every product category listed in the products table.

   Write a query that identifies the customer IDs of these Supercloud customers.   
   ```
    SELECT customer_id
     FROM customer_contracts cc
     JOIN products p ON cc.product_id = p.product_id
     GROUP BY customer_id 
     HAVING COUNT(DISTINCT p.product_category) = (SELECT COUNT (DISTINCT product_category) FROM products);
   ```
   - **Exercise 3 CTE vs. SUBQUERY:**
  
  Zomato is a leading online food delivery service that connects users with various restaurants and cuisines, allowing them to browse menus, place orders, and get meals delivered to their doorsteps.
  Recently, Zomato encountered an issue with their delivery system. Due to an error in the delivery driver instructions, each item's order was swapped with the item in the subsequent row. As a data analyst, you're asked to correct this swapping error and return the proper pairing of order ID and item.
  If the last item has an odd order ID, it should remain as the last item in the corrected data. For example, if the last item is Order ID 7 Tandoori Chicken, then it should remain as Order ID 7 in the corrected data.
  In the results, return the correct pairs of order IDs and items.
  ```
   WITH order_counts AS ( SELECT COUNT(order_id) AS total_orders  FROM orders)

    SELECT
      CASE
        WHEN order_id % 2 != 0 AND order_id != total_orders THEN order_id + 1
        WHEN order_id % 2 != 0 AND order_id = total_orders THEN order_id
            ELSE order_id - 1
        END AS corrected_order_id,item
    FROM orders
    CROSS JOIN order_counts
    ORDER BY corrected_order_id;
   ```
 ### **2. WINDOW FUNCTION**
   - **Exercise 3 WINDOW FUNCTION:**
  Your team at JPMorgan Chase is soon launching a new credit card. You are asked to estimate how many cards you'll issue in the first month.

  Before you can answer this question, you want to first get some perspective on how well new credit card launches typically do in their first month.

  Write a query that outputs the name of the credit card, and how many cards were issued in its launch month. The launch month is the earliest record in the monthly_cards_issued table for a given card. Order the results starting from the biggest issued amount.
  
  ```
   WITH first_launch AS ( SELECT  card_name, MIN(issue_year * 12 + issue_month) AS first_launch_date
    FROM monthly_cards_issued
    GROUP BY card_name
  )
   SELECT 
     m.card_name, 
     m.issued_amount
    FROM monthly_cards_issued m
    JOIN first_launch f 
    ON m.card_name = f.card_name 
    AND (m.issue_year * 12 + m.issue_month) = f.first_launch_date
   ORDER BY m.issued_amount DESC;

   ```
 ### **3. SQL RANKING**
   - **Exercise 1 SQL RANKING:**
  
  Assume there are three Spotify tables: artists, songs, and global_song_rank, which contain information about the artists, songs, and music charts, respectively.

  Write a query to find the top 5 artists whose songs appear most frequently in the Top 10 of the global_song_rank table. Display the top 5 artist names in ascending order, along with their song appearance ranking.

  If two or more artists have the same number of song appearances, they should be assigned the same ranking, and the rank numbers should be continuous (i.e. 1, 2, 2, 3, 4, 5). If you've never seen a rank order like this before, do the rank window function tutorial.
   
   Solution : 
 ```
  WITH TOP10 AS (
  SELECT artists.artist_name, DENSE_RANK() OVER ( ORDER BY COUNT(songs.song_id) DESC) AS artist_rank
  FROM artists
  INNER JOIN songs
    ON artists.artist_id = songs.artist_id
  INNER JOIN global_song_rank AS ranking
    ON songs.song_id = ranking.song_id
  WHERE ranking.rank < 11
  GROUP BY artists.artist_name
)
SELECT artist_name, artist_rank FROM TOP10 WHERE artist_rank < 6;  
 ```



   
   
   

   
 
  

  
  
 
  
  
