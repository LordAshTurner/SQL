Rockbuster Stealth Data Analysis Project# SQL

Rockbuster Stealth LLC is a movie rental company that used to have stores around the world. Facing stiff competition from streaming services such as Netflix and Amazon Prime,
the Rockbuster Stealth management team is planning to use its existing movie licenses to launch an online video rental service in order to stay competitive.

You’ve been hired as a data analyst by Rockbuster Stealth’s business intelligence (BI) department to help with the launch strategy for the new online video service. The BI
department helps other departments, from inventory to customer insights, with data-related queries. Your first task is to load all of Rockbuster’s data into a relational database
management system (RDBMS). Then, you’ll use SQL to analyze the data and answer any ad-hoc business questions that other departments may have.

Key Questions and Objectives
The Rockbuster Stealth Management Board has asked a series of business questions and they expect data-driven answers that they can use for their 2020 company strategy. Here are
the main questions they’d like to answer:
● Which movies contributed the most/least to revenue gain?
● What was the average rental duration for all videos?
● Which countries are Rockbuster customers based in?
● Where are customers with a high lifetime value based?
● Do sales figures vary between geographic regions?

![image](https://github.com/LordAshTurner/SQL/assets/159558850/aa3696cd-bfdb-47e9-a99b-84e429321d18)
![image](https://github.com/LordAshTurner/SQL/assets/159558850/c0fc7804-023f-410b-bfee-a405a3d8da70)


After finding my top 10 countries based on customer numbers, I built my case on when I identified the top 10 cities that fall within the top 10
countries I identified
![image](https://github.com/LordAshTurner/SQL/assets/159558850/e9bcc7d1-be0c-4dec-a306-fdb873936f43)
![image](https://github.com/LordAshTurner/SQL/assets/159558850/d5877f38-6b8c-4eb4-ba66-301bcc6794cd)

At this point, I wrote a query to find the top 5 customers from the top 10 cities who’ve paid the highest total amounts to Rockbuster. The customer
team would like to reward them for their loyalty!  By doing so, my final inquiry built from prior work led me to a pleasing result. 

(SELECT A.customer_id,
A.first_name,
A.last_name,
C.city,
D.country,
SUM(E.amount) AS total_amount_paid
FROM customer A
INNER JOIN address B ON A.address_id = B.address_id
INNER JOIN city C ON B.city_id = C.city_id
INNER JOIN country D ON C.country_id = D.country_id
INNER JOIN payment E ON A.customer_id = E.customer_id
GROUP BY A.customer_id,
A.first_name,
A.last_name,
C.city,
D.country
ORDER BY SUM(amount) DESC
LIMIT 5)
![image](https://github.com/LordAshTurner/SQL/assets/159558850/a4cdff90-eb5a-4fe7-a8a0-4731d8bdfbb3)

