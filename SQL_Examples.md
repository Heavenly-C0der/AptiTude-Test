# SQL Query Examples

This file provides practical examples for the SQL concepts mentioned in the DBMS study guide. We'll use two hypothetical tables: `Employees` and `Departments`.

### Schema

**`Employees` Table:**

| EmployeeID | FirstName | LastName | Salary | DepartmentID |
|------------|-----------|----------|--------|--------------|
| 1          | John      | Doe      | 60000  | 1            |
| 2          | Jane      | Smith    | 75000  | 1            |
| 3          | Emily     | Jones    | 50000  | 2            |
| 4          | Chris     | Brown    | 90000  | 2            |
| 5          | Michael   | Davis    | 65000  | NULL         |

**`Departments` Table:**

| DepartmentID | DepartmentName |
|--------------|----------------|
| 1            | Engineering    |
| 2            | Marketing      |
| 3            | Sales          |

---

### 1. Basic SQL Queries

- **`SELECT` and `FROM`**: Retrieve all employees.
  ```sql
  SELECT * FROM Employees;
  ```

- **`WHERE`**: Retrieve employees with a salary greater than 70000.
  ```sql
  SELECT FirstName, LastName, Salary FROM Employees WHERE Salary > 70000;
  ```

- **`ORDER BY`**: Retrieve all employees, ordered by their salary in descending order.
  ```sql
  SELECT FirstName, LastName, Salary FROM Employees ORDER BY Salary DESC;
  ```

- **`GROUP BY` and `HAVING`**: Find departments with more than one employee.
  ```sql
  SELECT DepartmentID, COUNT(EmployeeID) as NumberOfEmployees
  FROM Employees
  GROUP BY DepartmentID
  HAVING COUNT(EmployeeID) > 1;
  ```

---

### 2. JOINs

- **`INNER JOIN`**: Retrieve employees and their department names.
  ```sql
  SELECT Employees.FirstName, Departments.DepartmentName
  FROM Employees
  INNER JOIN Departments ON Employees.DepartmentID = Departments.DepartmentID;
  ```
  *Result will include John, Jane, Emily, and Chris.*

- **`LEFT JOIN`**: Retrieve all employees and their department names, including employees without a department.
  ```sql
  SELECT Employees.FirstName, Departments.DepartmentName
  FROM Employees
  LEFT JOIN Departments ON Employees.DepartmentID = Departments.DepartmentID;
  ```
  *Result will include Michael Davis with a NULL DepartmentName.*

- **`RIGHT JOIN`**: Retrieve all departments and the employees in them.
  ```sql
  SELECT Employees.FirstName, Departments.DepartmentName
  FROM Employees
  RIGHT JOIN Departments ON Employees.DepartmentID = Departments.DepartmentID;
  ```
  *Result will include the 'Sales' department with a NULL FirstName.*

- **`FULL OUTER JOIN`**: Retrieve all employees and all departments, matching where possible.
  ```sql
  SELECT Employees.FirstName, Departments.DepartmentName
  FROM Employees
  FULL OUTER JOIN Departments ON Employees.DepartmentID = Departments.DepartmentID;
  ```
  *Result will include Michael (no department) and Sales (no employees).*

---

### 3. Aggregate Functions

- **`COUNT()`**: Count the total number of employees.
  ```sql
  SELECT COUNT(*) FROM Employees;
  ```

- **`SUM()`**: Calculate the total salary expense for the 'Engineering' department.
  ```sql
  SELECT SUM(Salary)
  FROM Employees
  WHERE DepartmentID = 1;
  ```

- **`AVG()`**: Calculate the average salary of all employees.
  ```sql
  SELECT AVG(Salary) FROM Employees;
  ```

- **`MAX()` / `MIN()`**: Find the highest and lowest salaries.
  ```sql
  SELECT MAX(Salary), MIN(Salary) FROM Employees;
  ```

---

### 4. Subqueries (Nested Queries)

- **Find employees whose salary is above the company average.**
  ```sql
  SELECT FirstName, Salary
  FROM Employees
  WHERE Salary > (SELECT AVG(Salary) FROM Employees);
  ```

- **Find employees who work in the 'Marketing' department (using a subquery).**
  ```sql
  SELECT FirstName
  FROM Employees
  WHERE DepartmentID IN (SELECT DepartmentID FROM Departments WHERE DepartmentName = 'Marketing');
  ```
