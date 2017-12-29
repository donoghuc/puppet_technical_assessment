# Technical Assessment
I was invited to do a technical assessment at a tech company I applied to. The challenge requirements were sent via plain text email body (shown below in this readme, NOTE: I did some formatting to make it display nicely in markdown). 

The requirements were pretty open-ended (ie no particular format required). I used Jupytern Notebook [donoghuc_technical_challenge.ipynb](donoghuc_technical_challenge.ipynb) to build out an HTML document with SQL solutions and some javascript to toggle on/off underlying python code. The jupyter notebook will render in github viewer. I submitted [donoghuc_technical_challenge.html](donoghuc_technical_challenge.html) via email 24hrs after recieving requirements. 

### assessment questions (provided in body of email)
Below are a series of questions for you to review and complete.  The purpose of this evaluation is to get a baseline understanding of what kind of experience you’ve had with SQL and relational databases.  There are no tricks here—and if you can’t do a problem, don’t worry!  Just take a stab at it (we care about how you choose to approach a problem). Definitely look up anything you want online.  We recommend taking roughly an hour to work through these, although there is no time limit.

Part A

1. What is a join?
2. What are the types of join? Explain each (2 sentences or less)
3. What are the differences between a primary key, a unique key, and a foreign key?
4. What are the different standard normalizations?  Give an example of each.
5. What is a Database Relationship, and what are three of the more common ones?
6. What is a NULL value and how does it differ from a zero value?
7. Where can you get more information about BigQuery Standard SQL functions?


Part B

Salesperson
```
ID,Name,Hire Date
1,Nancy,04/01/06
2,Chuck,03/27/14
3,Lora,01/19/10
4,Phoebe,01/19/11
5,Clarence,05/01/17
```

Customer
```
ID,Name,City
1,Green,Portland
2,Sapphire,San Francisco
3,Red,Tulsa
4,Amber,Portland
5,Neon,Columbus
```
Order
```
ID,CreatedDate,ClosedDate,CustID,SalesID,Amount
1,04/14/15,05/30/17,4,3,100000
2,04/01/17,05/30/17,4,3,1000
3,03/27/16,05/01/17,1,1,3250
4,02/26/16,05/14/17,1,1,2000
5,04/30/17,05/06/17,5,1,12000
6,04/15/17,05/22/17,2,4,5000
7,05/02/17,05/03/17,3,5,550
```
Given the tables above, write a query that will tell you:

1. How much did each Salesperson sell in May 2017?
2. On average, how long does it take to close an order?
3. For each order, how long was the Salesperson at the company when the deal was closed?
4. List all customers who closed an order in May 2017, from the highest Amount to the lowest.

Part C

Customers
```
ID,Name,City,CustomerSince,Industry,NumEmployees
1,Rose,Nashville,04/01/14,Healthcare,50-100
2,Pearl,Seattle,03/27/13,Healthcare,1000
3,Jabberwocky,Portland,08/01/16,Technology,"500-1,000"
4,Jensen,San Diego,04/01/15,Finance,1000
```
Orders
```
ID,CustomerID,DateShipped
1,1,05/17/17
2,2,05/19/17
3,1,05/16/17
4,2,05/20/17
5,3,05/14/17
```
Products
```
ID,Name
1,Apple
2,Bananas
3,Cockatoos
```
Order_Details
```
OrderID,ProductID,Quantity
1,1,50
1,2,2
1,3,7
2,2,10
3,2,10
3,1,100
4,3,2
5,1,10
5,2,100
5,3,2
```

1. Given the tables above, write a query that will provide all of the available customer information for customers that have purchased at least 25 apples.


Part D
```SQL
SELECT
 ticket_id,
 MAX(operating_system) operating_system,
 MAX(difficulty) difficulty,
 MAX(environment) environment,
 MAX(escalation) escalation,
 MAX(nature_of_issue) nature_of_issue,
 MAX(needs_assistance) needs_assistance,
 MAX(organization) organization,
 MAX(support_level) support_level,
FROM (
 SELECT
   ticket_id,
   (CASE
       WHEN title = 'Operating System' THEN value
       ELSE NULL END) AS operating_system,
   (CASE
       WHEN title = 'Difficulty' THEN value
       ELSE NULL END) AS difficulty,
   (CASE
       WHEN title = 'Environment' THEN value
       ELSE NULL END) AS environment,
   (CASE
       WHEN title = 'Escalation' THEN value
       ELSE NULL END) AS escalation,
   (CASE
       WHEN title = 'Nature of Issue' THEN value
       ELSE NULL END) AS nature_of_issue,
   (CASE
       WHEN title = 'Needs Assistance' THEN value
       ELSE NULL END) AS needs_assistance,
   (CASE
       WHEN title = 'Organization' THEN value
       ELSE NULL END) AS organization,
   (CASE
       WHEN title = 'Priority' THEN value
       ELSE NULL END) AS priority,
   (CASE
       WHEN title = 'Support Level' THEN value
       ELSE NULL END) AS support_level
 FROM
   zendesk.tickets ) AS temp
GROUP BY
 Ticket_id
```
1. In layman’s terms, what is the above query doing?
2. Given the information available in the query, what does zendesk.tickets and the new table that results from this query look like? Describe the schema or diagram the tables below.
3. What, if anything, is odd about this query?

