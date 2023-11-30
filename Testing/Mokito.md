## Mocking
- Allows us to test a given class in isolation
- Test interaction between given class and its dependencies
- Minimizes configuration /availability of dependencies
- We can mock the DAO, DB or REST API to give a response
- Mocking Frameworks: Mockito, EasyMock...


## Mockito
Spring Boot has built-in support for Mockito.<br>

Structure:
- Set Up: Set expectations with mock responses
- Execute: Call the method you want to test
- Assert: Check the result and verify that it is the expected result
- Verify: Optionally... verify calls (how many times called etc...)
