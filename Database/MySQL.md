## MySQL Database
- MySQL Database Server: main engine of the database
- MySQL Workbench: client GUI for interacting with the database

## Add MySQL in Spring project
- Add dependency in Maven: MySQL Driver: mysql-connector-j
- Add database connection info in application.properties
  ```
  // Spring use JDBC for mySQL database communication
  spring.datasource.url=jdbc:mysql://localhost:3306/student_tracker
  spring.datasource.username=springstudent
  spring.datasource.password=springstudent
  ```


## Commands
- Create new user
- Create a new database

### Primary key
- uniquely identifies each row in a table
- must be a unique value
- cannot contain NULL values
