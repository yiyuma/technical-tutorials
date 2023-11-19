### JUnit5
User Guide: https://junit.org/junit5/docs/current/user-guide/

**JUnit 5** = JUnit Platform + JUnit Jupiter + JUnit Vintage
 - Supports creating test cases
 - Automation of the test cases with pass / fail
 - Utilities for testsetup, teardown and assertions

**Annotations**
- @Test: It means it is a test method. Method is inherited
- @BeforeEach: Method is executed before each test method (@Test, @ParameterizedTest, @RepeatedTest, @TestFactory). It is inherited. Useful for common set up code: creating objects,setting up test data
- @AfterEach: Method is executed after each test method (@Test, @ParameterizedTest, @RepeatedTest, @TestFactory). It is inherited. Useful for common clean up code: releasing resources, cleaning up test data
- @BeforeAll: Method is executed only once, before all test methods (@Test, @ParameterizedTest, @RepeatedTest, @TestFactory). It is inherited. It must be a static method. Useful for getting database connections, connecting to servers
- @AfterAll: Method is executed only once, after all test methods (@Test, @ParameterizedTest, @RepeatedTest, @TestFactory).  It is inherited. It must be a static method. Useful for releasing database connections, disconnecting from servers

- @ParameterizedTest
- @RepeatedTest
- @TestFactory
- @TestTemplate
- @TestClassOrder
- @TestmethodOrder
- @TestInstance
- @DisplayName
- @DisplayNameGeneration
- @Nested
- @Tag
- @Disabled
- @Timeout
- @ExtendWith
- @RegisterExtension
- @TempDir

**Lifecycle methods**
- @BeforeEach
- @AfterEach
- @BeforeAll
- @AfterAll

**Assertions**
- assertEquals
- assertNotEquals
- assertNull
- assertNotNull
