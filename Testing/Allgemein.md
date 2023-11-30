### Tranditional Development
Design -> Code -> Test

### Test Driven Development (TDD)
Test(First, write a failing test) -> Code( Write code to make the test pass) -> Refactor (Refactor and improve on design) -> Test (Report process for the next test) -> ...<br>
It is a continue loop.

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
  - Add Maven Surefire Plugin: maven.surefire-report-plugin
  ```
  // To use Maven to create report with code coverage, you have to at first add plugin in the build in pom.xml.
    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-surefire-plugin</artifactId>
                <configuration>
                    // create HTML report if the tests failed.
                    <testFailureIgnore>true</testFailureIgnore>
                    // show display name in the HTML report
                    <statelessTestsetReporter implementation="org.apache.maven.plugin.surefire.extensions.junit5.JUnit5Xml30StatelessReporter">
                        <usePhrasedTestCaseMethodName>true</usePhrasedTestCaseMethodName>
                    </statelessTestsetReporter>
                </configuration>
            </plugin>

            // report
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

            // Java Code Coverage (Add jacoco)
            <plugin>
                <groupId>org.jacoco</groupId>
                <artifactId>jacoco-maven-plugin</artifactId>
                <version>0.8.7</version>
                <executions>
                    <execution>
                        <id>jacoco-prepare</id>
                        <goals>
                            <goal>prepare-agent</goal>
                        </goals>
                    </execution>
                    <execution>
                        <id>jacoco-report</id>
                        <phase>test</phase>
                        <goals>
                            <goal>report</goal>
                        </goals>
                    </execution>
                </executions>
            </plugin>
        </plugins>
    </build>
  ```
  - run tests and executes Surefire Report Plugin to generate HTML reports using Maven in the terminal
  ```
  mvn clean test
  ```
  - Using Maven in the cmd (site: add website resources, images, css etc...), -DgenerateReports=false: Don't overwrite existing HTML reports
  ```
  mvn site -DgenerateReports=false
  ```

