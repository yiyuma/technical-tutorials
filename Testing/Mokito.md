## Mockito
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
