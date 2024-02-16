## SQL (Structured Query Language)
SQL is database language for the relational database. With SQL can man access and manipulate database.

### SQL Commands
- DDL: Data Definition Language, which deals with database schemas and descriptions, of how the data should reside in the database. CREATE, ALTER, DROP, TRUNCATE, COMMENT; RENAME
- DML: Data Manipulation Language, which deals with data manipulation. SELECT, INSERT, UPDATE, DELETE, MERGE
  
### SQL Statements (SQL keywords are not case sensitive, end with semicolon)
- **SELECT**: extracts data from a database
  ```
  // return all columns from the table tableName
  SELECT * FROM tableName;
  // return column1 and column2 from the table tableName
  SELECT columnq, column2 FROM tableName;
  // return only distinct (different) values
  SELECT DISTINCT columnName FROM databaseName;
  ```
- **UPDATE**: updates existing records in a table
  ```
  UPDATE tableName
  SET column1=value1, column2=value2,...
  WHERE condition;
  ```
- **DELETE**: deletes existing records in a table
  ```
  DELETE FROM tableName WHERE condition;
  ```
- **INSERT INTO**: inserts new data into a database
  ```
  INSERT INTO tableName(column1, column2, column3,...)
  VALUES
  (value1, value2, value3,...),
  (value1a, value2a, value3a,...),
  (value1b, value2b, value3b,...);
  ```
- **CREATE DATABASE**: is used to create a new database
  ```
  // Create a new SQL database with the name databasename
  CREATE DATABASE databasename;
  ```
- **DROP DATABASE**: is used to drop an existing SQL database
  ```
  DROP DATABASE databasename;
  ```
- **BACKUP DATABASE**: is used in SQL SERVER to create a full back up of an existing SQL database
  ```
  BACKUP DATABASE databasename
  TO DISK = 'filepath';
  ```
- **ALTER DATABASE**: modifies a database
- **CREATE TABLE**: is used to create a new table in a database.
  ```
   CREATE TABLE tablename(
      column1 datatype,
      column2 datatype,
      ...
    );
  ```
- **ALTER TABLE**: is used to add, delete or modify columns in an existing table.
  ```
  ALTER TABLE tableName
  ADD columnName datatype
  DROP COLUMN columnName
  RENAME COLUMN oldName to newName
  ALTER COLUMN columnName datatype // SQL SERVER, MS Access
  MODIFY COLUMN columnName datatype // MySQL, Oracle
  ```
- **DROP TABLE**: is used to drop an existing table completetly
  ```
  DROP TABLE tableName;
  ```
- **TRUNCATE TABLE**: is used to delete the data inside a table, but not the table itself.
  ```
  TRUNCATE TABLE tableName;
  ```
- **CREATE INDEX**: creates an index (search key)
- **DROP INDEX**: deletes an index
- **WHERE** clause: is used to filter records. SQL requires single quetos around text values.
  ```
  SELECT column1 FROM tableName WHERE condition;
  ```
  ***Operator*** in the WHERE clause: =, >, <, >=, <=, <>, BETWEEN, LIKE, IN
- **ORDER BY**: is used to sort the result in ascending or descending order. Default is ascending. Use **DESC** to sort the records in descending.
  ```
  SELECT * FROM tableName
  ORDER BY column1 ASC, column2 DESC;
  ```
- **AND**, **OR**: WHERE clause can contain one or many AND, OR operators.
  AND displays a record if all the conditions are TRUE.
  OR displays a record if any of the conditions are TRUE.
  ```
  SELECT column1, column2 FROM tableName WHERE condition1 AND (condition2 OR condition3);
  ```
- **NO**: use it with **Operators** in the **WHERE** clause.
- **IS NULL**: is used to test for empty values (NULL values).
  ```
  SELECT columnName
  FROM tableName
  WHERE columnName IS NULL;
  ```
- **IS NOT NULL**: is used to test for non-empty values (NOT NULL values).
  ```
  SELECT columnName
  FROM tableName
  WHERE columnName IS NOT NULL;
  ```
- **SQL Constraints**: can be specified when the table is created with CREATE TABLE statements, or after the table is created with the ALTER TABLE statement.
  - **NOT NULL**: Ensures that a column cannot have a NULL value
  - **UNIQUE**: Ensures that all values in a column are different
  - **PRIMARY KEY**: A combination of a NOT NULL and UNIQUE. Uniquely identifies each row in a table
  - **FOREIGN KEY**: Prevents actions that would destroy links between tables
  - **CHECK**: Ensures that the values in a column satisfies a special condition.
  - **DEFAULT**: Sets a default value for a column if no value is specified
  - **CREATE INDEX**: Used to create and retrieve data from the database very quickly
