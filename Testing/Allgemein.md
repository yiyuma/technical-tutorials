### Tranditional Development
Design -> Code -> Test

### Test Driven Development (TDD)
Test(First, write a failing test) -> Code( Wirte code to make the test pass) -> Refactor (Refactor and improve on design) -> Test (Repert process for the next test) -> ...

### Code Coverage
Code Coverage measures how many methods / lines are called by the tests. It is represented as a percentage.
- IntelliJ has built-in support for code coverage.
  - It can generate coverage reports in the IDE.<br>
    Select the project -> click the right mouse -> select "Run "project name" with coverage" in the context menu
  - It can genarate coverage reports in the HTML file.<br>
    In the tab "Coverage" select "Generate Coverage Report..."
  - Generate test result report
    In the tab "Cover" select "Export Test Results..."
- Use Maven to check code coverage. It is useful when running as part of DevOps build process, or CI/CD enviroments.
  - Maven Surefire Plugin: maven.surefile-report-plugin
  ```
  // run tests using Maven
  mvn clean test
  // generat test report
  mvn site
  ```

