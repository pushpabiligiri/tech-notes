# Java String

## String
A String in Java is an object used to store a sequence of characters enclosed in double quotes.  
* Strings are immutable, meaning their value cannot be changed after creation.
* Java provides a rich API for manipulation, comparison, and concatenation of strings.
  
### Ways Of Creating a Java String
There are two ways to create a string in Java: 

**1. String literal (Static Memory)**  
A string literal is created by assigning a sequence of characters directly to a String variable using double quotes. Java stores string literals in the `String Constant Pool`, allowing identical string values to share the same object.  
**Example:**
```java
String str = “GeeksforGeeks”;
```

**2. Using new keyword (Heap Memory)**
Using the `new keyword` creates a new object in heap memory, even if the same string already exists in the pool.
* One object is created in the heap memory
* The string literal is stored in the string pool (if not already present)
* The reference variable points to the heap object, not the pool  
**Example:**
```java
String str = new String (“GeeksforGeeks”);
```

### Immutable String
String objects are **immutable**,Once a string object is created its data or state can't be changed.  
**Example**
```java
public class GFG{
    
    public static void main(String[] args) {

        String str = "Hello";

        str.concat(" World");

        System.out.println(str);
    }
}
```
```bash
Hello
```
### String Pool
The String Pool is a special area in heap memory where Java stores string literals. It helps save memory by reusing existing string objects when the same literal is used multiple times.  
**For example:**
```java
String s1 = "Geeks";
String s2 = "Geeks";
```

### String Methods   
Java provides several built-in methods in the `String` class to perform operations on Strings.  
Package: `java.lang` (no import required).

**Important String Methods**
| No. | Method                  | Description                                     |
| --- | ----------------------- | ----------------------------------------------- |
| 1   | `length()`              | Returns the number of characters                |
| 2   | `charAt()`              | Returns character at a specified index          |
| 3   | `equals()`              | Compares two Strings                            |
| 4   | `equalsIgnoreCase()`    | Compares Strings ignoring case                  |
| 5   | `toUpperCase()`         | Converts to uppercase                           |
| 6   | `toLowerCase()`         | Converts to lowercase                           |
| 7   | `substring()`           | Extracts part of a String                       |
| 8   | `contains()`            | Checks whether text exists                      |
| 9   | `startsWith()`          | Checks starting characters                      |
| 10  | `endsWith()`            | Checks ending characters                        |
| 11  | `trim()`                | Removes leading and trailing basic whitespace   |
| 12  | `strip()`               | Removes leading and trailing Unicode whitespace |
| 13  | `replace()`             | Replaces characters or text                     |
| 14  | `replaceAll()`          | Replaces regex matches                          |
| 15  | `replaceFirst()`        | Replaces first regex match                      |
| 16  | `split()`               | Splits String into an array                     |
| 17  | `indexOf()`             | Finds first occurrence                          |
| 18  | `lastIndexOf()`         | Finds last occurrence                           |
| 19  | `isEmpty()`             | Checks whether String is empty                  |
| 20  | `isBlank()`             | Checks empty or whitespace-only String          |
| 21  | `concat()`              | Joins two Strings                               |
| 22  | `compareTo()`           | Compares Strings lexicographically              |
| 23  | `compareToIgnoreCase()` | Compares ignoring case                          |
| 24  | `toCharArray()`         | Converts String into character array            |
| 25  | `valueOf()`             | Converts other data types into String           |
| 26  | `intern()`              | Returns canonical String from pool              |
| 27  | `matches()`             | Checks whether String matches a regex           |
| 28  | `repeat()`              | Repeats String (Java 11+)                       |
| 29  | `join()`                | Joins multiple Strings with delimiter           |
| 30  | `format()`              | Formats a String                                |

**Java Code Examples**
```java
public class StringMethods {
    public static void main(String[] args) {

        String str = "Java Developer";

        System.out.println(str.length());          // 14
        System.out.println(str.charAt(0));         // J
        System.out.println(str.toUpperCase());     // JAVA DEVELOPER
        System.out.println(str.toLowerCase());     // java developer
        System.out.println(str.substring(0, 4));   // Java
        System.out.println(str.contains("Java"));  // true
        System.out.println(str.startsWith("Java"));// true
        System.out.println(str.endsWith("per"));   // true
        System.out.println(str.replace("Java", "Python"));
    }
}
```

