## PostgreSQL
PostgreSQL is an free open-source database system that supports both relational (SQL) and non-relational (JSON) queries. PostgreSQL is a back-end database for dynamic websites and web applications.

## PostgreSQL Installation
- Link: https://www.postgresql.org/download/
- Dokumentation: https://www.postgresql.org/docs/
- Default port: 5432
- Components
  - PostgreSQL Server: main engine of the database
  - pgAdmin4: client GUI for interacting with the database
  - SQL Shell (Command Line Tools): a terminal based program where you can write and execute SQL syntax in the commandline terminal.

## Connect to the Database
Two ways to connect to the database:
- SQL Shell (psql)
- pgAdmin4

## Note
- Relation means table in the database
- Always end SQL statements with a semicolon ;. SQL Shell waits for the semicolon and excutes all lines as one SQL statement.
- PostgreSQL requires quotes around text value. Numeric fields should without quotes.

## SQL Statements
- Check database version
  ```
  SELECT version();
  ```
  
- Check current database
  ```
  SELECT current_database();
  ```
  
- List all databases currently on the server
  ```
  // list all database name currently on the server
  SELECT datname FROM pg_database; // datname, pg_database will be fixed here
  ```
  
- Check current user
  ```
  SELECT current_user;
  ```
  
- Create User
  ```
  CREATE ROLE "newUser" WITH
  	NOLOGIN
  	NOSUPERUSER
  	NOCREATEDB
  	NOCREATEROLE
  	INHERIT
  	NOREPLICATION
  	CONNECTION LIMIT -1;
  ```
  - Create a new basic user with password
    ```
    CREATE ROLE newUsername WITH LOGIN PASSWORD 'password';
    ```
  - Create a new superuser with password
    ```
    CREATE ROLE newSuperusername WITH LOGIN PASSWORD 'password' SUPERUSER;
    ```
  - Create a new user with specific permission
    - CREATEDB: Allows the user to create databases
    - CREATEROLE: Allows the user to create roles (or users)
    - NOCREATEDB: Prevents the user to create databases
    - NOCREATEROLR: Prevents the user to create roles (or users)
    ```
    CREATE ROLE newUsername WITH LOGIN PASSWORD 'password' CREATEDB CREATEROLE;
    ```
  - INHERIT: Allows the user to inherit permissions from roles it is a member of. This is the default
  - VALID UTIL 'timestamp': The user's password will expire at the specified time.
     ```
    CREATE ROLE newUsername WITH LOGIN PASSWORD 'password' CREATEDB CREATEROLE VALID UNTIL '2025-01-01';
    ```
  - Changes password
    ```
    ALTER ROLE username WITH PASSWORD 'newPassword';
    ```


- Check user list
  ```
  // in psql. du = describe user
  \du
  // in terminal
  psql -c '\du'
  ```
  
- List all databases currently on the server
  ```
  // list all databases with details currently on the server
  \l
  // list all database name currently on the server
  SELECT datname FROM pg_database; // datname, pg_database will be fixed here
  ```
  
- Switch to another database
  ```
  // in psql. c = connect
  \c newDatabase
  ```
  
- Check table
  ```
  \d // list all table and sequence
  \dt // list all table
  \d tableName // show the details of the table tableName
  ```
  
- CREATE DATABASE: Create a new database
  ```
  CREATE DATABASE newDBName;
  ```
- Edit with **TABLE**
  - CREATE TABLE
    ```
    CREATE TABLE table_name(
      Column name + data type + constraints if any
    )
    // create table for the catagory
    CREATE TABLE ShoppingCategory(
      id BIGSERIAL NOT NULL PRIMARY KEY,
      name VARCHAR(255) NOT NULL,
      );
    ```
  - DROP TABLE: Delete table in a database. The records in the table will also be deleted.
    ```
    DROP TABLE tableName;
    ```
  - ALTER TABLE: is used to add, delete, or modify columns in an existing table, add and drop various   constraints on an existing table.
    ```
    // Add column
    ALTER TABLE tableName
    ADD newColumn VARCHAR(255);

    // Alter column: change the type of COLUMN columnName auf INT. Some data types cannot be converted if the column has value. Numbers can always be converted to text. but text cannot always be converted to numbers.
    ALTER TABLE tableName
    ALTER COLUMN columnName TYPE INT;

    // Drop column: remove an existing column
    ALTER TABLE tableName
    DROP COLUMN columnName;
    ```

