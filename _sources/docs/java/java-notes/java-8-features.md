# Java 8 Features
  
## 1. Lambda Expression

A **Lambda Expression** is a feature introduced in Java 8 that allows us to write concise and readable code by implementing the method of a Functional Interface without creating a separate class. <br>

In simple words, a Lambda Expression is a shorter way of writing an implementation of a Functional Interface.

**Syntax:**
```java
(parameters) -> {
    // method implementation
}
```


## 2. Functional Interfaces
A **Functional Interface** is an interface that contains exactly one **abstract method**. <br>

In simple words, a Functional Interface is an interface that has only one abstract method, and we can implement that method using a Lambda Expression.

### Basic example of Functional Interface

```java
@FunctionalInterface
interface Addition {

    int add(int a, int b);

}
```

Implementation using Lambda Expression:

```java
public class Main {
    public static void main(String[] args) {

        Addition obj = (a, b) -> a + b;

        System.out.println(obj.add(10, 20));
    }
}
```
Output:
```
30
```

### Rules of Functional Interface

1. It must contain exactly one abstract method.
2. It can contain multiple default and static methods.
3. It can override methods from the Object class, such as `toString()` and `equals()`.
4. `@FunctionalInterface` annotation is optional, but recommended.
5. It supports Lambda Expressions and method references.

Example:
```java
@FunctionalInterface
interface Employee {

    void display();  // Abstract method

    default void show() {
        System.out.println("Default method");
    }

    static void details() {
        System.out.println("Static method");
    }
}
```

### Types of Built-in Functional Interfaces

Java 8 provides four important built-in Functional Interfaces.

| Interface | Purpose | Method |
|---|---|---|
| Predicate | Checks a condition | `test()` |
| Function | Converts input into output | `apply()` |
| Consumer | Consumes input | `accept()` |
| Supplier | Supplies a value | `get()` |


### Other commonly used Functional Interfaces
|Interface	|Abstract method	|Purpose
|---|---|---|
|Runnable	|run()	|Multithreading
|Callable	|call()	|Returns a result from a thread task
|Comparator	|compare()	|Comparing and sorting
|ActionListener	|actionPerformed()	|Handling events



## 3. Stream API
**Stream API** is a feature introduced in Java 8 that is used to process collections of data in a functional programming style.  
It allows us to perform operations such as filtering, sorting, mapping, and collecting data with less code.  

### Why do we use Stream API?
Before Java 8, we used loops and conditions to process collections.  
Before Java 8:
```java
List<Integer> numbers = Arrays.asList(10, 20, 30, 40, 50);

for (Integer n : numbers) {
    if (n > 20) {
        System.out.println(n);
    }
}
```
output
```
30
40
50
```

Using Stream API (Java 8):

```java
List<Integer> numbers = Arrays.asList(10, 20, 30, 40, 50);

numbers.stream()
       .filter(n -> n > 20)
       .forEach(System.out::println);
```
Output:
```
30
40
50
```

### Types of Stream Operations
There are two main types of operations.

**A. Intermediate Operations**  
Intermediate operations transform or filter stream elements and return another Stream.  
They are lazy, meaning they execute only when a terminal operation is called.

| Method       | Purpose                                 |
| ------------ | --------------------------------------- |
| `filter()`   | Filters elements based on condition     |
| `map()`      | Transforms elements                     |
| `sorted()`   | Sorts elements                          |
| `distinct()` | Removes duplicates                      |
| `limit()`    | Limits the number of elements           |
| `skip()`     | Skips elements                          |
| `flatMap()`  | Converts nested streams into one stream |

Example 1: filter()
Find numbers greater than 20.
```java
List<Integer> list =
    Arrays.asList(10, 20, 30, 40, 50);

list.stream()
    .filter(n -> n > 20)
    .forEach(System.out::println);
```
Output:
```
30
40
50
```

Example 2: map()
Multiply every number by 2.
```java
List<Integer> list =
    Arrays.asList(1, 2, 3, 4, 5);

list.stream()
    .map(n -> n * 2)
    .forEach(System.out::println);
```
Output:
```
2
4
6
8
10
```

Example 3: distinct()
Remove duplicate elements.
```java
List<Integer> list =
    Arrays.asList(10, 20, 10, 30, 20);

list.stream()
    .distinct()
    .forEach(System.out::println);
```
Output:
```
10
20
30
```

Example 4: sorted()
```java
List<Integer> list =
    Arrays.asList(50, 10, 40, 20, 30);

list.stream()
    .sorted()
    .forEach(System.out::println);
```
Output:
```
10
20
30
40
50
```

