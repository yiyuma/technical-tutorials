## Spring Boot Test
Spring boot supports developing unit tests and integration tests using JUnit and Mockito.<br>
spring-boo-starter-test includes JUnit 5 and Mockito.

### Spring Boot Test
- Loads the application context with the annotation @SpringBootTest at class level
- Support for Spring dependency injection with the annotation @Autowired at fields
- Can access data from Spring application.properties with the annotation @Value at fields

### Annotations
- @SpringBootTest: class level annotation
- @MockBean: @MockBean = functionality of @Mock (Mockito) + add mock bean to Spring ApplicationContext + making the mock bean avariable for inject with @Autowired,
- @Autowired instead of @InjectMocks (Mockito)
  
### ReflectionTestUtils
Spring provides a utility class: ReflectionTestUtils. It allows you to get/set non-public fields and invoke non-public methods.
```
User user = (User)context.getBean("User");

ReflectionTestUtils.getField(user, "id");
ReflectionTestUtils.setField(user, "id", int);
ReflectionTestUtils.invokeMethod(user, "getUserTelefon");
```
