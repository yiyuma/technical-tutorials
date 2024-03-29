## PostgreSQL
PostgreSQL is an free open-source database system that supports both relational (SQL) and non-relational (JSON) queries. PostgreSQL is a back-end database for dynamic websites and web applications.

## PostgreSQL Installation
- Link: https://www.postgresql.org/download/
- Documentation: https://www.postgresql.org/docs/
- Default port: 5432
- Components
  - PostgreSQL Server: main engine of the database
  - pgAdmin4: client GUI for interacting with the database
  - SQL Shell (Command Line Tools): a terminal based program where you can write and execute SQL syntax in the commandline terminal.

## Connect to the PostgreSQL Database Server
Different ways to connect to the database:
- SQL Shell (psql)
- pgAdmin4
- JDBC Driver
  - Add dependency in Maven: PostgreSQL Driver: postgresql
  - Add database connection info in application.properties
    ```
    // Spring use JDBC for PostgreSQL database communication
    spring.datasource.url=jdbc:postgresql://localhost:5432/student_tracker
    spring.datasource.username=springstudent
    spring.datasource.password=springstudent
    ```

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
- Show the IP address and port of the current connection
  ```
  SELECT inet_server_addr(), inet_server_port();
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
- Edit with **TABLE**: CREATE, DROP, ALTER
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

- Edit with **RECORD**: INSERT INTO, UPDATE, DELETE, TRUNCATE
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
  - TRUNCATE TABLE statement: delete all records in the table
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
  ```
  SELECT * FROM tableName
  LIMIT 20 OFFSET 40 // return 20 records, starting from the 41th record
  ```
- **Functions**
  - MIN() function returns the smallest value of the selected column
  - MAX() function returns the larest value of the selected column. When you use MIN() or MAX(), the returned column will be named min or max by default. To give the column a new name, use the AS keyword.
   - COUNT() function returns the number of rows that matches a specified criterion. NULL values are not counted
   - SUM() function returns the total sum of a numeric column. Null values are ignored.
   - AVG() function returns the average value of a numeric column. With ::NUMERIC operator to define the numner with decimal.
 
- Aliases: are used to give a table, or a column in a table, a temporary name. An alias only exists for the duration of that query. An alias is created with the AS keyword. If you want your alias to contain one or more spaces, surround your alias with double quotes. Keyword AS is often used when two or more fields are concatenated into one.

- JOIN: is used to combine rows from two or more tables,  based on a related column between them. JOIN is used with ON
  - INNER JOIN: returns records that have matching values in both tables. INNER JOIN and JOIN will gie the same result. INNER is the default join type.
  - LEFT JOIN: returns all records from the left table, and the matched records from the right table. LEFT JOIN and LEFT OUTER JOIN will gie the same result. OUTER is the default join type.
  - RIGHT JOIN: returns all records from the right table, and the matched records from the left table. RIGHT JOIN and RIGHT OUTER JOIN will gie the same result. OUTER is the default join type.
  - FULL JOIN: returns all records when there is a match in either left or right table. If there is not a match the empty fields will get the value NULL. FULL JOIN and FULL OUTER JOIN will gie the same result. OUTER is the default join type.
  - CROSS JOIN: matches all records from the left table with each record from the right table.
    ```
    SELECT column1, column2 FROM table1 (INNER|LEFT|RIGT|FULL) JOIN table2 ON table1.id=table2.id;
    SELECT column1, column2 FROM table1 CROSS JOIN table2;
    ```

- UNION Operator: is used to combine the result-set of two or more queries. The queries in the union must follow rules:
  - They must have the same number of columns
  - The columns must have the same data types
  - The columns must be in the same order
  With the UNION operator, if some rows in the two queries returns the exact same result, only one row will be listed, because UNION selects only distinct values. Use UNION ALL to return duplicate values.
  ```
    SELECT column1 FROM table1
    UNION
    SELECT column2 FROM table2
    ORDER BY column1;
  ```
- GROUP BY clause groups rows that have the same values into summary rows. The GROUP BY clause is often used with aggregate functions like COUNT(), MAX(), MIN(), SUM(), AVG() to group the result-set by one or more columns.

- HAVING clause was added to SQL because the WHERE clause cannot be used with aggregate functions. Aggregate functions are often used with GROUP BY clausees, and by adding HAVING we can write condition like we do with WHERE clauses.
- EXISTS operator is used to test for the existence of any record in a sub query. The EXIST operator returns TRUE if the sub query returns one or more records. We can use NOT operator with the EXISTS operator to check which sub query does not return records.
- ANY operator allows you to perform a comparison between a single column value and a range of other values. ANY operator returns a Boolean value as a result. It returns TRUE if ANY of the sub query values meet the condition.
- ALL Operator returns a Boolean value as a result. It returns TRUE if ALL of the sub query values meet the condition. It is used with SELECT, WHERE and HAVING statements.
- CASE expression goes through conditions and returns a value when the first condition is met. Once a condition is true, it will stop reading and return the result. If no conditions are true, ite returns the value in the ELSE clause. It there is no ELSE part and no conditions are true, it returns NULL.
  
## Datatype
- BOOLEAN (BOOL): is used one byte for storing. It can have three values: true, false, NULL.
  - for the "true" state: true, yes, on, 1
  - for the "false" state: false, no, off, 0
- Character types: CHAR, VARCHAR, TEXT
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
- IN: is used to specify a list of possible values in the WHERE clause. SELECT statement can inside of IN (IN(SELECT)).
  ```
  SELECT * FROM tableName
  WHERE columnName IN ('value1', 'value2', 'value3');
  ```
- BETWEEN AND: selects values within a given range. The values can be numbers, texts, or dates. The begin and end values are included.
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
### Primary key
- uniquely identifies each row in a table
- must be a unique value
- cannot contain NULL values
  
## Mock data to test
https://mockaroo.com/
