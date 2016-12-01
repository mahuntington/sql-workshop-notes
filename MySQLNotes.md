# MySQL Bootcamp

## Lesson Objectives

1. What is a DB?
1. What are the different ways to store data?
1. What are the advantages of a database?
1. What does SQL Stand for?  What is it?
1. Diagram MySQL structure

```sql
-- CREATE DB/TABLES
SHOW DATABASES; -- show all sub databases
CREATE DATABASE our_database_name; -- create a sub database
USE our_database_name; -- use that sub database
CREATE TABLE people (first_name VARCHAR(20), age INT); -- craete a table with a text first_name column and an integer age column
DESCRIBE people; -- look at the table's schema

-- CRUD
INSERT INTO people (first_name, age) VALUES ('Matt' , 34); -- insert a row into people table
SELECT age FROM people; -- find all people, display just the age column
SELECT * FROM people; --  find all people, display all columns
UPDATE people SET weight = 300 WHERE first_name = 'Bill'; -- set weight to 300 for all rows that have a first_name column set to Bill
DELETE FROM people WHERE first_name = "Bill"; -- delete all rows that have a first_name column set to Bill

-- OPERATORS
SELECT * FROM people WHERE age != 63; -- find all rows that have an age that doesn't equal 63
SELECT * FROM people WHERE age < 63; -- find all rows that have an age less than 63
SELECT * FROM people WHERE age > 63; -- find all rows that have an age greater than 63
SELECT * FROM people WHERE age >= 63; -- find all rows that have an age greater or equal to than 63
SELECT * FROM people WHERE age <= 63; -- find all rows that have an age less than or equal to than 63
SELECT * FROM people WHERE first_name LIKE "%Charlie%"; -- find all rows that have a first_name that contains the value Charlie
SELECT * FROM people WHERE first_name NOT LIKE "%Charlie%"; -- find all rows that have a first_name that does not contain the value Charlie
SELECT * FROM people WHERE age IS NULL; -- find all rows that do not have any value for the age column
SELECT * FROM people WHERE age IS NOT NULL; -- find all rows that have any value for the age column


-- AND/OR
SELECT * FROM people WHERE first_name = 'Matt' AND age = 43; -- find all rows that have a first name set to Matt AND also have an age set to 43
SELECT * FROM people WHERE first_name = 'Matt' OR age = 49; -- find all rows that either have a first_name set to Matt OR have an age set to 49

-- ORDER
SELECT * FROM people ORDER BY age DESC; -- find all rows, but sort them in order of decreasing age
SELECT * FROM people ORDER BY first_name DESC; -- find all rows, but sort them in order of decreasing first_name values (reverse alphabetal)
SELECT * FROM people ORDER BY age ASC LIMIT 2; -- limit the results to 2
SELECT * FROM people ORDER BY age ASC LIMIT 2 OFFSET 3; -- limit the results to 2, but don't show the first 3 records
SELECT * FROM people ORDER BY age DESC, first_name ASC; -- order by age descending, for any rows that have the same age value, order those rows by first_name ascending

-- ALTER TABLE
ALTER TABLE people ADD COLUMN weight FLOAT; -- add a weight column that is a FLOAT (decimal number)
ALTER TABLE people DROP COLUMN height; -- drop the height column
ALTER TABLE people MODIFY COLUMN height FLOAT; -- change the height column to be a FLOAT (decimal number)

ALTER TABLE people ADD COLUMN height FLOAT AFTER first_name; -- add a heigh column after the first_name column
ALTER TABLE people MODIFY COLUMN height FLOAT AFTER age; -- move an existing height column so that it is after the age column

ALTER TABLE people ADD COLUMN id INT FIRST; -- add an id column in the first position
ALTER TABLE people MODIFY COLUMN height FLOAT FIRST; -- move an existing height column to the first position

ALTER TABLE people ADD COLUMN dob DATETIME; -- create a dob column which is a date
ALTER TABLE people CHANGE dob date_of_birth DATETIME; -- change the name of the dob column to date_of_birth

ALTER TABLE people ADD COLUMN id INT NOT NULL AUTO_INCREMENT PRIMARY KEY FIRST; -- create an id column that increments with each new row created

-- AGGREGATION
SELECT COUNT(*), age FROM people GROUP BY age;
SELECT SUM(salary), age FROM people GROUP BY age;
SELECT AVG(salary), age FROM people GROUP BY age;
SELECT MIN(salary), age FROM people GROUP BY age;
SELECT MAX(salary), age FROM people GROUP BY age;
SELECT GROUP_CONCAT(first_name), age FROM people GROUP BY age;
SELECT GROUP_CONCAT(first_name), age, height FROM people GROUP BY age, height;

-- JOINS
SELECT * FROM people JOIN companies ON people.employer_id = companies.id;
SELECT * from people JOIN companies;
SELECT * FROM people RIGHT JOIN companies ON people.employer_id = companies.id;
SELECT * FROM people LEFT JOIN companies ON people.employer_id = companies.id;
```