**Additional Useful String Methods**  
**matches()**
Checks whether the entire String matches a regular expression.
```java
String str = "Java123";

System.out.println(str.matches("[A-Za-z0-9]+"));
```
```bash
true
```

**repeat() – Java 11**  
Repeats a String a specified number of times.
```java
String str = "Java ";

System.out.println(str.repeat(3));
```
```bash
Java Java Java
```

**join()**  
Joins multiple Strings using a delimiter.
```java
String result = String.join("-", "Java", "Spring", "SQL");

System.out.println(result);
```
```bash
Java-Spring-SQL
```

**format()**  
Formats a String using placeholders.
```java
String name = "Rahul";
int age = 25;

String result = String.format("Name: %s, Age: %d", name, age);

System.out.println(result);
```
```bash
Name: Rahul, Age: 25
```

## 4. Important Interview Points

| Concept              | Remember                             |
| -------------------- | ------------------------------------ |
| String length        | `str.length()`                       |
| Array length         | `arr.length`                         |
| String comparison    | `equals()`                           |
| Reference comparison | `==`                                 |
| String immutable     | Cannot modify existing String object |
| StringBuilder        | Mutable, not synchronized            |
| StringBuffer         | Mutable, synchronized                |
| String Pool          | Reuses String literals               |

Interview preparation: Focus on `substring()`, `split()`, `replace()`, `equals()`, `compareTo()`, `indexOf()`, and `charAt()`. These methods are particularly useful in Java coding questions.

## String Builder  
`StringBuilder` is a predefined class in Java used to create and modify strings without creating a new object for every modification.

- It is mutable (we can change its content).
- It is not thread-safe.
- It is generally faster than `StringBuffer`.
- It was introduced in Java 5.
- It belongs to the `java.lang` package.

Syntax:
```java
StringBuilder sb = new StringBuilder("Java");
```

### Why do we use StringBuilder?  
StringBuilder modifies its existing content.

### Different ways to create StringBuilder
**Default constructor**
```java
StringBuilder sb = new StringBuilder();

System.out.println(sb);
System.out.println(sb.length());
System.out.println(sb.capacity());
```
```bash

0
16
```

**Note:** Default capacity is 16 characters.

**Constructor with initial capacity**
```java
StringBuilder sb = new StringBuilder(30);

System.out.println(sb.capacity());
```
```bash
30
```

**Constructor with String**
```java
StringBuilder sb = new StringBuilder("Java");

System.out.println(sb);
System.out.println(sb.length());
System.out.println(sb.capacity());
```
```bash
Java
4
20
```
Explanation:

- Initial String length = 4.
- Default extra capacity = 16.
- Total capacity = 20.

### Important StringBuilder methods



### StringBuilder capacity – Important interview topic  
* The default capacity of StringBuilder is 16.
* When the existing capacity is insufficient, Java increases the capacity automatically.
**Capacity formula:**  
\\[ NewCapacity = (OldCapacity \times 2) + 2 \\]

Example:
```java
StringBuilder sb = new StringBuilder();

System.out.println(sb.capacity());

sb.append("12345678901234567");

System.out.println(sb.capacity());
```
```bash
16
34
```
Explanation:
- Initial capacity = 16.
- We append 17 characters.
- Required capacity = 17.
- New capacity = (16 × 2) + 2 = 34.

This is the usual growth formula when the calculated capacity is sufficient; Java can choose a larger capacity when necessary.

###  String vs StringBuilder vs StringBuffer

| Feature                                | String                   | StringBuilder                 | StringBuffer                      |
| -------------------------------------- | ------------------------ | ----------------------------- | --------------------------------- |
| Mutability                             | Immutable                | Mutable                       | Mutable                           |
| Thread safety                          | Safe due to immutability | Not thread-safe               | Thread-safe methods               |
| Synchronization                        | Not applicable           | No                            | Yes                               |
| Performance for repeated modifications | Generally slower         | Generally faster              | Synchronization overhead          |
| Introduced                             | Java 1.0                 | Java 5                        | Java 1.0                          |
| Use case                               | Fixed text               | Single-threaded modifications | Shared synchronized modifications |


