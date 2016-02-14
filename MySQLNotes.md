# MySQL Bootcamp

## Lesson Objectives

1. What does SQL Stand for?  What is it?
1. What is a DB?
1. What are the different ways to store data?
1. What are the advantages of a database?
1. Diagram MySQL structure
1. Connect to MySQL
1. Create a DB
1. CRUD
1. Operators
1. AND/OR
1. ORDER BY
1. OFFEST/LIMIT
1. ALTER
1. GROUP BY

```sql
-- CREATE DB/TABLES
SHOW DATABASES;
CREATE DATABASE users;
USE users;
CREATE TABLE employees (first_name VARCHAR(20), age INT);
DESCRIBE employees;

-- CRUD
INSERT INTO employees (first_name, age) VALUES ('Matt' , 34);
SELECT age FROM employees;
SELECT * FROM employees;
UPDATE employees SET weight = 300 WHERE first_name = 'Bill';
DELETE FROM employees WHERE first_name = "Bill";

-- OPERATORS
SELECT * FROM employees WHERE age != 63;
SELECT * FROM employees WHERE age < 63;
SELECT * FROM employees WHERE age > 63;
SELECT * FROM employees WHERE age >= 63;
SELECT * FROM employees WHERE age <= 63;
SELECT * FROM employees WHERE first_name first_name LIKE "%Charlie%";
SELECT * FROM employees WHERE first_name NOT LIKE "%Charlie%";
SELECT * FROM employees WHERE age IS NULL;
SELECT * FROM employees WHERE age IS NOT NULL;


-- AND/OR
SELECT * FROM users WHERE first_name = 'Matt' AND age = 43;
SELECT * FROM users WHERE first_name = 'Matt' OR age = 49;

-- ORDER
SELECT * FROM employees ORDER BY age DESC;
SELECT * FROM employees ORDER BY age ASC LIMIT 2;
SELECT * FROM employees ORDER BY age ASC LIMIT 2 OFFSET 1;
SELECT * FROM employees ORDER BY age DESC, first_name ASC;

-- ALTER TABLE
ALTER TABLE employees ADD COLUMN weight FLOAT;
ALTER TABLE employees DROP COLUMN height;
ALTER TABLE employees ADD COLUMN height FLOAT AFTER first_name;
ALTER TABLE employees MODIFY COLUMN height FLOAT AFTER age;
ALTER TABLE employees ADD COLUMN id INT FIRST;
ALTER TABLE employees ADD COLUMN dob DATETIME;
ALTER TABLE employees CHANGE dob date_of_birth DATETIME;
ALTER TABLE companies ADD COLUMN id INT NOT NULL AUTO_INCREMENT PRIMARY KEY FIRST;

-- AGGREGATION
SELECT COUNT(*), age FROM employees GROUP BY age;
SELECT SUM(salary), age FROM employees GROUP BY age;
SELECT AVG(salary) FROM employees GROUP BY age;
SELECT MIN(salary) FROM employees GROUP BY age;
SELECT MAX(salary) FROM employees GROUP BY age;
SELECT GROUP_CONCAT(first_name) FROM employees GROUP BY age;
SELECT GROUP_CONCAT(first_name), age, height FROM employees GROUP BY age, height;

-- JOINS
SELECT * from employees FULL JOIN companies;
SELECT * FROM employees JOIN companies ON employees.`employer_id` = companies.`id`;
SELECT * FROM employees RIGHT OUTER JOIN companies ON employees.`employer_id` = companies.id WHERE employees.`employer_id` IS NULL;
SELECT * FROM employees LEFT OUTER JOIN companies ON employees.`employer_id` = companies.id WHERE employees.`employer_id` IS NULL;
SELECT employees.*, companies.`name` FROM employees INNER JOIN companies ON employees.`employer_id` = companies.id;
SELECT e.*, c.name AS company_name FROM employees AS e INNER JOIN companies AS c ON e.employer_id = c.id;
```
