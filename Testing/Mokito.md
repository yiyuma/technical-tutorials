## Mockito
Spring Boot has built-in support for Mockito.<br>

Structure:
- Set Up: Set expectations with mock responses. (Grammar: when(doSomeWork()).thenThrow(aErrorMessage).thenReturn(aResponse);
- Execute: Call the method you want to test
- Assert: Check the result and verify that it is the expected result
- Verify: Optionally... verify calls (how many times called etc...) (Grammar: verify())

Annotations from Mockito:
- @Mock
- @Spy
- @InjectMocks: will only inject dependencies annotated with @Mock or @Spy

Annotations from Spring Boot
- @MockBean: @MockBean = functionality of @Mock + add mock bean to Spring ApplicationContext + making the mock bean avariable for inject with @Autowired, @Autowired instead of @InjectMocks

## ReflectionTestUtils
Spring provides a utility class: ReflectionTestUtils. It allows you to get/set non-public fields and invoke non-public methods.
```
ReflectionTestUtils.getField(targetObject, "fieldName");
ReflectionTestUtils.setField(targetObject, "fieldName", fieldValue);
ReflectionTestUtils.invokeMethod(targetObject, "methodName");
```
