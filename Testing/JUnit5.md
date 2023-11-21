## JUnit5
User Guide: https://junit.org/junit5/docs/current/user-guide/

**JUnit 5** = JUnit Platform + JUnit Jupiter + JUnit Vintage
 - Supports creating test cases
 - Automation of the test cases with pass / fail
 - Utilities for testsetup, teardown and assertions

### Annotations
- @Test: It means it is a test method. Method is inherited
- @BeforeEach: Method is executed before each test method (@Test, @ParameterizedTest, @RepeatedTest, @TestFactory). It is inherited. Useful for common set up code: creating objects,setting up test data
- @AfterEach: Method is executed after each test method (@Test, @ParameterizedTest, @RepeatedTest, @TestFactory). It is inherited. Useful for common clean up code: releasing resources, cleaning up test data
- @BeforeAll: Method is executed only once, before all test methods (@Test, @ParameterizedTest, @RepeatedTest, @TestFactory). It is inherited. It must be a static method. Useful for getting database connections, connecting to servers
- @AfterAll: Method is executed only once, after all test methods (@Test, @ParameterizedTest, @RepeatedTest, @TestFactory).  It is inherited. It must be a static method. Useful for releasing database connections, disconnecting from servers
- @DisplayName: Custom display name with spaces, special characters and emojis. Useful for test reports in IDE or external test runner.
- @DisplayNameGeneration: Generation the display name automatically. It is a class level annotation.
  - Simple: Removes trailing parentheses from test method name
    ```
    @DisplayNameGeneration(DisplayNameGenerator.Simple.class)
    ```
  - ReplaceUnderscores: Replace underscores in test method name with spaces
    ```
    @DisplayNameGeneration(DisplayNameGenerator.ReplaceUnderscores.class)
    ```
  - IndicativeSentences: Generate sentence based on test class name and test method name
    ```
    @DisplayNameGeneration(DisplayNameGenerator.IndicativeSentences.class)
    ```
- @TestmethodOrder: Configures the order /sort algorithm for the test methods. It is a class level annotation.
  - MethodOrderer.DisplayName: Sorts test methods alphanumerically based on display names
    ```
    @TestmethodOrder(MethodOrderer.DisplayName.class)
    ```
  - MethodOrderer.MethodName: Sorts test methods alphanumerically based on method names
     ```
    @TestmethodOrder(MethodOrderer.MethodName.class)
    ```
  - MethodOrderer.Random: Pseudo-random order based on method names
     ```
    @TestmethodOrder(MethodOrderer.Random.class)
    ```
  - MethodOrderer.OrderAnnotation: Sorts test methods numerically based on @Order annotation
    - @Order: Manually specify the order with an int number. It is a method level annotation. Order with lowest number has highest priority. Negative numbers are allowed.
    ```
    @TestmethodOrder(MethodOrderer.OrderAnnotation.class)
    class TestClass{
     @Order(1)
     void testRunIn2(){...}

     @Order(3)
     void testRunIn3(){...}

     @Order(-5)
     void testRunIn1(){...}
    
    }
    ```
- @ParameterizedTest
- @RepeatedTest
- @TestFactory
- @TestTemplate
- @TestClassOrder

- @TestInstance


- @Nested
- @Tag
- @Disabled
- @Timeout
- @ExtendWith
- @RegisterExtension
- @TempDir

### Assertions
- assertEquals
- assertNotEquals
- assertNull
- assertNotNull
- assertSame: Assert that items refer to same object
- assertNotSame: Assert that items do not refer to same object
- assertTrue: Assert that condition is true
- assertFalse: Assert that condition is false
- assertArrayEquals: Assert that both objects arrays are deeply equal
- assertIterableEquals: Assert that both object iterables (ArrayList, LinkedList, HashSet, TreeSet) are deeply equal
- assertLinesMatch: Assert that both lists of strings match
- assertThrows: Assert that an executable throws an exception of expected type
- assertTimeoutPreemptively: Assert that an executable completes before given timeout is exceeded.
