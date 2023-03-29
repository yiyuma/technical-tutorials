Spring stellt eine große Menge von Open-Source Java Framework zur Verfügung.
z.B. 
- Spring Framework ist der Basis von allen Frameworks, die Spring zur Verfügung stellt.
- Spring Boot vereinfacht die Entwicklung der Web-Anwendung, denn Spring Boot ein embedded Tomcat (Servlet Container) hat.
- Spring Data bietet die Funktionen für Zugriff auf verschiedene relationale und NoSQL Datenbanken.
- Spring Data JPA ist eine Implementierung von Java Pesistence API (JPA).
- Spring MVC bietet die Funktionen für Entwicklung Webanwendung mit den Desing Pattern MVC.
- Spring Security stellt die Funktionen für Sicherheit der Webanwendung zur Verfügung. z.B. Unterstützung für Java web token (JWT), Authentifizierung  und Autorisierung. 

Inversion of Control (IoC) ist der Kern von Spring Framework, ist gleich wie Dependence Injection (DI).
D.h. Man erzeugt nicht selber die Beans, sondern konfiguriert man die Beans, und IoC Container übernimmt die Erzeugung von Beans.

Bean ist ein Objekt, das von Spring IoC Container instanziiert und verwaltet.
Spring hat 3 Möglichkeiten für Konfiguration des IoC Containers,
- XML based Konfiguration , ClasspathXmlApplicationContext.java
- Annotationen based Konfiguraion, @Component, @Controller, @Service, @Repository, @Autowired, @Primary(bei mehrere Bean Kandidaten), @Qualifier("myBean"), @Value("${build.info}"), @PropertyResource("classpath:build.info"), @ConfigurationProperties(prefix = "ekl.backend")

```
public class MovieRecommender {
    @Autowired
    @Qualifier("main")
    private MovieCatalog movieCatalog;
}
 
 public class MovieRecommender {
    private final MovieCatalog movieCatalog;
    
    @Autowired
    public void prepare(@Qualifier("main") MovieCatalog movieCatalog) {
        this.movieCatalog = movieCatalog;
    }
}

@Configuration
@PropertySource("classpath:build-info.properties")
@Getter
public class BuildInfoConfigure {
    @Value("${build.info}")
    private String buildInfo;
}
in file build-info.properties
build.info=1.0.1
```
Der Wert von "build.info" wird durch key value aus Spring Environment (application*.properties und Umgebugebungsvariablen von OS) aufgelöst. 
Wenn build.info nicht vorhanden ist, dann default value
```
@Configuration
@Getter
public class BuildInfoConfigure {
    @Value("${build.info:default value}")
    private String buildInfo;
}

```
Mit @ConfigurationProperties(prefix = "ekl.backend") kann man ein Bean erzeugen.
```
@ConfigurationProperties(prefix = "ekl.backend")
@Getter
@Setter
@Configuration
public class BuildInfoConfigV3 {
    private String version;
    private Map<String, String> properties;
}
```
- Java-based Konfiguraion, @Configuration + @Bean oder @Component + @ Bean ==> Bean Factory Methode

3 Möglichkeiten für Dependence Injection:
- Constructor-Based Dependency Injection: Die Abhängigkeiten (Dependencies) einer Klasse werden durch Aufruf eines Konstruktors aufgelöst. Dabei sucht IoC Container einen Konstruktor aus, der die größte Anzahl von Argumenten hat und alle Argumente können per DI injitziert werden.
- Setter-Based Dependency Injection: Die Abhängigkeit wird durch eine setter Methode mit @Autowired aufgelöst .
- Fields-Based Dependency Injection: Die Abhängigkeit wird durch ein Attribut (Field) mit @Autowired aufgelöst.

Bean Scope
Singelton: Nur eine einzige Instanz in IoC Container
Prototype: Bei jedem Aufruf wird eine neue Instanz erzeugt.Jedes Mal wenn ein Bean benötigt wird, wird eine neue Instanz erzeugt.
request: Im Lifecycle von ein HTTP request gibt es nur ein Bean. @RequestScope
session: Im Lifecycle von ein HTTP session gibt es nur ein Bean. @SessionScope
application:Im Lifecycle von ein ServletContext gibt es nur ein Bean. @ApplicationScope
websocket: Im Lifecycle von ein WebSocket gibt es nur ein Bean. @Scope(scopeName = "websocket", proxyMode = ScopedProxyMode.TARGET_CLASS)

Bean Lifecycle: Mann kan mit Annotations (@PostConstruct und @PreDestroy) und Methode (afterPropertySet(), init()) die Bean Lifecycle beeinflussen.  

Spring Expression Language (SpEL)

Servlet ist eine Java API, die die HTTP Methoden mit Java spezifiziert. Tomcat ist eine Implementierung von Servlet.
HTTP Methode: Get, Put, Delete, Post
HTTP Status Code: 
1xx informational response
2xx successful: 200 (OK), 202(Accepted)
3xx redirecton
4xx client errors: 403 (Forbidden), 404(Not Found), 405(Method not Allowed)
5xx server errors: 500 (Internal Server Error), 501(Not Implemented), 502 (Bad Gateway)

@Resource = @Autowired, von jakarta.annotation.Resource.

JSR: Java Specification Request
Authentifizierung ist für Identifizierung des Benutzers verantwortlich.
Autorisierung prüft, ob der Benutzer ausreichende Berechtigungen für Zugriff auf angesprochene Resource besitzt.
Konfiguration ist der Vorgang, wo das Verhalten von IoC Container festgelegt wird.
Definition ist das Ergebnis von z.B. Deklaration.
Deklaration ist ein Teil von der Konfiguration.
Implementierung = Umsetzung
Rautenzeichen #
Aspektorientierte Programmierung (AOP), @AspectJ


ConditionalOnProperties
Spring Validation z.B. @NotNull
WebSocket
