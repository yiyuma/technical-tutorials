## TypeScript
TypeScript is developed by Microsoft. It is a superset of JavaScript and ECMAScript. TypeScript >> ECMAScript >> JavaScript. <br>
The official link of TypeScript is Link: https://www.typescriptlang.org <br>

### TypeScript file
- TypeScript file has the **.ts** extension.
- Web browsers do not understand TypeScript. It must be convert from TypeScript code to JavaScript code. The convert calls **transpiling**.
  ```
  // Command to convert from the TypeScript code to JavaScript code. It will generate a js file (demoScript.js)
  tsc demoScript.ts
  ````
  
### Run generated JavaScript code in node
  ```
  node demoScript.js
  ```

### Variables
**Basis varialbes**
- boolean: true/false
- number: supports integer and floating point numbers
- string: Text data. enclosed in single or double quotes
  ```
  // string concatenation
  let firstName:string="Mia";
  let lastName:string="Schneider";
  console.log("Hi " + firstName + " " + lastName);
  console.log('Hi ${firstName} ${lastName}');
  ```
- any: supports "any" datatype assignment
  ```
  let data:any=50.0;
  data=flase;
  data="user";
  data=20;
  // the type of data is always changed, because its type is any.
  ```

**Define variables**
```
let <variableName>:<type> = <initial value>;
let count:int=3;
let isEabled:boolean=true;
let username:string="Admin";
```

### Keywords
- let: declare the variable.