- Edit with **RECORD**
  - INSERT INTO statement: Insert new record in a table
    ```
    INSERT INTO shoppingCategory(name)
    VALUES('Foods'),
          ('Toys'),
          ('Books');
    ```
  - UPDATE statement: is used to modify the value in existing records in a table.
    ```
    UPDATE tableName
    SET columnName='newValue'
    WHERE anotherColumnName='value';
    ```
  - DELETE statement: is used to delete existing records in a table
    ```
    // delete the records which the columnname is value
    DELETE FROM tableName
    WHERE columnName='value';

    // delelte all records in the table
    DELETE FROM tableName;
    ```
  - TRUNCATE TABLE: delete all records in the table
    ```
    TRUNCATE TABLE tableName;
    ```

- **Query** data
  - SELECT statements: to retrieve data from a database.
    ```
    // display all in the tableName
    SELECT * FROM tableName;
    // display column1 and column2 in the tableName
    SELECT column1, column2 FROM tableName;
    // display only different values from the columnName
    SELECT DISTINCT columnName FROM tableName;
    // display the count of the column with different values
    SELECT COUNT(DISTINCT columnName) FROM tableName;
    ```
- **Sort** data
  - ORDER BY: is used to sort the result in ascending or descending order.
    ```
    SELECT * FROM tableName
    ORDER BY columnName; // ascending is default
    ORDER BY columnName DESC; // DESC means descending
    ```
- LIMIT clause: is used to limit the maximum number of records to return
- OFFSET Clause: is used to specify where to start selecting the records to return. The first record is number 0.
- MIN() function returns the smallest value of the selected column
- MAX() function returns the larest value of the selected column. When you use MIN() or MAX(), the returned column will be named min or max by default. To give the column a new name, use the AS keyword.
   
## Datatype
- INT
- VARCHAR
- DATE
- TIMESTEMP
- BIGSERIAL

## Operators in the WHERE clause. WHERE clause is used to filter records.
- =: Equal to
- <: Less than
- \>: Greater than
- <=: Less than or equal to
- \>=: Greater than or equal to
- <>: Not equal to
- !=: Not equal to
- LIKE: Check if a value matches a pattern (case sensitive). % presents zero, one or multiple characters. _ represents one single character.
  ```
  SELECT * FROM tableName
  WHERE columnName LIKE 'M%';
  ```
- ILIKE: Check if a value matches a pattern (case insensitive)
- AND: Logical AND
- OR: Logical OR
- IN: Check if a value is between a range of values
  ```
  SELECT * FROM tableName
  WHERE columnName IN ('value1', 'value2', 'value3');
  ```
- BETWEEN: Check if a value is between a range of values
  ```
  SELECT * FROM tableName
  WHERE columnName BETWEEN value1 AND value2;
  ```
- IS NULL: Check if a value is NULL
- NOT: Makes a negative result, NOT LIKE, NOT IN, NOT BETWEEN, NOT NULL


## Constraints
- NOT NULL
- PRIMARY KEY
- 
## Add MySQL in Spring project
- Add dependency in Maven: MySQL Driver: mysql-connector-j
- Add database connection info in application.properties
  ```
  // Spring use JDBC for mySQL database communication
  spring.datasource.url=jdbc:mysql://localhost:5432/student_tracker
  spring.datasource.username=springstudent
  spring.datasource.password=springstudent
  ```

### Primary key
- uniquely identifies each row in a table
- must be a unique value
- cannot contain NULL values
  
## Mock data to test
https://mockaroo.com/
