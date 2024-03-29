## Spring 

### Spring projects
- **Spring Boot**: Spring Boot is used to create web applications. It uses Spring behind the scense, but it makes easier to get started with Spring development. It provides an embedded HTTP server (Tomcat).
- **Spring Data**: Spring Data is used to access different relational and NoSQL databases.
- **Spring MVC**: Spring MVC is used to create web applications.
- **Spring Security**: Spring Security is uesed to secure the java applications and web pages.

### Create Spring project
We can create Spring project with the help from the web page "Spring Initializr"(https://start.spring.io/). In this page we can add dependcies for the project.
- spring-boot-starter-web: building web apps, includes validation, REST. Uses Tomcat as default embedded server
- spring-boot-starter-security: Adding Spring Security support
- spring-boot-starter-data-jpa: Spring database support with JPA and Hibernate
- spring-boot-starter-thymeleaf
- spring-boot-starter-parent: special starter that provides Maven defaults. In it define the default Maven configuration.
- spting-boot-start-actuator: monitor and manager the application.

### Spring Container
**Primary functions**
- create and manage objects (Inversion of Control)
- Inject object dependencies (Dependency Inject)
**Inversion of Control**
Spring will scan for @Component, @Controller, @RestController, @Service, @Repository, @Configuration, @Bean. They are meta annotations and mark the class as a Spring Bean. They make the bean available for the dependency injection.

**Dependency Injection** <br>
The dependency inversion principle: The client delegates to another object the responsibility of providing its dependencies. @Autowired (matches by type, class or interface), @Primary, @Inject

**Configuring Spring Container**
- XML configuration file (legacy)
- Java Annotations
- Java Source Code

**Injection Types**
- Constructor Injection
  - Use this when you have required dependencies
  - This is as first choice
- Setter Injection
  - Use this when you have optional dependencies
  - if dependency is not provided, your app can provide reasonable default logic.
- Field Injection
  - does not recommended, because it maked the code harder to unit test

### Lazy initialization
With lazy initialization will a bean only be initialized when it is needed for dependency injection, or it is wxplicitly required.
- Mark annotation @Lazy on the class.
- Or define a global configuration in the application.properties 
  ```
  // by default is the value as false
  spring.main.lazy-initialization=true
  ```

### Bean scope
Bean scope defines the lifecycle of a bean. 
- How long does the bean live?
- How many instances are created?
- How is the bean shared?

Default scope is singleton. We cann use @Scope (class level) to define the bean scope.
```
@Component
@Scope(ConfigurableBeanFactory.SCOPE_SINGLETON)
public class className{ ... }
or
@Scope("singleton")
```
- **SCOPE_SINGLETON** or **singleton**: Create a single shared instance of the bean. It is cached in memory. All dependency injections will reference the same bean. Default scope.
- **SCOPE_PROTOTYPE** or **prototype**: Creates a new bean instance for each container request. Protrtype beans are lazy by default. It is no need to use @Lazy. For prototype beans Spring does not call the destroy method.
- **SCOPE_REQUEST** or **request**: Scoped to an HTTP web request. Only used for web apps.
- **SCOPE_SESSION** or **session**: Scoped to an HTTP web session. Only used for web apps.

### Bean lifecycle
**Container Started** -> **Bean Instantiated** -> **Dependencies Injected** -> **Internal Spring Processing** -> **Your Custom Init Method** -> **Your Custom Destroy Method** -> **Stop**
- You can add custom code during bean initialization with **@PostConstuct**
  - calling custom business logic methods
  - setting up handles to resources(db, sockets, files etc)
- You can add custom code during bean destruction with **@PreDestory**
  - calling custom business logic methods
  - clean up handles to resources (db, sockets, files etc)

### JSON Data Binding with Jackson
Spring uses Jackson Project to handle data binding between JSON and Java POJO.
- Jackson calls setter methods to convert JSON to Java POJO
- Jackson calls getter methods to convert Java POJO to JSON




