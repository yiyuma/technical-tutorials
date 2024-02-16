## Database
Database can store and manage data.<br>

## Database system
- Database
- Database Management System(DBMS): Software, which we can connect, query and manage the database.

## DBMS (Database Management System)
- relational: RDBMS (Relational Database Management System)
- NoSQL

## RDBMS
RDBMS (MySQL, PostegreSQL...) is the basis for SQL. 
- database: Relational database is a collection of table. (table is relation)
- table: The data in RDBMS is stored in database objects called tables. A table is a collection of related data entries and it consists of columns and rows.
- column: A field is a column in a table that is designed to maintain specific information about the every revord in the table.
- row: A record called a row. It is each individual entry that exists in a table.

## JDBC (Java DataBase Connectivity)
JDBC is an API for conncecting and executing queries on a database for Java. JDBC can work with any database as long as proper drivers are provided.

### JDBC Driver
JDBC Driver is a JDBC implementation used for connecting to a database.
To use JDBC Driver, you have to do:
- Registering the Driver
- Creating the connection

### MySQL in Spring
For MySQL you have to

Registering the Driver: 
- Add MySQL Driver "mysql-connector-j" in pom.xml file.
Creating the connection:
- Add MySQL Connection in the application.properites file.
  ```
  spring.datasource.url=jdbc:mysql://localhost:3306/DBMS_name
  spring.datasource.username=user
  spring.datasource.password=password
  ```
  DataSource is a factory for connections to a physical database.
