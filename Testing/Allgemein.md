### Tranditional Development
Design -> Code -> Test

### Test Driven Development (TDD)
Test(First, write a failing test) -> Code( Write code to make the test pass) -> Refactor (Refactor and improve on design) -> Test (Report process for the next test) -> ...

### Unit Test Code Coverage
Code Coverage measures how many methods / lines are called by the tests. It is represented as a percentage.
- Use **IntelliJ** to check code coverage. IntelliJ has built-in support for code coverage.
  - It can generate coverage reports in the IDE.<br>
    Select the project -> click the right mouse -> select "Run "project name" with coverage" in the context menu
  - It can generate coverage reports in the HTML file.<br>
    In the tab "Coverage" select "Generate Coverage Report..."
  - Generate test result report
    In the tab "Cover" select "Export Test Results..."
- Use **Maven** to check code coverage. It is useful when running as part of DevOps build process, or CI/CD environments.
  - Maven Surefire Plugin: maven.surefire-report-plugin
  ```
  // run tests and executes Surefire Report Plugin to generate HTML reports using Maven in the terminal
  mvn clean test
  // To use Maven to create report, you have to add plugin in the build in pom.xml.
      <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-surefire-plugin</artifactId>
                  
            </plugin>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-surefire-report-plugin</artifactId>
                <version>3.0.0-M5</version>
                <executions>
                    <execution>
                        <phase>test</phase>
                        <goals>
                            <goal>report</goal>
                        </goals>
                    </execution>
                </executions>
            </plugin>
        </plugins>
    </build>
  // Using Maven in the cmd (site: add website resources, images, css etc...), -DgenerateReports=false: Don't overwrite existing HTML reports
  
  mvn site -DgenerateReports=false
  
  ```

