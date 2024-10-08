## Regular Expression (Regex)
Regular expression is a sequence of characters that forms a search pattern. Regular expression can be used to perform all types of text search and text replace operations.
Regular expression is in java.util.regex package. The package includes the following classes:
- **Pattern** class: Defines a pattern (to be used in a search): with method compile() create pattern.
  ```
  Pattern pattern = Pattern.compile("hello", Pattern.CASE_INSENSITIVE);
  Pattern.CASE_INSENSITIVE:
  Pattern.LITERAL
  Pattern.UNICODE_CASE
  ```
- **Matcher** class: Used to search for the pattern: With method matcher() can search for the pattern in a string.
  ```
  Matcher matcher = pattern.matcher("Hello World");
  ```
- **PatternSyntaxException** class: Indicates syntax error in a regular expression pattern. With method find() can know if the pattern was found int the string.
  ```
  boolean matchFound = matcher.find();
  ```
```
^ - Starts with
$ - Ends with
[] - Range
() - Group
. - Single character
+ - one or more characters in a row
? - optional preceding character match
\ - escape character
\n - new line
\d - Digit
\D - Non-digit
\s - White space
\S - Non-white space
\w - alphanummeric / underscore character (word chars)
{x,y} - Repeat low (x) to high (y) (no "y" means at lease x, no ",y" means
(x|y) - Alternatice - x or y
[^x] - Anything but x (where x is whatever character you want)
```

```
String regexPatternVersion = "((?<major>[0-9]{1,2}).(?<minor>[0-9]{1,2}).(?<patch>[0-9]{1}))";
Pattern pattern = Pattern.compile(regexPatternVersion);
Matcher matcher = pattern.matcher(version);
if(matcher.matches()) {
  major = Integer.parseInt(matcher.group("major"));
  minor = Integer.parseInt(matcher.group("minor"));
  patch = Integer.parseInt(matcher.group("patch"));
}
```
