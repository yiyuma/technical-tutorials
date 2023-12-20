## Spring Annotations

### Spring Core Annotations
- **@SpringBootApplication** is used to mark the main class of a Spring Boot application.<br>
@SpringBootApplication = @EnableAutoConfiguration + @Configuration + @ComponentScan<br>
- **@EnableAutoConfiguration**: Spring Boot looks for auto-configuration beans on its classpath and 	automatically applies them. @EnableAutoConfiguraion should be used always with @Configuration together.
- **@Configuration**: able to register extra beans with @Bean or import other configuration classes.
- **@ComponentScan**: @ComponentScan without arguments tells Spring to scan components in the current package and its sub-packages. Man can also define the scan path with **scanBasePackage** or **scanBasePackages**
```
@SpringBootApplication(scanBasePackage="scanPackage")
or
@SpringBootApplication(scanBasePackages={"scanPackage1",
                                         "scanPackage2"})
or
@ComponentScan(scanBasePackage="scanPackage1")
@ComponentScan(scanBasePackage="scanPackage2")
```
```
// ComponentScan with Exclusions
@ComponentScan(excludeFilters = @ComponentScan.Filter(type=FilterType.Regex, pattern="..."))
or
@ComponentScan(excludeFilters = @ComponentScan.Filter(type=FilterType.ASSIGNABLE_TYPE, value=className.class))
```
**@Component**: Configuration, Controller, Service and Repository are meta-annotated. Congiguraion, Controller, Service, Repoistory are Component, but the inverse is not true.<br>
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
