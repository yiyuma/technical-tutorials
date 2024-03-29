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

### Data Types
- **Primitive Data Types**: Primitive data types are predefined in Java. A primitive data type begins with a lower case. Primitive variables live in the stack memory. A primitive variable has always a value. Primitives variable has no attributes or behaviors.<br>
  - Integer types: byte (8 bits), short(16 bits), int (32 bits), long (64 bits, should end the value with an "L"). The default value is 0.
  - Floating point types: a number with a decimal
    - float: 32 bits. It should be end the value with "f". The precision of float is only 6 or 7 decimal digits. The default value is 0.0f.
    - double: 64 bits. It should be end the value with "d". The precision of double is about 15 digits. The default value is 0.0d.
    - Scientific numbers: a floating point number can also be a scientific number with an "e" to indicate the power of 10.
  - Others: boolean (1 bit), Default value is false. char (16 bits), default value is \u0000. <br>
Char is with a single quotes. Java uses Unicode system. In Unicode, character holds 2 byte (16 bits), so java also uses 2 byte for char.
  - Casting
    - Widening Casting (automatically) converting a smaller type to a larger size type. <br>
      byte -> short -> char -> int -> long -> float -> double
    - Narrowing Casting (manually) converting a larger type to a smaller size type. <br>
      double -> float -> long -> int -> char -> short -> byte
    ```
      // widening casting
      int intValue = 3;
      double doubleValue = intValue;
      // narrowing casting
      double doubleValue = 3,14d;
      int intValue = (int) doubleValue;
    ```
- **Reference Data Types**: A reference data type refers to an object. It begins with an upper case.
 The reference variables live in the heap memory. The reference variable can be null. The reference variable has attributes or behaviors. <br>
String, Arrays, Classes
- **Wrapper classes**: Wrapper class provides the mechanism to convert primitive data type into object and object into primitive data type. The default value is null. Wrapper classes are immutable.
  - Boolean, Character, Byte, Short, Integer, Long, Float, Double
  - In the case we need to use wrapper classes:
    - Change the value in method
    - Serialization
    - Synchronization: Java synchronization works with objects in Mutlithreading
    - java.util.pachage
    - Collection framework
  - Autoboxing and Unboxing
    - Autoboxing: primitive data type -> wrapper class
    - Unboxing: wrapper class -> primitive data type
      ```
      // Autoboxing
      int a = 20;
      Integer i = a;
      // Unboxing
      Integer i = new Integer(20);
      int a = i;
      ```

### Call by value vs. Call by reference
- Call by value: Parameters passed to the callee method will be clones of original parameters. Any changes to one variable donot modify the other.
- Call by reference: The unique identifier of the object is sent to the method. Any changes to the parameter's instance members will result in that change being made to the original value.
- Parameter passing in Java is always **call by value**.
  - For primitive types, parameters are call by value. 
  - For object types, the object reference is call by value. All objects are dynamically stored in Heap memory. In the stack memory are stored the addresses of the object.

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
