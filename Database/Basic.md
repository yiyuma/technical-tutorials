## Database
Database can store and manage data.<br>

## DBMS (Database Management System)
Database Management System(DBMS): Software, which we can connect, query and manage the database.
- relational: RDBMS (Relational Database Management System)
- NoSQL

## RDBMS
RDBMS (MySQL, PostegreSQL...) is the basis for SQL. 
- database: Relational database is a collection of table. (table is relation)
- table: A table is a collection of related data entries and it consists of columns and rows.
- column: A field (attribut) is a column in a table that is designed to maintain specific information about the every record in the table.
- row: A record called a row. It is each individual entry that exists in a table.

## SQL (Structured Query Language)
SQL is database language for the relational database. With SQL can man access and manipulate database.

### SQL Commands
- DDL: Data Definition Language, which deals with database schemas and descriptions of how the data should reside in the database. CREATE, ALTER, DROP, TRUNCATE, COMMENT; RENAME
- DML: Data Manipulation Language, which deals with data manipulation. SELECT, INSERT, UPDATE, DELETE, MERGE
  
## JDBC (Java DataBase Connectivity)
JDBC is an API for conncecting and executing queries on a database for Java. JDBC can work with any database as long as proper drivers are provided.

### JDBC Driver
JDBC Driver is a JDBC implementation used for connecting to a database.
To use JDBC Driver, you have to do:
- Registering the Driver
- Creating the connection

### MySQL in Spring
For MySQL you have to
- Registering the Driver: 
  Add MySQL Driver **mysql-connector-j** in pom.xml file.
- Creating the connection:
  Add MySQL Connection in the application.properites file.
  ```
  spring.datasource.url=jdbc:mysql://localhost:3306/DBMS_name
  spring.datasource.username=username
  spring.datasource.password=password
  ```
  DataSource is a factory for connections to a physical database.

### PostgreSQL in Spring
For PostgreSQL you have to
- Registering the Driver: 
  Add PostgreSQL Driver in Maven: PostgreSQL Driver: **postgresql**
- Creating the connection:
  Add database connection info in application.properties
  ```
  // Spring use JDBC for PostgreSQL database communication
  spring.datasource.url=jdbc:postgresql://localhost:5432/DBMS_name
  spring.datasource.username=username
  spring.datasource.password=password
  ```
