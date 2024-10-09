## Data Types
- **Primitive Data Types**: Primitive data types are predefined in Java. A primitive data type begins with a lower case. Primitive variables live in the stack memory. A primitive variable has always a value. Primitives variable has no attributes or behaviors.<br>
  - Integer types: byte (8 bits), short(16 bits), int (32 bits), long (64 bits, should end the value with an "L"). The default value is 0.
  - Floating point types: a number with a decimal
    - float: 32 bits. It should be end the value with "f". The precision of float is only 6 or 7 decimal digits. The default value is 0.0f.
    - double: 64 bits. It should be end the value with "d". The precision of double is about 15 digits. The default value is 0.0d.
    - Scientific numbers: a floating point number can also be a scientific number with an "e" to indicate the power of 10.
  - Others:
    - boolean (1 bit), Default value is false. char (16 bits), default value is \u0000.
    - Char is with a single quotes. Java uses Unicode system. In Unicode, character holds 2 byte (16 bits), so java also uses 2 byte for char.
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
## String
- Convert String to int: int intValue = Integer.parseInt(stringValue);
- Convert int to String: string stringValue = Integer.toString(intVallue);
  
## Call by value vs. Call by reference
- Call by value: Parameters passed to the callee method will be clones of original parameters. Any changes to one variable donot modify the other.
- Call by reference: The unique identifier of the object is sent to the method. Any changes to the parameter's instance members will result in that change being made to the original value.
- Parameter passing in Java is always **call by value**.
  - For primitive types, parameters are call by value. 
  - For object types, the object reference is call by value. All objects are dynamically stored in Heap memory. In the stack memory are stored the addresses of the object.

## Stack memory and Heap space
- **Stack memory** in Java is used for static memory allocation and the execution of a thread. LIFO (Last In First Out). If this memory is full, Java throws **java.lang.StackOverFlowError**. <br>
  **Frame**: A Stack frame contains all the data for one function call. The stack frame only exists during the execution time of a function including any references.
- **Heap space** Heap space is used for the dynamic memory allocation of Java objects and JRE classes at runtime. New objects are always create in heap space. References to these objects are stored in stack memory. If heap space is full, Java throws **java.lang.OutOfMemoryError**. 

## Modifiers (Access modifiers and non-access modifiers)
- **Access modifiers** (prvate, default, protected, public): is used to set the access level for classes, attributes, methods and constructors. For classes (public, default), for attributes, mehtods and constructors (public, protected, default, private) 
  - private: only within the class
  - default: within the class and the package. If you do not specify any access level, it will be the default.
  - protected: within the class, the package, outside the package through child class.
  - public: everywhere
- **Non-access modifiers** (final, abstract, static, transient, synchronized, volatile). for classes (final, abstract), for methods and attributes (final, static, abstract, transient, synchronized, volatile)
  - final:
    - for classes: The class cannot be inherited by other classes.
    - for attributes and methods: Attributes and methods cannot be overriden or modified. Constructor cannot mark as final.
  - abstract: The purpose of an abstract class is to function as a base for subclasses. Encapsulate some common functionality in one place and let sub classes implement differences. It can only be used in an abstract class, and can only be used on method.
    - for classes: The class cannot be used to create objects. To access an abstract class, it must be inherited from another class. The abstract class can also be used to provide some implementation of the interface, In such case, the end user may not be forced to override all the methods of the interface.
    - for methods: The method does not have a body. The body is provided by the subclass.
  - static: only for attributes and methods. Attributs and methods belongs to the class, rather than an object. A static method means that it can be accessed without creating an object of the class.
  - transient: Attributes and methods are skipped when serializing the object containing them.
  - synchronized: Methods can only be accessed by one thread at a time
  - volatile: The value of an attributes is not cached thread-locally, and is always read from the "main memory"

## Collections
Collection is an object. It groups multiple elements into a single unit.<br>
Collections are used to store, retrieve, manipulate, and communication aggregate data.
- Interfaces: Collection interfaces are generic.
  - interface Set extends Collection: in package java.util.Set. It cannot contain duplicate elements.
    ```
    int size();
    boolean isEmpty();
    boolean contains(Object element);
    boolean add(E element);
    boolean remove(Object element);
    Iterator<E> iterator();
    boolean containsAll(Collection<?> c);
    boolean addAll(Collection<?> c);
    ```
  - interface SortedSet extends Set: a Set that maintains its elements in ascending order.
  - interface List extends Collection: in package java.util.List. It is an ordered collection. List can contain duplicate elements. With index can man element insert or access.
  - interface Queue extends Collection: A Queue provides additional insertion, extraction and inspection operations. Queues order elements in a FIFO manner.
  - interface Deque extends Collection:  A Deque provides additional insertion, extraction and inspection operations. Deque can be used as FIFO and LIFO.
  - interface Map: an object that maps keys to values. A Map cannot contain duplicate keys. Each key can map to at most one value.
  - interface SortedMap: a Map that maintains its mappings in ascending key order.

