## Spring 

### Spring Boot
Spring Boot uses Spring behind the scense, but it makes easier to get started with Spring development. 
It provide an embedded HTTP server (Tomcat).

### Spring Container
**Primary functions**
- create and manage objects (Inversion of Control)
- Inject object dependencies (Dependency Inject)
**Inversion of Control**
Spring will scan for @Component, @Controller, @RestController, @Service, @Repository, @Configuration, @Bean. They are meta annotations and mark the class as a Spring Bean. They make the bean available for the dependency injection.
**Dependency Injection** <br>
The dependency inversion principle: The client delegates to another object the responsibility of providing its dependencies.

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
With lazy initialization will a bean only be initialized when it is needed for dependency injection.
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
- SCOPE_SINGLETON: Create a single shared instance of the bean. It is cached in memory. All dependency injections will reference the same bean. Default scope.
- SCOPE_PROTOTYPE: Creates a new bean instance for each container request. Protrtype beans are lazy by default. It is no need to use @Lazy. For prototype beans Spring does not call the destroy method.
- SCOPE_REQUEST: Scoped to an HTTP web request. Only used for web apps.
- SCOPE_SESSION: Scoped to an HTTP web session. Only used for web apps.

### Bean lifecycle
Container Started -> Bean Instantiated -> Dependencies Injected -> Internal Spring Processing -> Your Custom Init Method -> Your Custom Destroy Method -> Stop
- You can add custom code during bean initialization with @PostConstuct
- You can add custom code during bean destruction with @PreDestory

**@Autowired vs. @Inject**
@Autowired: matches by type: class or interface




