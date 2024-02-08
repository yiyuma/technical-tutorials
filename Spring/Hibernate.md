## ORM, JPA, Hibernate
**Object-to-Relational Mapping (ORM)** means the Mapping between object and database table.

**Jakarta Pesistence API (JPA)** is a Standard JAVA API for Object-to-Relational Mapping. It is only a specification
- defines a set of interface
- requires an inplementation to be useable.

**Hibernate** is a framework for persisting / saving Java objects in a database. Hibernate provides the Object-to-Relational Mapping (ORM). It is an implementation of JPA.

**Java DataBase Connectivity (JDBC)** is an API for conncecting and executing queries on a database for Java. JDBC can work with any database as long as proper drivers are provided. 

**Relationship between Hibernate/JPA and JDBC** <br>
Hibernate/JPA uses JDBC for all database communications. Hibernate/JPA <=> JDBC <=> Datebase. <br>
Add JDBC connection info in the application.properties
```
// Spring use JDBC for mySQL database communication
spring.datasource.url=jdbc:mysql://localhost:3306/student_tracker
spring.datasource.username=user
spring.datasource.password=password
```

## Hibernate

### Data Access Object (DAO)
DAO is a common design pattern. DAO is responsible for interfacing with the database. (like a helper for communicating with the database) DAO needs a JPA Entity Manager.<br>

### Entity Manager
EntityManager is the main component for saving and retrieving entities. It is from Jakarta Persistence API (JPA). Its bean will be created automatically from Spring Boot.<br>
- entityManager.persist(obj): create obj
- entityManager.find(obj, primary key): read obj
- entityManager.merge(obj): update obj
- entityManager.remove(obj): delete obj 

### Data Source
Data source defines database connection info. Data Source is automatically created by Spring Boot based on the file application properties (JDBC URL, user id, password, etc...)

### Relationship DAO, Entity Manager, Data Source and database
DAO <--> Entity Manager <--> Data Source <--> database

### Hibernate Mapping
- **One-to-One mapping**
  - ***Uni-Directional***: An Instructor has an instructor detail.
    ```
    @Entity
    @Table(name="INSTRUCTOR")
    @Data
    @NoArgsConstructor
    public class Instructor{
      // Instructor has an InstructorDetail: One to One Mapping
      // INSTRUCTOR_DETAIL_ID is the foreign key in the Table INSTRUCTOR
      @OneToOne(cascade=CascadeType.ALL)
      @JoinColumn(name="INSTRUCTOR_DETAIL_ID)
      private InstructorDetail instructorDetail;
    }
    
    @Entity
    @Table(name="INSTRUCTOR_DETAIL")
    @Data
    @NoArgsConstructor
    public class InstructorDetail{
      @Id
      @GeneratedValue
      @Column(name="ID")
      private UUID id;
    }
    ```
  - ***Bi-Directional***: An Instructor has an instructor detail.
    ```
    @Entity
    @Table(name="INSTRUCTOR")
    @Data
    @NoArgsConstructor
    public class Instructor{
      // INSTRUCTOR_DETAIL_ID is the foreign key in the Table INSTRUCTOR
      @OneToOne(cascade=CascadeType.ALL)
      @JoinColumn(name="INSTRUCTOR_DETAIL_ID)
      private InstructorDetail instructorDetail;
    }
    
    @Entity
    @Table(name="INSTRUCTOR_DETAIL")
    @Data
    @NoArgsConstructor
    public class InstructorDetail{
      @Id
      @GeneratedValue
      @Column(name="ID")
      private UUID id;

      // for Bi-Directional
      // instructorDetail is the field name in the class Instructor
      @OneToOne(mappedBy="instructorDetail", cascade=CascadeType.ALL)
      private Instructor instructor;
    }
    ```
