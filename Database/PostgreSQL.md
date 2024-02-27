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
- Always end SQL statements with a semicolon ;. SQL Shell waits for the semicolon and excutes all lines as one SQL statement.


## SQL Statements
- Check database version
  ```
  SELECT version();
  ```
- Check current user
  ```
  SELECT current_user;
  ```
- Check current database
  ```
  SELECT current_database();
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
    CREATE ROLE newUser WITH LOGIN PASSWORD 'password';
    ```
  - Create a new superuser with password
    ```
    CREATE ROLE newSuperuser WITH LOGIN PASSWORD 'password' SUPERUSER;
    ```
  - Create a new user with specific permission
    - CREATEDB: Allows the user to create databases
    - CREATEROLE: Allows the user to create roles (or users)
    - NOCREATEDB: Prevents the user to create databases
    - NOCREATEROLR: Prevents the user to create roles (or users)
    ```
    CREATE ROLE newUser WITH LOGIN PASSWORD 'password' CREATEDB CREATEROLE;
    ```
  - INHERIT: Allows the user to inherit permissions from roles it is a member of. This is the default
  - VALID UTIL 'timestamp': The user's password will expire at the specified time.
     ```
    CREATE ROLE newUser WITH LOGIN PASSWORD 'password' CREATEDB CREATEROLE VALID UNTIL '2025-01-01';
    ```
  - Changes password
    ```
    ALTER ROLE newUser WITH PASSWORD 'newPassword';
    ```
- Check user list
  ```
  // in psql. du = describe user
  \du
  // in terminal
  psql -c '\du'
- Create a new database
  ```
  CREATE DATABASE newDBName;
  ```
- List all databases currently on the server
  ```
  // list all databases with details currently on the server
  \l
  // list all database name currently on the server
  SELECT datname FROM pg_database;
  ```
- Switch to another database
  ```
  // in psql. c = connect
  \c newDatabase
  ```
- Create table
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
- Check table
  ```
  \d // list all table and sequence
  \dt // list all table
  \d tableName // show the details of the table tableName
  ```
- Dorp table
  ```
  DROP TABLE tableName;
  ```
- Insert records
  ```
  INSERT INTO shoppingCategory(name)
  VALUES('Foods');
  ```
## Datatype
- INT
- VARCHAR
- DATE
- TIMESTEMP
- BIGSERIAL

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
