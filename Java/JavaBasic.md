### Java Programming Language
Java is a compiled and interpreted language.<br>
- Source code: Java source code is written in ***plain text*** files. The extension of the file is ***.java***.
- Bytecode: ***Java Compiler*** compiles the source file (.java file) into ***.class*** file. The .class file contains only bytecodes. <br> The bytecode is the machine language of the JVM.
- Process:
  - compiled: java file --> Java compiler --> .class file
    ```
       // Java Compiler (in JDK) compiles java project in cmd. The ABC.class file will be created.
       javac ABC.java
    ```
  - interpreted: .class file --> JVM --> excutable file
    ```
     Java launcher tool interpretes the application with an instance of the JVM.
     // Interpret a java project
     java projectName;
     // run a jar file
     java -jar projectName.jar
     // run spring-boot project with maven
     mvn spring-boot:run
    ```
- Compiler vs. Interpreter
  - Compiler processes all statements of code. Interpreter reads each statement of code.
  - Compiled: Code will be transformed into machine readable instructions (bytecode) and can be executed directed by computer's cpu.
  - Interpreted: Code donot need to transform. Another program executes code.

### Java Compiler
Java Compiler can compile Java ***source code*** into ***.class file***. It can able to detect errors in the code or errors when reading it. The cmd command is ***javac***.

### Java Virtual Machine (JVM): 
JVM provides Runtime Enviroment in which Java bytecode can be executed. <br>
It is platform dependent. For each software and hardware we have different JVM configuration.
Task:
  - Loads code
  - Verifies code
  - Executes code
  - Provides Runtime Enviroment

### Java Runtime Enviroment (JRE): JVM + Set of libraries
JRE is the minimun required to run a java code.<br>
The libraries will be used by JVM at runtime

### Java Development Kit (JDK): JRE + Development Tools (Debugger + Compiler + Java Doc)

### Integrated Development Enviroment (IDE): 
- IntelliJ,
- Eclipse
- ...

### Type checking
Type checking is the process of verifying and enforcing the constraints of types.
- static check: at compile time
- dynamic check: at runtime

  
### Java doc
The comments in the source code. IDE can export comments in Java code as a document.

### Classpath
The path for the .class files. It is defined in the Variable Environment. JVM will find all the .class files by ***Class Path***.

### .jar file, .war file and .ear file
- .jar file: Java ARchive file
- .war file: Web application file
- .ear file: Enterprise application ERchive file
