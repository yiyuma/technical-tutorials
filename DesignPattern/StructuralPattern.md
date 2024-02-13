## Data Access Object (DAO)

- DAO is a structural pattern.
- DAO is an abstract API.
- DAO allows us to isolate the application/business layout from the persistence layer(a relational dababase).
  ```
    Application/Business Layout <--> DAO <--> Persistence Layout (Relational Database)
  ```
-  DAO is responsible for interfacing with the database. (like a helper for communicating with the database). We define the functions of CRUD in DAO.
- if we use JPA API, we need JPA Entity Manager to implemet DAO.
- Spring Data JPA Interface (CrudRepository or JpaRepository) has defined the CRUD operations for the user.

## Composite

## Proxy

## Facade
