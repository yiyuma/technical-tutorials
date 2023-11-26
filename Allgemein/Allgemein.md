## REST
**REST (REpresentational State Transfer)** is lightweight approach for communicating between applications.
- REST calls can be made over HTTP.
- REST is language independent.
- REST applications can use any data format. (Commonly see XML and JSON)

**REST over HTTP** <br>
Leverage HTTP Method for CRUD Operation
- POST: **C**reate a new entity
- GET: **R**ead a list of entities or single entity
- PUT: **U**pdate an existing entity
- DELETE: **D**elete an existing entity

**HTTP Request Message** has 3 areas
- Request line: has the actual HTTP command or method (Post, Get, Put, Delete)
- Header variables: has the request metadata (additional information about the request)
- Message body: has the contents of the message or the actual payload

**HTTP Response Message** has 3 areas
- Response line: has server protocol and HTTP status code
- Header variables: has the response metadata
- Message body: has the contents of the message

**HTTP Status Code** <br>
- 1xx informational response
- 2xx successful: 200 (OK), 202(Accepted)
- 3xx redirection
- 4xx client errors: 401(Authentication Required) 403 (Forbidden), 404(File Not Found), 405(Method not Allowed)
- 5xx server errors: 500 (Internal Server Error), 501(Not Implemented), 502 (Bad Gateway)

**MIME Content Types (Multipurpose Internet Mail-Extension)** is a message format for the actual payload. It simply describes the acutal content or the format of the message being returned. Basic Syntax is type/sub-type. Example: text/html, text/plain (information that is returned to the client), application/json, application/xml(for RESTful client)

**JSON (JavaScript Object Notation)** is plain text data. It is lightweight data format for storing and exchanging data.
- Language independent.
- Can use with any programming language.
- Format:
  - Curley braces define object
  - Object members are name/value pairs, delimited by colons
  - Name is always in double-quotes
  - Values:
    - Numbers: no quotes
    - String: in double quotes
    - Boolean: true, false
    - Nested JSON object with curley braces
    - Array with square brackets[] (["Java", "JavaScript","C#", "Python"])
    - null

**CSV** (Comma-Separated Values) is text file format that uses commas to separat values.