- **One-to-Many mapping**
  - ***Uni-Directional***: A course has many reviews
    ```
    @Entity
    @Table(name="COURSE")
    @Data
    @NoArgsConstructor
    public class Course{
      @Id
      @GeneratedValue
      @Column(name="ID")
      private UUID id;

      // COURSE_ID is the foreign key in the Table REVIEW
      @OneToMany(cascade=CascadeType.ALL, fetch=FetchType.Lazy)
      @JoinColumn(name="COURSE_ID")
      private List<Review> reviews;
    }

    @Entity
    @Table(name="REIVEW")
    @Data
    @NoArgsConstructor
    public class Review{
      @Id
      @GeneratedValue
      @Column(name="ID")
      private UUID id;
    }
    ```
  - ***Bi-Directional***: An instructor has many courses.
    ```
    @Entity
    @Table(name="INSTRUCTOR")
    @Data
    @NoArgsConstructor
    public class Instructor{
      // Instructor has an InstructorDetail: One to One Mapping
      // INSTRUCTOR_DETAIL_ID is the foreign key in the Table INSTRUCTOR
      @OneToOne(cascade=CascadeType.ALL)
      @JoinColumn(name="INSTRUCTOR_DETAIL_ID)
      private InstructorDetail instructorDetail;
  
      // An Instructor has many cources: One to Many Mapping
      // instructor is the field name in the class Course
      @OneToMany(mappedBy="instructor",
                cascade={CascadeType.PERSIST, CascadeType.MERGE, CascadeType.DETACH, CascadeType.REMOVE})
      Set<Course> courses;

      // Add convenience methods for bi-directional relationship
      public void add(Course course){
          if(courses==null){
              courses = new Set<>();
          }
          courses.add(course);
          course.setInstructor(this);
      }

      // Remove convenience methods for bi-directional relationship
      public void delete(Course course){
      }
    }
    
    ```
- **Many-to-One mapping**
  - ***Bi-Directional***: An instructor has many courses.
  ```
    @Entity
    @Table(name="COURSE")
    @Data
    @NoArgsConstructor
    public class Course{
      @Id
      @GeneratedValue
      @Column(name="ID")
      private UUID id;

      // INSTRUCTOR_ID is the foreign key in the Table COURSE
      @ManyToOne(cascade={CascadeType.PERSIST, CascadeType.MERGE, CascadeType.DETACH, CascadeType.REMOVE})
      @JoinColumn(name="INSTRUCTOR_ID")
      private Instructor instructor;

      // COURSE_ID is the foreign key in the Table REVIEW
      @OneToMany(cascade=CascadeType.ALL, fetch=FetchType.Lazy)
      @JoinColumn(name="COURSE_ID")
      private List<Review> reviews;
    }
  ```
- **Many-to-Many mapping**: A student visits many courses. A course has many students.
  ```
    @Entity
    @Table(name="COURSE")
    @Data
    @NoArgsConstructor
    public class Course{
      @Id
      @GeneratedValue
      @Column(name="ID")
      private UUID id;

      // INSTRUCTOR_ID is the foreign key in the Table COURSE
      @ManyToOne(cascade={CascadeType.PERSIST, CascadeType.REFRESH, CascadeType.MERGE, CascadeType.DETACH})
      @JoinColumn(name="INSTRUCTOR_ID")
      private Instructor instructor;

      // COURSE_ID is the foreign key in the Table REVIEW
      @OneToMany(cascade=CascadeType.ALL, fetch=FetchType.Lazy)
      @JoinColumn(name="COURSE_ID")
      private List<Review> reviews;

      // A course has many students
      @ManyToMany(cascade={CascadeType.PERSIST, CascadeType.REFRESH, CascadeType.MERGE, CascadeType.DETACH}
      @JoinTable(name="COURSE_STUDENT", joinColumns=@JoinColumn(name="COURSE_ID"),
                 inverseJoinColumns=@JoinColum(name="STUDENT_ID"))
      private List<Student> students;
    }

    @Entity
    @Table(name="STUDENT")
    @Data
    @NoArgsConstructor
    public class Student{
      @Id
      @GeneratedValue
      @Column(name="ID")
      private UUID id;
  
      // A student has many courses
      @ManyToMany(cascade={CascadeType.PERSIST, CascadeType.REFRESH, CascadeType.MERGE, CascadeType.DETACH}
      @JoinTable(name="COURSE_STUDENT", joinColumns=@JoinColumn(name="STUDENT_ID"),
                 inverseJoinColumns=@JoinColum(name="COURSE_ID"))
      private List<Course> courses;
    }
  ```

