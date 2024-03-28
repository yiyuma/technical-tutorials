### Run java code in cmd
```
// compile java project
javac projectname.java;
// run a java project
java project;
// run a jar file
java -jar filename.jar
// run spring-boot project with maven
mvn spring-boot:run
```

### Modifiers (Access modifiers and non-access modifiers)
- **Access modifiers** (prvate, default, protected, public): is used to set the access level for classes, attributes, methods and constructors. For classes (public, default), for attributes, mehtods and constructors (public, protected, default, private) 
  - private: only within the class
  - default: within the class and the package. If you do not specify any access level, it will be the default.
  - protected: within the class, the package, outside the package through child class.
  - public: everywhere
- **Non-access modifiers** (final, abstract, static, transient, synchronized, volatile). for classes (final, abstract), for methods and attributes (final, static, abstract, transient, synchronized, volatile)
  - final:
    - for classes: The class cannot be inherited by other classes.
    - for attributes and methods: Attributes and methods cannot be overriden or modified. Constructor cannot mark as final.
  - abstract: The purpose of an abstract class is to function as a base for subclasses. Encapsulate some common functionality in one place and let sub classes implement differences.
    - for classes: The class cannot be used to create objects. To access an abstract class, it must be inherited from another class. The abstract class can also be used to provide some implementation of the interface, In such case, the end user may not be forced to override all the methods of the interface.
    - for attributes and methods:
  - static: only for attributes and methods. 

### StringBuilder, StringBuffer, String
**StringBuilder** in Java represents a mutable sequence of characters. StringBuilder Class provides no guarantee of synchronization.<br>
**StringBuffer** in Java represents a mutable sequence of characters. StringBuilder Class provides guarantee of synchronization.<br>
String Class in Java creates an immutable sequence of characters.


### Java Date and Time
- **LocalDate**: represents a date (year, month, day(yyyy-MM-dd))
- **LocalTime**: represents a time (hour, minute,second and nanosecondes (HH-mm-ss-ns)
- **LocalDateTime**: represents both a date and a time (yyyy-MM-dd-HH-mm-ss-ns)
- **DateTimeFormatter**: formatter for displaying and parsing date-time objects (E: Thu)
```
// display the current date from the system time zone
LocalDate.now();
// display the current time from the system time zone
LocalTime.now();
// display the current date and time from the system time zone
LocalDateTime.now();
// display the current date and time of the zone id
LocalDateTime.now(ZoneId.of("Asia/Shanghai"));
// define a time formatter
DateTimeFormatter timeFormatter = DateTimeFormatter.ofPattern("dd-MM-yyyy HH:mm:ss);
// display the current date and time with the defined time formatter
LocaDateTime dateTime = LocalDateTime.now();
dateTime.format(timeFormatter);
```
