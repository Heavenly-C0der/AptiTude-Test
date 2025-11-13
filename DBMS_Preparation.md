# Database Management Systems (DBMS) Study Guide

For an ML Engineer, understanding databases is crucial for accessing, storing, and managing the large datasets required for training and inference. This guide covers the fundamental DBMS concepts you'll likely be tested on.

---

### 1. Key Topics

#### A. Relational Databases & SQL
This is the most important area. You must be proficient in writing SQL queries.

> For concrete examples of these queries, see [SQL Query Examples](./SQL_Examples.md).

- **Basic SQL Queries:**
  - `SELECT`: Retrieving data from tables.
  - `FROM`: Specifying the table.
  - `WHERE`: Filtering rows based on conditions.
  - `GROUP BY`: Aggregating rows that have the same values into summary rows.
  - `HAVING`: Filtering groups based on aggregate functions.
  - `ORDER BY`: Sorting the result set.
- **JOINs:**
  - `INNER JOIN`: Returns records that have matching values in both tables.
  - `LEFT JOIN` (or `LEFT OUTER JOIN`): Returns all records from the left table, and the matched records from the right table.
  - `RIGHT JOIN` (or `RIGHT OUTER JOIN`): Returns all records from the right table, and the matched records from the left table.
  - `FULL OUTER JOIN`: Returns all records when there is a match in either left or right table.
- **Aggregate Functions:**
  - `COUNT()`: Counts the number of rows.
  - `SUM()`: Calculates the sum of a set of values.
  - `AVG()`: Calculates the average of a set of values.
  - `MAX()` / `MIN()`: Returns the maximum/minimum value.
- **Subqueries (Nested Queries):** Queries embedded within another query.

#### B. Database Design & Normalization
Understanding how to design a database schema is key to avoiding data redundancy and ensuring data integrity.

- **Keys:**
  - **Primary Key:** A unique identifier for each record in a table.
  - **Foreign Key:** A key used to link two tables together. It's a field in one table that refers to the Primary Key in another table.
  - **Candidate Key:** An attribute or set of attributes that can uniquely identify a tuple.
  - **Super Key:** A set of attributes that can uniquely identify a tuple.
- **Normalization:** The process of organizing columns and tables in a relational database to minimize data redundancy.
  - **First Normal Form (1NF):** The table is atomic (each cell contains a single value) and each record is unique.
  - **Second Normal Form (2NF):** The table is in 1NF and all non-key attributes are fully functional dependent on the primary key.
  - **Third Normal Form (3NF):** The table is in 2NF and there are no transitive dependencies.

#### C. Transactions & Concurrency
- **ACID Properties:** A set of properties of database transactions intended to guarantee validity even in the event of errors, power failures, etc.
  - **Atomicity:** All changes to data are performed as if they are a single operation. Either all of the changes are performed, or none of them are.
  - **Consistency:** Data is in a consistent state when a transaction starts and when it ends.
  - **Isolation:** The intermediate state of a transaction is invisible to other transactions.
  - **Durability:** After a transaction has been committed, it will remain so, even in the event of a power loss.

#### D. Relational vs. NoSQL Databases
- Have a basic understanding of the difference between SQL (like PostgreSQL, MySQL) and NoSQL databases (like MongoDB, Cassandra).
- **When to use which:** SQL for structured data with a predefined schema; NoSQL for unstructured or semi-structured data, large-scale data, and flexible schema requirements.

---

### 2. How to Prepare

- **Practice SQL:** The best way to learn SQL is by writing queries. Use online platforms to solve SQL problems.
- **Design a System:** Take a simple concept (e.g., a blog, an e-commerce store) and design the database schema for it. Decide on the tables, columns, and relationships.
- **Understand the Concepts:** For normalization and ACID properties, focus on understanding the "why" behind them—they are designed to ensure data integrity.

---

### 3. Recommended Resources

- **Online SQL Practice:**
  - **LeetCode / HackerRank:** Both have excellent database problem sets that require you to write complex SQL queries.
  - **SQLZoo:** Interactive tutorials for learning SQL.
- **YouTube:**
  - Search for "database normalization explained" or "ACID properties" to find many clear, visual explanations.
- **Websites:**
  - **GeeksforGeeks:** In-depth articles on all major DBMS topics.
