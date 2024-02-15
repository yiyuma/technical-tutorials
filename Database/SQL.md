## SQL (Structured Query Language)
With SQL can man access and manipulate database.

### SQL Commands
- DDL: Data Definition Language, which deals with database schemas and descriptions, of how the data should reside in the database. CREATE, ALTER, DROP, TRUNCATE, COMMENT; RENAME
- DML: Data Manipulation Language, which deals with data manipulation. SELECT, INSERT, UPDATE, DELETE, MERGE
  
### SQL Statements (SQL keywords are not case sensitive)
- SELECT: extracts data from a database
  ```
    SELECT * FROM datebaseName
    SELECT columnName FROM databaseName
    // get a list of the different values
    SELECT DISTINCT columnName FROM databaseName
  ```
- UPDATE: updates data in a database
- DELETE: deletes data from a database
- INSERT INTO: inserts new data into a database
- CREATE DATABASE: creates a new database
  ```
    // Create a new SQL database with the name databasename
    CREATE DATABASE databasename;
  ```
- ALTER DATABASE: modifies a database
- DROP DATABAS: deletes a database
  ```
    DROP DATABASE databasename;
  ```
- CREATE TABLE: creates a new table
  ```
   CREATE TABLE tablename(
      column1 datatype,
      column2 datatype,
      ...
    );
  ```
- ALTER TABLE: modifies a table
- DROP TABLE: deletes a table
- CREATE INDEX: creates an index (search key)
- DROP INDEX: deletes an index
