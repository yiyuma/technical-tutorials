## Spring Boot
**Spring Boot Application** must be annotated with @SpringBootApplication. <br>
The Spring-Boot Application bootstraps with SpringApplication.run(classname.class, args) to 
- create application context and registers all beans.
- start the embedded server Tomcat...
```
public static void main(String[] args){
  SpringBootApplication.run(classname.class, args);
}
```

## REST
**REST (REpresentational State Transfer)** is lightweight approach for communicating between applications.
- REST calls can be made over HTTP.
- REST is language independent.
- REST applications can use any data format. (Commonly see XML and JSON)

**REST over HTTP** <br>
Leverage HTTP Method for CRUD Operation
- POST: **C**reate a new entity
- GET: **R**ead a list of entities or single entity
- PUT: **U**pdate an existing entity
- DELETE: **D**elete an existing entity

**HTTP Request Message** has 3 areas
- Request line: has the actual HTTP command or method (Post, Get, Put, Delete)
- Header variables: has the request metadata (additional information about the request)
- Message body: has the contents of the message or the actual payload

**HTTP Response Message** has 3 areas
- Response line: has server protocol and HTTP status code
- Header variables: has the response metadata
- Message body: has the contents of the message

**HTTP Status Code** <br>
- 1xx informational response
- 2xx successful: 200 (OK), 202(Accepted)
- 3xx redirection
- 4xx client errors: 401(Authentication Required) 403 (Forbidden), 404(File Not Found), 405(Method not Allowed)
- 5xx server errors: 500 (Internal Server Error), 501(Not Implemented), 502 (Bad Gateway)

**MIME Content Types (Multipurpose Internet Mail-Extension)** is a message format for the actual payload. It simply describes the acutal content or the format of the message being returned. Basic Syntax is type/sub-type. Example: text/html, text/plain (information that is returned to the client), application/json, application/xml(for RESTful client)

**JSON (JavaScript Object Notation)** is plain text data. It is lightweight data format for storing and exchanging data.
- Language independent.
- Can use with any programming language.
- Format:
    - Curley braces define object
    - Object members are name/value pairs, delimited by colons
    - Name is always in double-quotes
    - Values:
        - Numbers: no quotes
        - String: in double quotes
        - Boolean: true, false
        - Nested JSON object with curley braces
        - Array with square brackets[] (["Java", "JavaScript","C#", "Python"])
        - null

**Java JSON Data Binding with Jackson (Converting JSON data to a Java POJO)** <br>
***Jackson*** handles data binding between JSON and Java POJO with getter and setter method. JSON to Java POJO with setter methods on POJO. Java POJO to JSON with getter methods on POJO. Spring Boot will automatically handle Jackson integration (Spring Boot Stater Web). JSON data being passed to REST controller is converted to Java POJO. Java POJO being returned from REST controller is converted to JSON.

**Postman** is a client tool. It can send HTTP requests to the REST Web Service / API, and then it will get the response, and we can actually view it there in the tool.

## Spring Exception Handler
**Spring Exception Handler** <br>
- step 1: create custom response class: It is a Java POJO class. It will be sent back to client as JSON.
- step 2: create custom exception class: This class will be extended from RuntimeException
- step 3: Add throw exception in REST service
- step 4: Add an exception handler method using ***@ExceptionHandler*** annotation.

**Global Exception Handler**
- **@ControllerAdvise** (class level annotation): is similar to an interceptor or filter for Controller. It can be used in pre-process requests to controllers or post-process responses to handle exceptions. It is realtime use of AOP.
- **@ExceptionHandler** (method level annotation): is a class level annotation and will return a ResponseEntity.
  ```
  @ControllerAdvice
  public class CustomRestExceptionHandler{
    @ExceptionHandler
    public ResponseEntity<CustomErrorResponse> handleException(CustomException exc)
    {
      CustomErrorResponse error = new CustomErrorResponse();
      error.setStatus(HttpStatus.NOT_FOUND.value());
      error.setMessage(exc.getMessage());
      error.setTimeStamp(System.currentTimeMillis());
    
      return new ResponseEntity<>(error, HttpStatus.NOT_FOUND);
    }
  }
  
  CustomErrorResponse: Type of the response body
  CustomException: Exception type to handle/catch
  ```
  
## Annotations
**@SpringBootApplication** is used to mark the main class of a Spring Boot application.<br>
@SpringBootApplication = @Configuration + @EnableAutoConfiguration + @ComponentScan<br>
- @Configuration
- @EnableAutoConfiguration: Spring Boot looks for auto-configuration beans on its classpath and automatically applies them. @EnableAutoConfiguraion should be used always with @Configurion together.
Able to register extra beans with @Bean or import other configuration classes
- @ComponentScan: Enables component scanning of current package. Also recursively scans sub-package. Man can define scan path with scanBasePackage or scanBasePackages
```
@SpringBootApplication(scanBasePackage="scanPackage")
or
@SpringBootApplication(scanBasePackages={"scanPackage1",
                                         "scanPackage2"})
```
**@Component**: Configuration, Controller, Service and Repository are meta-annotated with Component. Congiguraion, Controller, Service, Repoistory are Component, but the inverse is not true.<br>
**@Configuration** is meta-annotation. It is used for defining beans with @Bean (method level) and their dependencies.<br>
**@Controller** is meta-annotation. It applied to Controller implementations. In the @ControllerAdvice will implemented the Exceptions for the Controller.<br>
**@Service** is meta-annotation. It applied to Service implementations. Spring will automatically register the Service implementation.<br>
- Service layer: Service Facade design pattern. It is intermediate layer for custom business logic. Integrate data from multiple sources(DAO/repositories).
- Service layer has the responsibility to manage transaction boundaries. Apply @Transactional annotation on service methods.
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



### application.properties
***Database configuration***
```
spring.datasource.url=jdbc:mysql://localhost:3306/databaseUrl
spring.datasource.username=user
spring.datasource.password=password
```
***Turn off the spring boot banner***
```
spring.main.banner-mode=off
```
***Logging level***
```
logging.level.root=warn
- warn is only for warning and error
```
### Design pattern
***Service Facade*** is used in the service layer.<br>
***Proxy*** is used in the AOP.<br>


