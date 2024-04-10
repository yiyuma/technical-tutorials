## Key words
- **const**: this will declare the variable as "constant", which means unchangeable and read-only.



## String
String separate in an array with separator ;
```
string name;
List<string> names = name.Split(';').Select(n=>n.Trim()).Where(n=>!n.IsNullOrEmpty).ToList();
```
An string array to a string with separator ,
```
List<string> names;
string name = string.Join(",", names);
```
          
