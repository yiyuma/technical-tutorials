## Spring Annotations

### Spring Core Annotations
- **@SpringBootApplication** is used to mark the main class of a Spring Boot application.<br>
@SpringBootApplication = @EnableAutoConfiguration + @Configuration + @ComponentScan<br>
- **@EnableAutoConfiguration**: Spring Boot looks for auto-configuration beans on its classpath and 	automatically applies them. @EnableAutoConfiguraion should be used always with @Configuration together.
- **@Configuration**: able to register extra beans with @Bean or import other configuration classes.
- **@ComponentScan**: @ComponentScan without arguments tells Spring to scan components in the current package and its sub-packages. Man can also define the scan path with **scanBasePackage** or **scanBasePackages**
  ```
  @SpringBootApplication(scanBasePackages="scanPackage")
  or
  @SpringBootApplication(scanBasePackages={"scanPackage1",
                                     "scanPackage2"})
  or
  @ComponentScan(basePackages="scanPackage1")
  @ComponentScan(basePackages="scanPackage2")
  ```
  ```
  // ComponentScan with Exclusions
  @ComponentScan(excludeFilters = @ComponentScan.Filter(type=FilterType.Regex, pattern="..."))
  or
  @ComponentScan(excludeFilters = @ComponentScan.Filter(type=FilterType.ASSIGNABLE_TYPE,       value=className.class))
  ```
- **@EnableAutoConfiguration** vs. **@ComponentScan**:
  - @ComponentScan scans for Spring components.
  - @EnableAutoConfiguration enables Spring Boot to auto-configure the application context. It automatically creates and registers beans based on both the included jar files in the classpath and the beans (Components, controllers, services, repositories) defined by application.
- **@Component** is an annotation that allows Spring to detect our cunstom beans automatically. @Controller, @Service, @Repoistory and @Configuration are @Component, but the inverse is not true. @Configuraion, @Controller, @Service and @Repository are stereotype annotations. 
- **@Controller** is meta-annotation. It applied to Controller implementations.
- **@ControllerAdvice** will implemented the Exceptions for the Controller.
- **@RestController** = @Controller + @ResponseBody (The return value of the methods will be saved in a ResponseBody.). It is for REST. It is class level annotation.
- **@Service** is meta-annotation. It applied to Service implementations. Spring will automatically register the Service implementation.
  - Service layer: uses Service Facade design pattern. It is intermediate layer for custom business logic. Integrate data from multiple sources(DAO/repositories).
  - Service layer inject DAO and has the responsibility to manage transaction boundaries. Apply @Transactional annotation on service methods.
- **@Repository**: specifies a repository. It supports component scanning. It translated JDBC exceptions.
- **@Configuration** is meta-annotation. It is used for defining beans with @Bean (method level) and their dependencies.
- **@Bean** is an annotation that Spring uses to gather beans at runtime. It is a method level annotation. The methods with @Bean must be in @Configuraion classes. We can use @Bean for the outside class.
- **@Autowired** is an annotation to mark a dependency which Spring is going to resolve and inject. We can use it with constructor, setter or field injection. If you only have one constructor then @Autowired on constructor is optional.
- **@Qualifier** In @Qualifier we can give the bean id. Bean id is same name as class, only first character is lower-case (The bean id of the class PersonInfo is personInfo).
- **@Primary** is a class level annotation. @Primary can have only one for multiple implementations. If you mix @Primary and @Qualifier, then @Qualifier has higher priority.
- **@Inject**:
- **@Lazy**: Lazy initialisieren. The bean will be initialized, if it is needed for dependency injection or it is explicitly required. Man can set lazy initialization in the application.properties file for a global lazy initialization.
  ```
  // set global lazy initialization
  spring.main.lazy-initialization=true  
  ```
