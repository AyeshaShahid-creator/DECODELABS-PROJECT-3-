# SQL Data Analysis — Project 3
Overview
This project performs SQL Data Analysis on the
cleaned e-commerce orders dataset (1,200 records)
produced in Project 1. The dataset is loaded into a
SQLite database and queried using 10 structured SQL
queries — covering SELECT, WHERE, ORDER BY,
GROUP BY, HAVING, COUNT, SUM, and AVG — to
extract real business insights through relational logic.
Key Concept
SQL is a declarative language — you define what you
want, and the database engine decides how to fetch
it. Understanding the logical execution order (FROM
→ WHERE → GROUP BY → HAVING → SELECT →
ORDER BY) is critical to writing correct queries and
avoiding the common "Alias Trap".
Queries Written
# Query Clauses
Used
Business
Question
Answered
1
Preview
First 10
Orders
SELECT,
LIMIT
What does the
data look like?
2 All Delivered
Orders
WHERE,
ORDER
BY
Which
delivered
orders had
highest value?
3
High-Value
Orders >
$2000
WHERE,
ORDER
BY
Which orders
are flagged as
high-value?
4 Orders by
Product
COUNT,
GROUP
BY
Which product
is ordered
most?
5 Revenue by
Product
SUM,
GROUP
BY
Which product
generates the
most revenue?
6
Avg Order
Value by
Payment
Method
AVG,
GROUP
BY
Which
payment
method drives
highest order
value?
# Query Clauses
Used
Business
Question
Answered
7
Orders &
Revenue by
Referral
Source
COUNT,
SUM,
AVG,
GROUP
BY
Which channel
brings the
most
customers and
revenue?
8
High-
Volume
Products
only
GROUP
BY,
HAVING
Which
products
exceed 170
orders?
9
Cancelled
Orders by
Product
WHERE,
GROUP
BY,
COUNT
Which product
has the most
cancellations?
10
Revenue
Contribution
% per
Product
SUM,
Subquery,
GROUP
BY
What
percentage of
total revenue
does each
product
generate?
Key Findings
Chair and Printer are nearly tied for highest
revenue (~$195,600 each), despite Printer leading
in order count.
Credit Card has the highest average order value
($1,127.55) among all payment methods.
Instagram drives the most orders (259) and the
most total revenue ($275,285) — the top
acquisition channel.
Chair has the most cancellations (45 orders) —
worth investigating for a product or fulfillment
issue.
Revenue is fairly evenly distributed: each product
contributes between 12% and 15.5% of total
revenue.
Tech Stack
Python 3
SQLite3 (via Python's built-in sqlite3 module)
Pandas (for loading CSV → database and
displaying results)
Repository Structure
├── sql_analysis.py # Main SQL query
script
├── orders.db # SQLite
database (auto-generated from cleaned CSV)
├── sql_query_log.csv # Log of all
queries run
├── cleaned_dataset.csv # Input dataset
(output of Project 1)
└── README.md
How to Run
pip install pandas
python sql_analysis.py
This will create orders.db from the cleaned CSV, run
all 10 queries, print results to the console, and save
sql_query_log.csv .
SQL Execution Order (Key Concept
from the Kit)
The database does NOT read your query top to
bottom. The actual order is:
1. FROM → Locate the table
2. WHERE → Filter individual rows
3. GROUP BY → Bucket the filtered rows
4. HAVING → Filter the buckets
5. SELECT → Pick columns and calculate
6. ORDER BY → Sort the final output
This is why you cannot use a SELECT alias inside a
WHERE clause — the alias doesn't exist yet when
WHERE runs.