### Java Persistence Query Language (JPQL) 
JPQL is based on **entity name** and **entity fields** in the **java class**. <br>
Statement: FROM, WHERE, =, OR, LIKE, order by, asc(ascending), desc(descending), UPDATE, SET, DELETE<br>
JPQL Named Parameters are prefixed with a colon ':'. JPQL Named Parameters is as a placeholder.<br>

### Create database tables from Java Code
Spring JPA Hibernate supports DDL auto.
DDL (Data Definition Language): related to database schema creating
in application.properties define
```
spring.jpa.hibernate.ddl-auto=create
```
- none: No action will be performed
- create-only: Database tables are only created
- drop: Database tables are dropped
- create: Database tables are dropped followed by database tables creation
- create-drop: Database tables are dropped followed by database tables creation. On application shutdown, drop the database tables. For unit testing
- validate: Validate the database tables schema
- update: Update the database tables schema

### Spring Data JPA
Spring Data JPA create a DAO and just plug in your **entity name** and **type of primary key**. Spring will give a CRUD implementation. Spring Data JPA provides the interface JpaRepository.<br>

### Spring Data REST
- Spring Data REST will scan your project for JpaRepository
- Expose REST APIs for each entity type for your JpaRepository
- Spring Data REST will create endpoints based on entity type. 
- Spring Data REST endpoints are HATEOAS compliant. (HATEOAS: Hypermedia as the Engine of Application State, think of it as meta-data for REST data)
- Set base path in the application.properties
```
spring.data.rest.base-path=/magic-api
```
- Specify plural name/ path with an annotation: @RepositoryRestResource(path="members")
- Pagination: default page size is 20. 
```
spring.data.rest.default-page-size=50
```
- Sort: default is ascending
```
http://localhost:8080/employees?sort=lastName,desc
```

## Terminology
### Entity class
Java class that is mapped to a database table.
- Must be annotated with @Entity
- Must have a public or protected no-argument constructor

### Primary Key
- Uniquely identifies each row in a table.
- Must be a unique value
- Cannot contain NULL values

### Foreign Key
- Link tables together
- a field in one table that refers to primary key in another table

### Join Table
A table that provides a mapping between two tables. It has foreign keys for each table to define the mapping relationship.

### Cascade
- apply the same operation to related entities

### FetchType
- Eager loading: will retrieve everything
- Lazy loading: will retrieve on request. Lazy loading requires an open Hibernate session. If the Hibernate session is cloed, Hibernate will throw an exception.
- Default Fetch Types:
  - @OneToOne: FetchType.EAGER
  - @OneToMany: FetchType.LAZY
  - @ManyToOne: FetchType.EAGER
  - @ManyToMany: FetchType.LAZY
- In One-To-Many Mapping, if you only need instructor without courses, you can directly use findInstructorById(), which is created by JpaRepository. If you need instructor with courses, but the fetch type is FetchType.Lazy. You can declare a function findInstructorByIdJoinFetch() in the interface, which extends Interface JpaRepository. Then you can override it in the implemetation class from the interface.
  ```
  public Instructor findInstructorByIdJoinFetch(UUID theId){
    TypedQuery<Instructor> query = entityManager.createQuery("select i from instructor i JOIN FETCH i.courses where i.id= :data", Instructor.class);
    query.setParameter("data", theId);
    Instructor instructor = query.getSingleResult();
    return instructor;
  }
  ```
  
### Directional
- Uni-Directional: One way directional
- Bi-Directional: Two ways directional

### Entity Lifecycle
- Detach: If entity is detached, it is not associated with a Hibernate session
- Merge: If instance is detached from session, then merge will reattach to session
- Persist: Transitions new instances to managed state. Next flush / commit will save in db.
- Remove: Transitions managed entity to be removed. Next flush / commit will delete from db.
- Refresh: Reload /synch object with data from db. Prevents state date.

### Cascade Type
- PERSIST: If entity is persisted / saved, related entity will also be persisited
- REMOVE: If entity is removed / deleted, related entity will also be deleted
- REFRESH: If entity is refreshed, related entity will also be refreshed
- DETACH: If entity is detached (not associated w/ session), then related entity will also be detached.
- MERGER: if entity is merged, then related entity will also be merged.
- ALL: all of above cascade types