## StringBuilder, StringBuffer, String
**StringBuilder** in Java represents a mutable sequence of characters. StringBuilder Class provides no guarantee of synchronization.<br>
**StringBuffer** in Java represents a mutable sequence of characters. StringBuilder Class provides guarantee of synchronization.<br>
String Class in Java creates an immutable sequence of characters.


## Java Date and Time
- **LocalDate**: represents a date (year, month, day(yyyy-MM-dd))
  ```
    // display the current date from the system time zone
    LocalDate localDate = LocalDate.now();
    // get current year
    int year = localDate.getYear();
    // get current month
    int month = localDate.getMonthValue();
    // get current day
    int day = localDate.getDayOfMonth();
  ```
- **LocalTime**: represents a time (hour, minute,second and nanosecondes (HH-mm-ss-ns)
- **LocalDateTime**: represents both a date and a time (yyyy-MM-dd-HH-mm-ss-ns)
  ```
    // display the current date and time from the system time zone
    LocalDateTime localDateTime = LocalDateTime.now();
    var year = Integer.toString(localDateTime.getYear());
    var month = Integer.toString(localDateTime.getMonthValue());
    var day = Integer.toString(localDateTime.getDayOfMonth());
    var hour = Integer.toString(localDateTime.getHour());
    var minute = Integer.toString(localDateTime.getMinute());
    // display the current date and time of the zone id
    LocalDateTime.now(ZoneId.of("Asia/Shanghai"));
  ```
- **DateTimeFormatter**: formatter for displaying and parsing date-time objects (E: Thu)
```
  // define a time formatter
  DateTimeFormatter timeFormatter = DateTimeFormatter.ofPattern("dd-MM-yyyy HH:mm:ss);
  // display the current date and time with the defined time formatter
  LocaDateTime dateTime = LocalDateTime.now();
  dateTime.format(timeFormatter);
```

## Regular Expression (Regex)
Regular expression is a sequence of characters that forms a search pattern. Regular expression can be used to perform all types of text search and text replace operations.<br>
Regular expression is in **java.util.regex** package. The package includes the following classes and interface:
- **Pattern** class: Defines a pattern (to be used in a search): with method **compile(param1, param2)** create pattern.
  - param1: indicates which pattern is being searched for.
  - param2: the flag
    - Pattern.CASE_INSENSITIVE: case insensitive
    - Pattern.LITERAL: Special characters in the pattern will not have any special meaning and will be treated as ordinary characters when performing a search.
    - Pattern.UNICODE_CASE: Use it together with the CASE_INSENSITIVE flag to also ingore the case of letters outside of the English alphabet.
  ```
  Pattern pattern = Pattern.compile("hello", Pattern.CASE_INSENSITIVE); 
  ```
- **Matcher** class: Used for performing match operations on text using patterns: With method **matcher(param1)** can search for the pattern in a string. Param1 is the string to check.
  ```
  Matcher matcher = pattern.matcher("Hello World");
  ```
  With method **find()** can know if the pattern was found in the string.
- **PatternSyntaxException** class: used for Indicating syntax error in a regular expression pattern. It is an uncheck exception.
  ```
  boolean matchFound = matcher.find();
  ```
- **MatchResult** Interface: Used for representing the result of a match operation.

```
^ - Starts with
$ - Ends with
[] - Range
() - Group
. - Any dingle character
+ - one or more characters in a row
? - once or not
* - zero or not once
\ - escape character
\n - new line
\d - Digit [0-9]
\D - Non-digit [^0-9]
\s - White space [\t\n\x0B\f\r]
\S - Non-white space  [^\s]
\w - alphanummeric / underscore character (word chars) [a-zA-Z_0-9]
\W - Non-word character  [^\w]
\b - Word boundary
\B - Non-Word boundary
{n} - appears n times
{n,} - appears n times or more than n
{x,y} - Repeat low (x) to high (y) (no "y" means at lease x, no ",y" means
(x|y) - Alternatice - x or y
[^x] - Anything but x (where x is whatever character you want)
```