- **@Scope** define the bean scope.(singleton, prototype...)
- **@PostConstuct**: use it to add custom code during bean initialization (custom business logic methods, setting up handles to resources)
- **@PreDestroy**: use it to add custom code during bean destruction (custom business logic methods, clean up handles to resources
- **@ControllerAdvice**: In @ControllerAdvice defines Exception Handler. It is similar to a filter. Pre-process requests to controllers. Post-process responses to handle exception.
- **@ExceptionHandler**: define a REST Exception Handler
- **@Autowired vs. @Inject**
@Autowired: matches by type: class or interface

### Hibernate annotations
- **@Entity**: declare any POJO class as an entity for a database. (Class level annotation)
- **@Table**: Use to change table details. (Class level annotation)
  - name: If not specified, table name in db is the same name as class name.
  - schema:
  - catalogue
  - enforce unique constraints
- **@Id**: declare a primary key inside the POJO class. (Method level annotation). Data type can be Java primitive and primitive wrapper types, String, Date, BigDecimal and BigInteger.
- **@GeneratedValue**: Automatically generate the primary key value. if we donot specify the strategy, the generation type defaults to AUTO. The id value will be generated by the database and managed by the database.
  - strategy
    - GenerationType.AUTO: the persistence provider will detemine values based on the type of the primary key attribute. The type can be numerical or UUID. For numeric values, the generation is based on a sequence or table generator. For UUID, it will use the UUIDGenerator.
    - GenerationType.IDENTITY: assign primary keys using identity column in the database. The ids are auto-incremented.
    - GenerationType.SEQUENCE: assign primary keys using sequence if the database supports them. It switches to table generation if they arenot supported. In order to customize the sequence name, we can use the @GenericGenerator annotation with SequenceStyleGenerator.
      ```
      @Entity
      public class User{
        @Id
        @GeneratedValue(strategy=GenerationType.SEQUENCE,
                        generator="sequence-generator")
        @GenericGenerator(name="sequence-generator",
                          strategy="org.hibernate.id.enhanced.SequenceStyleGenerator",
                          parameters={@Parameter(name="sequence_name", value="user_generator"),
                                      @Parameter(name="initial_value", value="4"),
                                      @Parameter(name="increment_size", value="1")})
        private long userId;
      }
      ```
    - GenerationType.TABLE: assign primary keys using an underlying database table to ensure uniqueness
      ```
      @Entity
      public class Department{
        @Id
        @GeneratedValue(strategy=GenerationType.TABLE,
                        generator="table-generator")
        @TableGenerator(name="table-generator",
                        table="dep_ids",
                        pKColumnName="seq_id",
                        valueColumnName="seq_value")
        private long depId;
      }
      ```
    - Customer Generator: we can define our custom generator by implementing the IdentifierGenerator interface.
- **@Column**: @Column is optional. mapping column in database.
  - name: specifies the name of the column in the table. If not specified, column name is the same name as java field.
  - length: specifies its length
  - unique: specifies whether the column is unique
  - nullable: specifies whether the column is nullable or not
- **@Transient**: Do not pesist the field in the database
- **@Transactional**: automatically begin and end a transaction for the JPA code.
- **@OneToOne**: annotation for the one to one mapping. Method level annotation.
  - cascade: cascade type (CascadeType.PERSIST, CascadeType.REMOVE, CascadeType.REFRESH, CascadeType.DETACH, CascadeType.MERGE, CascadeType.ALL). It can be used by Uni-Directional and Bi-Directional.
  - fetch: fetchType (fetchType.LAZY, fetchType.EAGER)
  - mappedBy: used in Bi-Directional. It is the field name in the related class.
- **@JoinColumn**: to define foreign key.
  - name: foreign key column name
- **@OneToMany**: annotation for one to many mapping.
- **@ManyToOne**: annotation for many to one mapping.
  - mappedBy:  It is the property name in the related class.
  - fetch: fetch type
- **@ManyToMany**: annotation for many to many mapping.
- **@JoinTable**: annotation for a table that provides a mapping between two tables.
  - name: Join table name (name="COURSE_STUDENT")
  - joinColumns: join column (joinColumns=@JoinColumn(name="COURSE_ID")): COURSE_ID is foreign key of the course in the table COURSE_STUDENT.
  - inverseJoinColumns: inverse join column (inverseJoinColumns=@JoinColumn(name="STUDENT_ID")): STUDENT_ID is foreign key of student in the table COURSE_STUDENT.
- **@Temporal**:
- **@Enumarated**: specifies whether the enum should be persisted by name (EnumType.STRING) or by ordinal(default).

### Spring web annotations
- **@RequestMapping("/api")** is used to map web request to Spring Controller methods<br>
- **@PathVariable**: Bind path variable
  ```
  // studentId is here the path variable
  @GetMapping("/student/{studentId}")
  public Student getStudent(@PathVariable int studentId){...}
  ```
**ResponseEntity** is a wrapper for the HTTP response object. It provides fine-grainted control to specify HTTP status code, HTTP headers and Response body.
```
@ExceptionHandler
public ResponseEntity<StudentErrorResponse> handleException(StudentNotFoundException exc){
  StudentErrorResponse error = new StudentErrorResponse();
  error.setStatus(HttpStatus.NOT_FOUND.value());
  error.setMessage(exc.getMessage());
  error.setTimeStamp(System.currentTimeMillis());
  return new ResponseEntity<>(error, HttpStatus.NOT_FOUND);
}
```




@GetMapping("/students/{id}") is method level annotation. {id} here is path variable.
```
@GetMapping("/students/{id})
public Student getStudent(@PathVariable int {id}){
    return students.get(id); 
}
```
```
@PostMapping("/students")
public Student addStudent(@RequestBody Student theStudent){
    theStudent.setId(0);
    Student dbStudent = studentService.save(theStudent);
}
```


@GetMapping(path= "/api/user/{id}", produces = MediaType.APPLICATION_JSON_VALUE)
@PostMapping(path= "/api/auth/login",consumes = MediaType.APPLICATION_JSON_VALUE, produces = MediaType.APPLICATION_JSON_VALUE)
@PutMapping itempotent
@DeleteMapping


@RequestParam(name="user-name", defaultValue="") String userName
- Service layer: Service Facade design pattern. It is intermediate layer for custom business logic. Integrate data from multiple sources(DAO/repositories).
- Service layer has the responsibility to manage transaction boundaries. Apply @Transactional annotation on service methods.

Define custom application properties:
application properties is saved unter 
@Value("PropertyName in the application properties")
