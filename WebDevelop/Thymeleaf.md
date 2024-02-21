## Thymeleaf 
Link:  www.thymeleaf.org <br>
Thymeleaf is a Java templating engine. It used to generated the HTML views for web apps.

### Thymeleaf template
- can be an HTML page with some Thymeleaf epressions
- Include dynamic content from Thymeleaf expressions
- Thymeleaf is processed on the server.
- Results included in HTML returned to browser

### Add Thymeleaf template
- Add Thymeleaf to Maven POM file
  ```
  <dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-thymeleaf</artifactId>
  </dependency>
  ```
- Thymeleaf template files go in **src/main/resources/templates**
- For web apps, Thymeleaf templates have a .html extension
- Using CSS with Thymeleaf Templates. css files will be placed in **scr/main/resources/static/css/** folder
  - Can use local CSS files as part of the project
    ```
    <!-- reference local CSS file in HTML file -->
    <link ref="stylesheet" th:href="@{/css/demo.css}" />
    ```
  - Reference remote CSS files
    ```
    <!-- reference remote CSS file in HTML file -->
    <link ref="stylesheet" href="@{http://webaddress/demo.css}" />
    ```
