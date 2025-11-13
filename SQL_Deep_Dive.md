# SQL Deep Dive: JOINs, GROUP BY, and Subqueries

This guide provides a detailed explanation of the essential SQL topics identified in the study plan: `JOIN`s, `GROUP BY`, and Subqueries. Understanding these concepts is critical for any data-related role.

To make the examples clear, we will use two simple tables: `Employees` and `Departments`.

**`Employees` Table:**
| EmployeeID | Name    | DepartmentID | Salary |
|------------|---------|--------------|--------|
| 1          | Alice   | 101          | 70000  |
| 2          | Bob     | 102          | 80000  |
| 3          | Charlie | 101          | 60000  |
| 4          | David   | 103          | 90000  |
| 5          | Eve     | NULL         | 50000  |

**`Departments` Table:**
| DepartmentID | DepartmentName |
|--------------|----------------|
| 101          | Engineering    |
| 102          | Marketing      |
| 104          | Sales          |

---

### 1. JOINs: Combining Data from Multiple Tables

A `JOIN` clause is used to combine rows from two or more tables based on a related column between them.

#### A. `INNER JOIN`

*   **Concept:** The `INNER JOIN` keyword selects records that have matching values in **both** tables. It is the most common type of join.
*   **Analogy:** Think of it as the intersection of two sets. You only get the data that exists in both.
*   **Example:** Let's find the names of employees and the department they work in.

    ```sql
    SELECT
        Employees.Name,
        Departments.DepartmentName
    FROM
        Employees
    INNER JOIN
        Departments ON Employees.DepartmentID = Departments.DepartmentID;
    ```

*   **Result:**
    | Name    | DepartmentName |
    |---------|----------------|
    | Alice   | Engineering    |
    | Bob     | Marketing      |
    | Charlie | Engineering    |

    *Notice that David and Eve are not in the result. David's `DepartmentID` (103) doesn't exist in the `Departments` table, and Eve's is `NULL`. The "Sales" department is also not listed because no employee is assigned to it.*

#### B. `LEFT JOIN` (or `LEFT OUTER JOIN`)

*   **Concept:** The `LEFT JOIN` keyword returns **all** records from the left table (`Employees`), and the matched records from the right table (`Departments`). The result is `NULL` from the right side if there is no match.
*   **Analogy:** You take everything from the first set, and only the matching parts from the second set.
*   **Example:** Let's list all employees and their department, even if they don't have one.

    ```sql
    SELECT
        Employees.Name,
        Departments.DepartmentName
    FROM
        Employees
    LEFT JOIN
        Departments ON Employees.DepartmentID = Departments.DepartmentID;
    ```

*   **Result:**
    | Name    | DepartmentName |
    |---------|----------------|
    | Alice   | Engineering    |
    | Bob     | Marketing      |
    | Charlie | Engineering    |
    | David   | NULL           |
    | Eve     | NULL           |

    *Now, all employees are listed. David and Eve, who have no matching department in the `Departments` table, have `NULL` as their `DepartmentName`.*

---

### 2. `GROUP BY`: Summarizing and Aggregating Data

*   **Concept:** The `GROUP BY` statement groups rows that have the same values in specified columns into summary rows. It is often used with **aggregate functions** (`COUNT()`, `MAX()`, `MIN()`, `SUM()`, `AVG()`) to perform calculations on each group.
*   **Rule of Thumb:** If you are using an aggregate function and you have other columns in your `SELECT` statement, you must `GROUP BY` those other columns.
*   **Example:** Let's find the number of employees in each department and the average salary for each department.

    ```sql
    SELECT
        Departments.DepartmentName,
        COUNT(Employees.EmployeeID) AS NumberOfEmployees,
        AVG(Employees.Salary) AS AverageSalary
    FROM
        Employees
    INNER JOIN
        Departments ON Employees.DepartmentID = Departments.DepartmentID
    GROUP BY
        Departments.DepartmentName;
    ```

*   **Result:**
    | DepartmentName | NumberOfEmployees | AverageSalary |
    |----------------|-------------------|---------------|
    | Engineering    | 2                 | 65000         |
    | Marketing      | 1                 | 80000         |

    *The query first joins the tables, then groups the resulting rows by `DepartmentName`. Finally, the aggregate functions (`COUNT` and `AVG`) are calculated for each group.*

---

### 3. Subqueries (Nested Queries)

*   **Concept:** A subquery is a SQL query nested inside a larger query. The subquery is executed first, and its result is used by the outer query. Subqueries can be used in `SELECT`, `FROM`, `WHERE`, and `HAVING` clauses.
*   **Example:** Let's find the names of all employees who earn more than the company's average salary.

    1.  First, we need to find the average salary.
    2.  Then, we can find the employees who earn more than that average.

    A subquery lets us do this in one step:

    ```sql
    SELECT
        Name,
        Salary
    FROM
        Employees
    WHERE
        Salary > (SELECT AVG(Salary) FROM Employees);
    ```

*   **Execution Flow:**
    1.  The inner query `(SELECT AVG(Salary) FROM Employees)` runs first. The average salary is (70000 + 80000 + 60000 + 90000 + 50000) / 5 = 70000.
    2.  The outer query then becomes:
        ```sql
        SELECT Name, Salary FROM Employees WHERE Salary > 70000;
        ```

*   **Result:**
    | Name  | Salary |
    |-------|--------|
    | Bob   | 80000  |
    | David | 90000  |
