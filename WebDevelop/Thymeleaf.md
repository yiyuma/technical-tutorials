## Thymeleaf 
Link:  www.thymeleaf.org <br>
Thymeleaf is a Java templating engine. It used to generated the HTML views for web apps.

### Thymeleaf template
- can be an HTML page with some Thymeleaf epressions
- Include dynamic content from Thymeleaf expressions
- Thymeleaf is processed on the server.
- Results included in HTML returned to browser

**Add Thymeleaf to Maven POM file**
```
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-thymeleaf</artifactId>
</dependency>
```
**Thymeleaf template files go in src/main/resources/templates** <br>
For web apps, Thymeleaf templates have a .html extension<br>
