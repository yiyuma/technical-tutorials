### Java Programming Language
Java is Compiler and Interpreter.<br>
- Source code: Java source code is written in ***plain text*** files. The extension of the file is ***.java***.
- Bytecode: ***Java Compiler*** compiles the source file (.java file) into ***.class*** file. The .class file contains only bytecodes. <br> The bytecode is the machine language of the JVM.
- Process:
  - Compiler: .java file --> Java compiler --> .class file
    ```
       // Java Compiler compiles java project in cmd. The ABC.class file will be created.
       javac ABC.java
    ```
  - Interpreter .class file --> JVM --> excutable file
    ```
     Java launcher tool interpretes the application with an instance of the JVM.
     // Interpret a java project
     java projectName;
     // run a jar file
     java -jar projectName.jar
     // run spring-boot project with maven
     mvn spring-boot:run
    ```

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

### Java doc: 
The comments in the source code.
