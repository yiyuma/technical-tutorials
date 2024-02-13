## Spring Boot

### Run a spring boot project in cmd
```
java -jar filename.jar
or
mvn spring-boot:run
```

### Spring Boot Application
***Spring Boot Application*** must be annotated with @SpringBootApplication. <br>
The Spring-Boot Application bootstraps with SpringApplication.run(classname.class, args) to 
- create application context and registers all beans.
- start the embedded server Tomcat...
```
public static void main(String[] args){
  SpringBootApplication.run(classname.class, args);
}
```
## Spring Exception Handler
**Spring Exception Handler** <br>
- step 1: create custom response class: It is a Java POJO class. It will be sent back to client as JSON.
  ```
  public class UserErrorResponse{
  	private int status;
  	private String message;
  	private long timeStamp;
  	// Constructors
  	// Getters / Setters
  }
  ```
- step 2: create custom exception class: This class will be extended from RuntimeException
  ```
  public class UserNotFoundException extends RuntimeException{
  	public UserNotFoundException(String message){super(message);}
  }
  ```
- step 3: Add throw exception in REST service
- step 4: Add an exception handler method using ***@ExceptionHandler*** annotation.

**Global Exception Handler**
- **@ControllerAdvise** (class level annotation): is similar to an interceptor or filter for Controller. It can be used in pre-process requests to controllers or post-process responses to handle exceptions. It is realtime use of AOP.
- **@ExceptionHandler** (method level annotation): is a class level annotation and will return a ResponseEntity.
  ```
  @ControllerAdvice
  public class UserRestExceptionHandler{
    @ExceptionHandler
    public ResponseEntity<UserErrorResponse> UserNotFoundhandleException(UserNotFoundException exc)
    {
      UserErrorResponse error = new UserErrorResponse();
      error.setStatus(HttpStatus.NOT_FOUND.value());
      error.setMessage(exc.getMessage());
      error.setTimeStamp(System.currentTimeMillis());
    
      return new ResponseEntity<>(error, HttpStatus.NOT_FOUND);
    }
  }

  ResponseEntity: a wrapper for the HTTP response object (HTTP status code (=HttpStatus.NOT_FOUND), HTTP headers and Reponse body (= error)).
  UserErrorResponse: Type of the response body
  UserNotFoundException: Exception type to handle/catch
  ```

  
## Spring Boot Unit Testing
Using **@SpringBootTest**
- Loads the application context
- Support for Spring dependency injection
- Can access data from Spring application.peoperties

Step1 : Add **spring-boot-starter-test** dependency in pom.xml file. spring-boot-starter-test includes a transitive dependency on JUnit 5.
```
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-test</artifactId>
    <scope>test</scope>
</dependency>
```
Step2: Add Annotation @SpringBootTest on the test method
```
@SpringBootTest (classes=Application.class) // load Spring Application Context.
public class ApplicationTest{
	// Injection
	@Autowired
	User user;
	// Access Spring Application Context
	@Autowired
	ApplicationContext context
	// Access data from application.properties (info.app.name=ToDoListApplication)
	@Value("${info.app.name}")
	private String appInfo
	@Test
	void basicTest(){}
}
```

## Annotations


**@Repository**is meta-annotation. It applied the Repository implementations.<br>
**@RestController** = @Controller + @ResponseBody (The return value of the methods will be saved in a ResponseBody.). It is for REST. It is class level annotation. <br>

@RequestMapping("/api") is class level annotation.<br>
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
**ResponseEntity** is a wrapper for the HTTP response object. It provides fine-grainted control to specify HTTP status code, HTTP headers and Response body.

@GetMapping(path= "/api/user/{id}", produces = MediaType.APPLICATION_JSON_VALUE)
@PostMapping(path= "/api/auth/login",consumes = MediaType.APPLICATION_JSON_VALUE, produces = MediaType.APPLICATION_JSON_VALUE)
@PutMapping itempotent
@DeleteMapping

@PathVariable String id
@RequestParam(name="user-name", defaultValue="") String userName


Define custom application properties:
application properties is saved unter 
@Value("PropertyName in the application properties")

## spring-boot-devtools
spring-boot-devtools: automatically restarts the application when code is updated. <br>
Add spring-boot-devtools:
- add dependency of spring-boot-devtool
  ```
  <dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-devtools</artifactId>
  </dependency>
  ```
- Preferences->Build,Execution,Deployment->Compiler: select "check Build project automatically"
- Preferences->Advanced Settings: select "Allow auto-make to..."

## spring-boot-starter-actuator
Expose endpoints to monitor and manager your application.<br>
Add spring-boot-starter-actuator in pom.xml
```
  <dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-actuator</artifactId>
  </dependency>
```
/actuator is the prefix.
- /health: check the status your application. It is exposed by default
- /info: provide information about your application. The infos must be defined in the application.properties file.
  ```
  in application.properties
  info.app.name=test project
  info.app.description=This is a test project
  info.app.verion=1.0.0
  ```
- /auditevents: audit events for your application
- /beans: list of all beans registered in the Spring application context
- /mapping: List of all @RequestMapping paths

Only the /health is exposed by default. To expose all actuator endpoints over HTTP you have to define in the application.properties.
```
management.endpoints.web.exposure.include=*
or for the /info
management.endpoints.web.exposure.include=health,info
management.info.env.enabled=true
```

## Design pattern
***Service Facade*** is used in the service layer.<br>
***Proxy*** is used in the AOP.<br>


