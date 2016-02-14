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
CREATE DATABASE our_database_name;
USE our_database_name;
CREATE TABLE people (first_name VARCHAR(20), age INT);
DESCRIBE people;

-- CRUD
INSERT INTO people (first_name, age) VALUES ('Matt' , 34);
SELECT age FROM people;
SELECT * FROM people;
UPDATE people SET weight = 300 WHERE first_name = 'Bill';
DELETE FROM people WHERE first_name = "Bill";

-- OPERATORS
SELECT * FROM people WHERE age != 63;
SELECT * FROM people WHERE age < 63;
SELECT * FROM people WHERE age > 63;
SELECT * FROM people WHERE age >= 63;
SELECT * FROM people WHERE age <= 63;
SELECT * FROM people WHERE first_name first_name LIKE "%Charlie%";
SELECT * FROM people WHERE first_name NOT LIKE "%Charlie%";
SELECT * FROM people WHERE age IS NULL;
SELECT * FROM people WHERE age IS NOT NULL;


-- AND/OR
SELECT * FROM people WHERE first_name = 'Matt' AND age = 43;
SELECT * FROM people WHERE first_name = 'Matt' OR age = 49;

-- ORDER
SELECT * FROM people ORDER BY age DESC;
SELECT * FROM people ORDER BY age ASC LIMIT 2;
SELECT * FROM people ORDER BY age ASC LIMIT 2 OFFSET 1;
SELECT * FROM people ORDER BY age DESC, first_name ASC;

-- ALTER TABLE
ALTER TABLE people ADD COLUMN weight FLOAT;
ALTER TABLE people DROP COLUMN height;
ALTER TABLE people MODIFY COLUMN height FLOAT;

ALTER TABLE people ADD COLUMN height FLOAT AFTER first_name;
ALTER TABLE people MODIFY COLUMN height FLOAT AFTER age;

ALTER TABLE people ADD COLUMN id INT FIRST;
ALTER TABLE people MODIFY COLUMN height FLOAT FIRST;

ALTER TABLE people ADD COLUMN dob DATETIME;
ALTER TABLE people CHANGE dob date_of_birth DATETIME;

ALTER TABLE people ADD COLUMN id INT NOT NULL AUTO_INCREMENT PRIMARY KEY FIRST;

-- AGGREGATION
SELECT COUNT(*), age FROM people GROUP BY age;
SELECT SUM(salary), age FROM people GROUP BY age;
SELECT AVG(salary) FROM people GROUP BY age;
SELECT MIN(salary) FROM people GROUP BY age;
SELECT MAX(salary) FROM people GROUP BY age;
SELECT GROUP_CONCAT(first_name) FROM people GROUP BY age;
SELECT GROUP_CONCAT(first_name), age, height FROM people GROUP BY age, height;

-- JOINS
SELECT * FROM people JOIN companies ON people.employer_id = companies.id;
SELECT * from people JOIN companies;
SELECT * FROM people RIGHT OUTER JOIN companies ON people.employer_id = companies.id;
SELECT * FROM people LEFT OUTER JOIN companies ON people.employer_id = companies.id;
```
