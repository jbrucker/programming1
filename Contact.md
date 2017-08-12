## Email 

For my email, invoke this method with my name:
```java
public static String email(String first, String last) {
    final char AT = '@';
    StringBuilder sb = new StringBuilder();
    sb.append(Character.toLowerCase(first.charAt(0)))
      .append('.')
      .append(last.toLowerCase())
      .append(AT).append("ku.th");
    return sb.toString();
}
```
When you need to join or modify Strings, 
a
<a href="https://docs.oracle.com/javase/7/docs/api/java/lang/StringBuilder.html">
StringBuilder</a> (as above) is more efficient than using Strings.
Stringbuilder is mutable (the methods modify the existing StringBuilder)
while Strings are immutable (every operation creates a new String). 