**B. Terminal Operations**  
Terminal operations produce a result or perform an action. They trigger stream processing.

| Method        | Purpose                                               |
| ------------- | ----------------------------------------------------- |
| `forEach()`   | Iterates elements                                     |
| `collect()`   | Collects elements into a collection or another result |
| `count()`     | Counts elements                                       |
| `reduce()`    | Combines elements into one result                     |
| `min()`       | Finds minimum                                         |
| `max()`       | Finds maximum                                         |
| `anyMatch()`  | Checks whether any element matches                    |
| `allMatch()`  | Checks whether all elements match                     |
| `noneMatch()` | Checks whether no elements match                      |
| `findFirst()` | Returns first element                                 |
| `findAny()`   | Returns any element                                   |

Example 1: count()  
```java
List<Integer> list =
    Arrays.asList(10, 20, 30, 40, 50);

long count = list.stream().count();

System.out.println(count);
```
Output:
```
5
```

Example 2: collect()  
```java
List<Integer> list =
    Arrays.asList(10, 20, 30, 40, 50);

List<Integer> result = list.stream()
        .filter(n -> n > 20)
        .collect(Collectors.toList());

System.out.println(result);
```
Output:
```
[30, 40, 50]
```

Example 3: reduce()  
Used to combine all elements into a single result.
```java
List<Integer> list =
    Arrays.asList(10, 20, 30, 40);

int sum = list.stream()
        .reduce(0, (a, b) -> a + b);

System.out.println(sum);
```
Output:
```
100
```
Explanation:  
- `0` is the initial value.
- `a` represents the accumulated result.
- `b` represents the current element.
- `a + b` combines the values.

**Important difference between map() and filter()**  
This is a frequently asked interview question.

| map()                                       | filter()                        |
| ------------------------------------------- | ------------------------------- |
| Used to transform data                      | Used to filter data             |
| Takes a Function                            | Takes a Predicate               |
| Returns transformed elements                | Returns matching elements       |
| Number of elements usually remains the same | Number of elements may decrease |

Example:
```java
List<Integer> list =
    Arrays.asList(10, 20, 30, 40);

list.stream()
    .filter(n -> n > 20)
    .map(n -> n * 2)
    .forEach(System.out::println);
```
Output:
```
60
80
```
Here, first `filter()` selects numbers greater than 20, and then `map()` multiplies them by 2.

### Real-time Employee Examples  
Suppose we have an Employee class.
```java
class Employee {

    private int id;
    private String name;
    private double salary;

    public Employee(int id, String name, double salary) {
        this.id = id;
        this.name = name;
        this.salary = salary;
    }

    public int getId() {
        return id;
    }

    public String getName() {
        return name;
    }

    public double getSalary() {
        return salary;
    }
}
```

Create employee records:

```java
List<Employee> employees = Arrays.asList(
    new Employee(1, "Rahul", 30000),
    new Employee(2, "Priya", 45000),
    new Employee(3, "Amit", 25000),
    new Employee(4, "Sneha", 60000)
);
```

**Question 1:** Find employees whose salary is greater than 30,000.
```java
employees.stream()
    .filter(e -> e.getSalary() > 30000)
    .forEach(e -> System.out.println(e.getName()));
```
```bash
Priya
Sneha
```

**Question 2:** Get only employee names.
```java
List<String> names = employees.stream()
    .map(Employee::getName)
    .collect(Collectors.toList());

System.out.println(names);
```
```bash 
[Rahul, Priya, Amit, Sneha]
```

**Question 3:** Find the highest salary.

```java
double maxSalary = employees.stream()
    .mapToDouble(Employee::getSalary)
    .max()
    .orElse(0);

System.out.println(maxSalary);
```
```bash
60000.0
```

**Question 4:** Sort employees by salary.
```java
employees.stream()
    .sorted(Comparator.comparingDouble(Employee::getSalary))
    .forEach(e ->
        System.out.println(e.getName() + " " + e.getSalary()));
```
```bash
Amit 25000.0
Rahul 30000.0
Priya 45000.0
Sneha 60000.0
```


## 4. Optional class  
Optional is a class introduced in Java 8 in the `java.util` package. It is used to handle situations where a value may or may not be present.  
In simple words, Optional helps avoid NullPointerException by representing a value that might be null or absent.

### Why do we use Optional?  
Before Java 8, we used null checks to avoid NullPointerException.  
Before Java 8:  
```java
public class Main {
    public static void main(String[] args) {

        String name = null;

        if (name != null) {
            System.out.println(name.length());
        } else {
            System.out.println("Name is not available");
        }
    }
}
```
```bash
Name is not available
```

