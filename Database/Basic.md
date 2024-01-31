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
