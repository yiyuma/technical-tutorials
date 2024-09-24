## Mockito

### What is Mockito
Mockito is mocking framework for Java in software test. It is an open source framework.<br>
Link: https://site.mockito.org/ <br>

### When use Mockito
If you want to test a class with extenal dependencies, for example the class has dependencies with DAO or database. You can mock the DAO or database for this class using Mockito.

### Annotations from Mockito:
- @Mock: create and inject mocked instances
- @Spy: spy an existing instance
- @Captor: create an ArgumentCaptor
- @InjectMocks: inject mock fields into the tested object automatically. It will only inject dependencies annotated with @Mock or @Spy
- @DoNotMock: it is on class level or interface level. It means marked class or interface should not be mocked during testing. This annotation has an attribut "reason".
  
### Ways to enable the use of Mockito annotations
- Spring boot project can use Mockito directlly. Spring boot has built-in support for Mockito. In maven if you add spring-boot-starter-test, it has reference of mockito.
- In class level add
  ```
  @ExtendWith(MockitoExtension.class)
  ```
- In init() of an unit testing class use man
  ```
  MockitoAnnotations.openMocks(this);
  ```
- In test class use MockitoJUnit.rule()
  ```
  @Rule
  public MockitoRule initRule = MockitoJUnit.rule();
  ```

a mock object is a dummy implementation for an interface or a class. It allows to define the output of certain method calls. They typically record the interaction with the system and tests can validate that.


### Structure of an unit testing with Mockito:
- Set Up: Set expectations with mock responses. (Grammar: when(doSomeWork()).thenThrow(aErrorMessage).thenReturn(aResponse);
- Execute: Call the method you want to test
- Assert: Check the result and verify that it is the expected result
- Verify: Optionally... verify calls (how many times called etc...) (Grammar: verify())



Annotations from Spring Boot
- @MockBean: @MockBean = functionality of @Mock + add mock bean to Spring ApplicationContext + making the mock bean avariable for inject with @Autowired, @Autowired instead of @InjectMocks
