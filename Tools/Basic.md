## Java JDK (Java SE Development Kit)
- Download link: https://www.oracle.com/java/technologies/downloads/  
- Install Java JDK
- Set environment varialbes:
  - Add java bin folder in the path: Environment variables -> Path -> Edit -> New -> type C:\Program Files\Java\jdk-17\bin
  - Set JAVA_HOME: Environment variables -> New… -> Name of the variable = JAVA_HOME, Value of the variable = C:\Program Files\Java\jdk-17
- Check java version in cmd
  ```
  java -version
  ```

## Maven (Build automation tool)
- Download link: https://maven.apache.org/download.cgi?.
- Unzip file in the programm file folder
- Set environment varialbes:
  - Add maven bin folder in the path: Environment variables -> Path -> Edit -> New -> type C:\Program Files\apache-maven-3.9.5\bin
- Check maven version in cmd
  ```
  mvn -v
  ```

## IntelliJ (IDE, Integrated Development Enviroment)
- Download link: https://www.jetbrains.com/idea/download/?fromIDE=&section=windows

## MySQL (Relational Database)
- Download link: https://dev.mysql.com/downloads/windows/installer/8.0.html <br>
- We install 
  - MySQL Community Server
  - MySQL Workbench
  - MySQL Shell
- Set environment varialbes:
  - Add MySQL Server bin folder in the path: Environment variables -> Path -> Edit -> New -> type C:\Program Files\MySQL\MySQL Server 8.1\bin
- Check MySQL version in cmd
  ```
  mysql --version
  ```

## Git (Version control)
- Download link: https://git-scm.com/downloads
- Check Git version in cmd
  ```
  git -v
  or
  git --version
  ```

## Postman
Postmann is a client tool. It can send HTTP requests to the REST Web Service / API, and then it will get the response, and we can actually view it there in the tool.

## Visual Studio Code
- Download link: https://code.visualstudio.com/

## node (Command-line tool)
For running JavaScript code from command-line.
- Download link: https://nodejs.org/download/release/v16.10.0/
- Check node version in cmd
  ```
  node --version
  ```

## npm (Node Package Manager) (Command-line tool)
It can download new node packages and features. Similar to Maven.
- Check npm version in cmd
  ```
  npm --version
  ```

## tcs (Command-line tool)
TypeScript Compiler
- Install tcs in cmd using npm
  ```
  npm install -g typescript@4.6.4
  ```
- Check tcs version in cmd
  ```
  tcs --version
  ```