Using Optional (Java 8):
```java
import java.util.Optional;

public class Main {
    public static void main(String[] args) {

        Optional<String> name = Optional.ofNullable(null);

        System.out.println(name.orElse("Name is not available"));
    }
}
```
```bash
Name is not available
```
Here, Optional handles the absence of a value without requiring an explicit null check.

### Three ways to create Optional objects  

Java 8 provides three important methods. 

**1\. Optional.of()**  
Used when the value is definitely not null.
```java
Optional<String> name = Optional.of("Java");

System.out.println(name.get());
```
```bash
Java
```  
Note: If we pass null to `Optional.of()`, it throws NullPointerException.

**2\. Optional.ofNullable()**  
Used when the value may be null or non-null.
```java
String name = null;

Optional<String> result = Optional.ofNullable(name);

System.out.println(result);
```
```bash
Optional.empty
```

**3\. Optional.empty()**  
Used to create an empty Optional.
```java
Optional<String> name = Optional.empty();

System.out.println(name.isPresent());
```
```bash
false
```

### Important Optional methods

| Method          | Purpose                                          |
| --------------- | ------------------------------------------------ |
| `of()`          | Creates Optional with a non-null value           |
| `ofNullable()`  | Creates Optional with nullable value             |
| `empty()`       | Creates empty Optional                           |
| `get()`         | Returns the value if present                     |
| `isPresent()`   | Checks whether value exists                      |
| `isEmpty()`     | Checks whether value is absent (Java 11+)        |
| `orElse()`      | Returns default value if empty                   |
| `orElseGet()`   | Uses Supplier to generate default value if empty |
| `orElseThrow()` | Throws exception if empty                        |
| `ifPresent()`   | Executes action if value exists                  |
| `filter()`      | Filters the value based on condition             |
| `map()`         | Transforms the value                             |

### Examples of important methods

**Example 1: isPresent()**
```java
Optional<String> name = Optional.of("Java");

if (name.isPresent()) {
    System.out.println(name.get());
}
```
```bash
Java
```

**Example 2: orElse()**  
Returns the actual value if present; otherwise returns the default value.
```java
Optional<String> name = Optional.ofNullable(null);

System.out.println(name.orElse("Default Name"));
```
```bash
Default Name
```

**Example 3: orElseGet()**  
Uses a Supplier to generate a default value when Optional is empty.
```java
Optional<String> name = Optional.empty();

System.out.println(
    name.orElseGet(() -> "Java Developer")
);
```
```bash
Java Developer
```

**Example 4: orElseThrow()**  
Throws an exception if the value is absent.
```java
Optional<String> name = Optional.empty();

String result = name.orElseThrow(
    () -> new RuntimeException("Name not found")
);
```

**Example 5: ifPresent()**  
Executes the given operation only if the value is available.
```java
Optional<String> name = Optional.of("Java");

name.ifPresent(n -> System.out.println(n));
```bash
Java
```

### Difference between orElse() and orElseGet()

This is a frequently asked interview question.

| orElse()                                | orElseGet()                                   |
| --------------------------------------- | --------------------------------------------- |
| Takes a default value                   | Takes a Supplier                              |
| Default expression is evaluated eagerly | Supplier executes only when Optional is empty |
| Can perform unnecessary work            | Avoids unnecessary default-value generation   |


### Real-time example – Employee Management  
Suppose we want to find an employee by ID.

```java
public Optional<Employee> findEmployeeById(int id) {

    Employee employee = employeeRepository.findById(id);

    return Optional.ofNullable(employee);
}
```
Usage:
```java
Optional<Employee> employee = findEmployeeById(101);

employee.ifPresent(e ->
    System.out.println(e.getName())
);
```

In Spring Data JPA, the repository's `findById()` method already returns `Optional<Employee>`:

```java
Optional<Employee> employee =
        employeeRepository.findById(101);

Employee result = employee.orElseThrow(
    () -> new RuntimeException("Employee not found")
);
```

## 4. Default & Static methods in interfaces
### Default methods:
A Default Method is a method inside an interface that has a method body and uses the default keyword.  
The main purpose was to add new methods to existing interfaces without breaking existing implementing classes.    
**Example:** 
```java 
interface Animal {

    void eat();

    default void sound() {
        System.out.println("Animal makes sound");
    }
}

class Dog implements Animal {

    @Override
    public void eat() {
        System.out.println("Dog is eating");
    }
}

public class Main {
    public static void main(String[] args) {

        Dog d = new Dog();

        d.eat();
        d.sound();
    }
}
```
```bash
Dog is eating
Animal makes sound
```
### Why do we use Default Methods?  
Suppose we already have an interface with 100 implementing classes.  
If we add a new abstract method, all 100 classes must implement it.  
Instead, if we add a default method, existing classes can continue working without changes.  
This provides backward compatibility.

### Static Method:  
A Static Method is a method inside an interface that uses the static keyword and contains a method implementation.  
**Example:**
```java
interface Animal {

