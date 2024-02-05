## SQL (Structured Query Language) Syntax

### SQL Commands
- DDL: Data Definition Language, which deals with database schemas and descriptions, of how the data should reside in the database. CREATE, ALTER, DROP, TRUNCATE, COMMENT; RENAME
- DML: Data Manipulation Language, which deals with data manipulation. SELECT, INSERT, UPDATE, DELETE, MERGE
  
### SQL Statements
- SELECT * FROM datebaseName
- SELECT columnName FROM databaseName
- SELECT DISTINCT columnName FROM databaseName: get a list of the different values
- Create a new SQL database with the name databasename
  ```
   CREATE DATABASE databasename;
  ```
- Drop an existing SQL database with the name databasename
  ```
   DROP DATABASE databasename;
  ```
- Create table
  ```
   CREATE TABLE tablename(
      column1 datatype,
      column2 datatype,
      ...
    );
  ```
