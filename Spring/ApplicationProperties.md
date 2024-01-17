## application.properties
Link: https://docs.spring.io/spring-boot/docs/current/reference/html/application-properties.html <br>

Inject properties into Spring Boot application using **@Value**.
```
@Value("${info.app.name}")
private string infoAppName;
```

### Application information
```
info.app.name=test project
info.app.description=This is a test project
info.app.verion=1.0.0
```

### Web
```
// HTTP server port
server.port=7000
// Context path of the application
server.servlet.context-path=/my-app
// Default HTTP session time out
server.servlet.session.timeout=15m
```

### Database configuration
```
// JDBC URL of the database
spring.datasource.url=jdbc:mysql://localhost:3306/databaseUrl
// Login username of the database
spring.datasource.username=user
// Login password of the database
spring.datasource.password=password
```

### Security
```
// Override default username (user) and set password
spring.security.user.name=newUser
spring.security.user.password=password
```

### Actuator
```
management.endpoints.web.exposure.include=health,info
management.endpoints.web.exposure.include=*
management.endpoints.web.exclude=health
// Base path for actuator endpoints
management.endpoints.web.base-path=/actuator
```

### Turn off the spring boot banner
```
spring.main.banner-mode=off
```

### Logging level
```
// warn is only for warning and error
logging.level.root=warn
```

### info about app
This infos will be shown in actuator/info.
```
info.app.name=myApp
info.app.description=This is my first app.
info.app.version=1.0.0
```

### Custom properties
```
coach.name=Winne
coach.company=CompanyOne
```