    static void details() {
        System.out.println("Animal details");
    }
}

public class Main {
    public static void main(String[] args) {

        Animal.details();
    }
}
```
```bash
Animal details
```
Important points:
1. Static methods belong to the interface itself.
2. We call them using the interface name.
3. They are not inherited by implementing classes.
4. They cannot be overridden by implementing classes.
5. They have a method body.

## 5. CompletableFuture  
CompletableFuture is a class introduced in Java 8 that is used to perform asynchronous and non-blocking operations.  
It allows us to execute tasks in the background without blocking the main thread and process the result when the task is completed.  

**Example:** Running two tasks concurrently  
Suppose you need to fetch employee details and department details independently.

```java
CompletableFuture<String> employee =
    CompletableFuture.supplyAsync(() -> "Employee: Rahul");

CompletableFuture<String> department =
    CompletableFuture.supplyAsync(() -> "Department: IT");

CompletableFuture<String> result =
    employee.thenCombine(department,
        (emp, dept) -> emp + "\n" + dept);

System.out.println(result.join());
```
```bash
Employee: Rahul
Department: IT
```

### Why do we use CompletableFuture?  
Imagine your application needs to call two different APIs:  
- API 1: Get employee details.
- API 2: Get employee salary.

If you call them one after another, the second API waits until the first API finishes.

Using `CompletableFuture`, both API calls can execute independently.

**Basic example**
```java
import java.util.concurrent.CompletableFuture;

public class Main {
    public static void main(String[] args) {

        CompletableFuture<Void> future =
            CompletableFuture.runAsync(() -> {
                System.out.println("Task running in background");
            });

        future.join();

        System.out.println("Main thread completed");
    }
}
```
```bash
Task running in background
Main thread completed
```

`runAsync()` executes a task asynchronously when you don't need a return value.
`join()` waits until the asynchronous task completes.

### Important CompletableFuture methods

| Method            | Purpose                                    |
| ----------------- | ------------------------------------------ |
| `runAsync()`      | Executes a task without returning a result |
| `supplyAsync()`   | Executes a task and returns a result       |
| `thenApply()`     | Transforms the result                      |
| `thenAccept()`    | Consumes the result; returns no result     |
| `thenRun()`       | Executes another task after completion     |
| `thenCombine()`   | Combines results from two futures          |
| `allOf()`         | Waits for all futures to complete          |
| `anyOf()`         | Completes when any one future completes    |
| `exceptionally()` | Handles exceptions                         |
| `join()`          | Waits and returns the result               |

**thenApply()**  
It takes the result from one task and transforms it.  
```java
CompletableFuture<String> future =
    CompletableFuture.supplyAsync(() -> "java")
        .thenApply(name -> name.toUpperCase());

System.out.println(future.join());
```
```bash
JAVA
```

**thenCombine()**  
Suppose we want to fetch employee name and salary independently and combine the results.
```java
CompletableFuture<String> nameFuture =
    CompletableFuture.supplyAsync(() -> "John");

CompletableFuture<Integer> salaryFuture =
    CompletableFuture.supplyAsync(() -> 50000);

CompletableFuture<String> result =
    nameFuture.thenCombine(salaryFuture,
        (name, salary) -> name + " " + salary);

System.out.println(result.join());
```
```bash
John 50000
```

**Exception handling**  
We can handle exceptions using `exceptionally()`.
```java
CompletableFuture<String> future =
    CompletableFuture.supplyAsync(() -> {
        if (true) {
            throw new RuntimeException("Something went wrong");
        }
        return "Success";
    }).exceptionally(ex -> "Error: " + ex.getMessage());

System.out.println(future.join());
```
```bash
Error: java.lang.RuntimeException: Something went wrong
```

## 8. CompletableFuture vs Future

| Future                               | CompletableFuture                           |
| ------------------------------------ | ------------------------------------------- |
| Introduced in Java 5                 | Introduced in Java 8                        |
| Supports asynchronous execution      | Supports asynchronous execution             |
| Does not provide convenient chaining | Supports chaining using `thenApply()`, etc. |
| Limited exception handling           | Provides exception-handling methods         |
| No built-in way to combine futures   | Supports `thenCombine()`, `allOf()`, etc.   |


## 6. Method References  
– System.out::println 

## 7. New Date/Time API  
– LocalDate, LocalDateTime, ZonedDateTime. 
  


