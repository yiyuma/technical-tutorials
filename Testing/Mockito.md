## Mockito
Mockito is mocking framework for Java in software test. It is an open source framework.<br>
Link: https://site.mockito.org/ <br>
Using Mockito simplifies the development of tests for classes with extenal dependencies. <br>
Spring boot has built-in support for Mockito. In maven if you add spring-boot-starter-test, it has reference of mockito.

a mock object is a dummy implementation for an interface or a class. It allows to define the output of certain method calls. They typically record the interaction with the system and tests can validate that.


### Structure:
- Set Up: Set expectations with mock responses. (Grammar: when(doSomeWork()).thenThrow(aErrorMessage).thenReturn(aResponse);
- Execute: Call the method you want to test
- Assert: Check the result and verify that it is the expected result
- Verify: Optionally... verify calls (how many times called etc...) (Grammar: verify())

### Annotations from Mockito:
- @Mock
- @Spy
- @InjectMocks: will only inject dependencies annotated with @Mock or @Spy

Annotations from Spring Boot
- @MockBean: @MockBean = functionality of @Mock + add mock bean to Spring ApplicationContext + making the mock bean avariable for inject with @Autowired, @Autowired instead of @InjectMocks
