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

**@Autowired vs. @Inject**
@Autowired: matches by type: class or interface


Dependency Injection: <br>
The dependency inversion principle: The client delegates to another object the responsibility of providing its dependencies.

### Annotations
@Component: makes the class as a Spring Bean and make it available for dependency injection.
@Autowired: tells Spring to inject a dependency. If you only have one constructor then @Autowired on constructor is optional.
