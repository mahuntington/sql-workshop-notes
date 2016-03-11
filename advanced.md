# PostGres - Advanced

## Lesson Objectives - important
1. Joins
1. Linking Tables
1. Alias
1. Indexes
1. Constraints

## Lesson Objectives - good to know about
1. EER Diagrams
1. Unions
1. Truncate
1. Triggers
1. Views
1. Functions/Stored Procedures
1. Transactions
1. Locks
1. Privileges
1. Denormalization
1. Excel -> CSV -> MySQL

## Important

### Joins
1. Cross Join
1. Inner Join
1. Left Join
1. Right Join
1. Full Join
```sql
SELECT table1.column1, table2.column2
FROM table1
INNER JOIN table2
ON table1.common_filed = table2.common_field;
```

### Linking Tables
1. `http://code.tutsplus.com/articles/sql-for-beginners-part-3-database-relationships--net-8561`
1. One to One Relationships
	- each user has one address
	- only one person at that address
1. One to Many/Many to One Relationships
	- customer has many orders
1. Many to Many Relationships
	- actors and movies
1. Self Referncing Relationships
	- customer referral

### Alias
```sql
SELECT t1.column1 as col1, t2.column2 as col2
FROM table1 as t1
INNER JOIN table2 as t2
ON t1.common_filed = t2.common_field;
```

### Indexes
1. `CREATE INDEX index_name ON table_name (column_name);`
1. `CREATE INDEX index_name ON table_name (column1_name, column2_name);`
1. Primary Key

### Constraints
1. NOT NULL	
1. Unique
1. Foreign Keys
```sql
CREATE TABLE companies(
  id          SERIAL       PRIMARY KEY,
  name        VARCHAR(16)  NOT NULL UNIQUE,
  city        VARCHAR(16)
);
INSERT INTO companies ( city ) VALUES ('Palo Alto');
CREATE TABLE people(
  id          INT          PRIMARY KEY,
  name        VARCHAR(16)  NOT NULL,
  email       VARCHAR(32)  NOT NULL UNIQUE,
  company_id  INT          REFERENCES companies(id)
);
```

## Good to Know About

### EER Diagrams

### Unions

### Truncate

### Triggers

### Views

### Functions/Stored Procedures

### Transactions

### Locks

### Privileges

### Denormalization

### Excel -> CSV -> MySQL

### SQL Injection
