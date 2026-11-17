# Java Basics


JDK, JRE, and JVM  
this & super keyword

## OOP concepts
There are four main pillars of OOPs:
1. Encapsulation
2. Inheritance
3. Polymorphism
4. Abstraction

### Encapsulation
Encapsulation means wrapping data (variables) and methods into a single unit (class) and restricting direct access to data.  
We achieve encapsulation using:
- Private variables.
- Public getter and setter methods.

**Real-time example:** ATM machine  
When we use an ATM:
- We cannot directly access the bank account balance.
- We can check the balance using an ATM option.
- We can deposit or withdraw money through permitted operations.
- The account balance is protected from direct modification.

```java
class BankAccount {

    private double balance = 10000;

    public double getBalance() {
        return balance;
    }

    public void deposit(double amount) {
        if (amount > 0) {
            balance = balance + amount;
        }
    }

    public void withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance = balance - amount;
        }
    }
}

public class Main {
    public static void main(String[] args) {

        BankAccount account = new BankAccount();

        account.deposit(5000);
        account.withdraw(2000);

        System.out.println(account.getBalance());
    }
}
```
```bash
13000.0
```
Interview point: Encapsulation is mainly used for data hiding and data protection.

### Inheritance
Inheritance means one class can acquire the properties and methods of another class.  
We use the `extends` keyword for class inheritance.

**Real-time example:** Employee Management System  
Imagine an organization has different types of employees:
- Developer
- Manager
- Tester

All employees have common properties:
- Employee ID
- Employee name
- Salary

Instead of writing the same code in every class, we create a common `Employee` parent class.
```java
class Employee {

    int empId;
    String name;

    void displayDetails() {
        System.out.println(empId);
        System.out.println(name);
    }
}

class Developer extends Employee {

    void writeCode() {
        System.out.println("Developer writes Java code");
    }
}

class Manager extends Employee {

    void manageTeam() {
        System.out.println("Manager manages the team");
    }
}

public class Main {
    public static void main(String[] args) {

        Developer dev = new Developer();

        dev.empId = 101;
        dev.name = "Rahul";

        dev.displayDetails();
        dev.writeCode();

        Manager manager = new Manager();

        manager.empId = 102;
        manager.name = "Priya";

        manager.displayDetails();
        manager.manageTeam();
    }
}
```
```bash
101
Rahul
Developer writes Java code
102
Priya
Manager manages the team
```

Explanation:
- `Employee` is the parent class.
- `Developer` and `Manager` are child classes.
- Both child classes reuse the properties and methods of Employee.
- We avoid duplicate code.
Interview point: Inheritance promotes code reusability.

**Types of inheritance in Java**
1. Single inheritance – One parent and one child.
2. Multilevel inheritance – A class inherits from another child class.
3. Hierarchical inheritance – Multiple child classes inherit from one parent.
4. Multiple inheritance – Not supported through classes in Java, but possible through interfaces.
5. Hybrid inheritance – Can be achieved using interfaces.

### Polymorphism  
Polymorphism means one name having multiple forms.  
In Java, polymorphism is mainly divided into two types:  

**A. Compile-time polymorphism (Method Overloading)**  
**Real-time example:** Payment System  
In an application, we can make payments using different methods:
- UPI
- Credit card
- Debit card

We can use the same method name `makePayment()` with different parameters.
```java
class Payment {

    void makePayment(String upiId) {
        System.out.println("Payment through UPI: " + upiId);
    }

    void makePayment(long cardNumber) {
        System.out.println("Payment through Card: " + cardNumber);
    }

    void makePayment(String upiId, double amount) {
        System.out.println("UPI Payment amount: " + amount);
    }
}

public class Main {
    public static void main(String[] args) {

        Payment payment = new Payment();

        payment.makePayment("rahul@upi");
        payment.makePayment(1234567890123456L);
        payment.makePayment("rahul@upi", 5000);
    }
}
```
```bash
Payment through UPI: rahul@upi
Payment through Card: 1234567890123456
UPI Payment amount: 5000.0
```

Explanation:
- Same method name: `makePayment()`.
- Different parameters.
- The compiler identifies which method to call based on the arguments.

Interview point: Method overloading is compile-time polymorphism.

**B. Runtime polymorphism (Method Overriding)**  
**Real-time example:** Notification System  
An application sends notifications through different channels:  
- Email
- SMS
- WhatsApp

All notification classes have the same method `sendNotification()`, but each class provides its own implementation.
```java
class Notification {

    void sendNotification() {
        System.out.println("Sending notification");
    }
}

class Email extends Notification {

    @Override
    void sendNotification() {
        System.out.println("Sending Email");
    }
}

class SMS extends Notification {

    @Override
    void sendNotification() {
        System.out.println("Sending SMS");
    }
}

public class Main {

    public static void main(String[] args) {

        Notification notification;

        notification = new Email();
        notification.sendNotification();

        notification = new SMS();
        notification.sendNotification();
    }
}
```
```bash
Sending Email
Sending SMS
```

Explanation:
- `Notification` is the parent class.
- `Email` and `SMS` override the parent method.
- Parent reference holds child objects.
- JVM decides which overridden method to execute at runtime based on the actual object.

Interview point: Method overriding is runtime polymorphism.

### Abstraction  
Abstraction means hiding implementation details and showing only essential functionality to the user.  
We achieve abstraction using:  
1. Abstract classes.
2. Interfaces.

**Real-time example:** Online Banking Application
When we transfer money:  
- We enter the amount.
- We select the beneficiary.
- We click the transfer button.

We don't need to know the internal implementation of how the bank processes the transaction.

**Example using Abstract Class:**
```java
abstract class Bank {

    abstract void transferMoney();

    void login() {
        System.out.println("User logged in");
    }
}

class SBI extends Bank {

    @Override
    void transferMoney() {
        System.out.println("Money transferred through SBI");
    }
}

class HDFC extends Bank {

    @Override
    void transferMoney() {
        System.out.println("Money transferred through HDFC");
    }
}

public class Main {

    public static void main(String[] args) {

        Bank bank = new SBI();

        bank.login();
        bank.transferMoney();
    }
}
```
```bash
User logged in
Money transferred through SBI
```

Explanation:

- `Bank` is an abstract class.
- `transferMoney()` is an abstract method without implementation.
- SBI and HDFC provide their own implementations.
- The user interacts with the common functionality without needing to know its internal implementation.

Interview point: Abstraction hides implementation details and exposes essential functionality.

## Arrays  
Arrays are used to store multiple values in a single variable, instead of declaring separate variables for each value.

### Types of Arrays in Java
Java supports three common array structures:

1. One-dimensional array
2. Two-dimensional array
3. Multidimensional array

### One-Dimensional Array  
An array that stores elements in a single row.  
Declaration:
```java
int[] numbers = new int[5];
```

Initialization:
```java
int[] numbers = {10, 20, 30, 40, 50};
```

Accessing elements:
```java
public class Main {
    public static void main(String[] args) {

        int[] numbers = {10, 20, 30, 40, 50};

        System.out.println(numbers[0]);
        System.out.println(numbers[2]);
        System.out.println(numbers[4]);
    }
}
```
```bash
10
30
50
```
Remember:  
- Array indexing starts from `0`.
- Last index = `array.length - 1`.
- Array size is fixed once created.

### Array Methods
Java provides a predefined utility class called `Arrays` inside the `java.util` package.  
It contains several static methods to perform operations such as sorting, searching, comparing, copying, and filling arrays.  
```java
import java.util.Arrays;
```

**Important Arrays Class Methods**

| Method                  | Purpose                               |
| ----------------------- | ------------------------------------- |
| `Arrays.toString()`     | Converts array into readable String   |
| `Arrays.sort()`         | Sorts array in ascending order        |
| `Arrays.equals()`       | Compares two arrays                   |
| `Arrays.copyOf()`       | Copies an array                       |
| `Arrays.fill()`         | Fills array with a specific value     |
| `Arrays.binarySearch()` | Searches an element in a sorted array |
| `Arrays.stream()`       | Converts array into Stream            |
| `Arrays.deepToString()` | Prints multidimensional arrays        |
| `Arrays.deepEquals()`   | Compares multidimensional arrays      |
| `Arrays.copyOfRange()`  | Copies a specific range of elements   |
| `Arrays.compare()`      | Compares two arrays lexicographically |
| `Arrays.mismatch()`     | Finds the first mismatching index     |
| `Arrays.asList()`       | converts an array into a List.        |
| `Arrays.parallelSort()` | to sort array elements in ascending order using parallel processing.|

Note: **arr.length** is a property used to find the length of the Array

### Examples of Important Array Methods

**1. Arrays.toString()**
Converts an array into a readable String representation.
```java
import java.util.Arrays;

int[] arr = {10, 20, 30, 40};

System.out.println(Arrays.toString(arr));
```
```bash
[10, 20, 30, 40]
```

**2. Arrays.sort()**  
Sorts array elements in ascending order.
```java
int[] arr = {50, 10, 40, 20, 30};

Arrays.sort(arr);

System.out.println(Arrays.toString(arr));
```
```bash
[10, 20, 30, 40, 50]
```

**3. Arrays.equals()**  
Checks whether two arrays contain the same elements in the same order.
```java
int[] arr1 = {10, 20, 30};
int[] arr2 = {10, 20, 30};

System.out.println(Arrays.equals(arr1, arr2));
```
```bash
true
```

**4. Arrays.copyOf()**  
Creates a new array by copying the original array.
```java
int[] arr = {10, 20, 30};

int[] newArr = Arrays.copyOf(arr, 5);

System.out.println(Arrays.toString(newArr));
```
```bash
[10, 20, 30, 0, 0]
```

**5. Arrays.fill()**  
Fills all array elements with the specified value.
```java
int[] arr = new int[5];

Arrays.fill(arr, 100);

System.out.println(Arrays.toString(arr));
```
```bash
[100, 100, 100, 100, 100]
```

**6. Arrays.binarySearch()**  
Searches for an element in a sorted array.
```java
int[] arr = {10, 20, 30, 40, 50};

int result = Arrays.binarySearch(arr, 30);

System.out.println(result);
```
```bash
2
```
Remember: Binary search should be performed on a sorted array to get reliable results.

**7. Arrays.stream()**  
Converts an array into a Stream so that we can perform operations using Java 8 Stream API.
```java
int[] arr = {10, 20, 30, 40, 50};

Arrays.stream(arr)
      .filter(n -> n > 20)
      .forEach(System.out::println);
```
```bash
30
40
50
```

**8. Arrays.copyOfRange()**  
Copies elements from a specified start index to an end index (exclusive).
```java
int[] arr = {10, 20, 30, 40, 50};

int[] newArr = Arrays.copyOfRange(arr, 1, 4);

System.out.println(Arrays.toString(newArr));
```
```bash
[20, 30, 40]
```

**9. Arrays.deepToString()**  
Used to print multidimensional arrays.
```java
int[][] arr = {
    {10, 20},
    {30, 40}
};

System.out.println(Arrays.deepToString(arr));
```
```java
[[10, 20], [30, 40]]
```

**10. Arrays.deepEquals()**  
Compares the contents of two multidimensional arrays.
```java
int[][] arr1 = {{10, 20}, {30, 40}};
int[][] arr2 = {{10, 20}, {30, 40}};

System.out.println(Arrays.deepEquals(arr1, arr2));
```
```bash
true
```
## Abstract class  
An abstract class in Java is a class declared using the `abstract` keyword. It is used to achieve abstraction and provides a common base for other classes.  
An abstract class can contain:  
1. Abstract methods and Concrete methods
2. Constructors.
3. Instance variables and static variables.
4. Static and final methods.

### Why do we use Abstract Classes?  
We use abstract classes when multiple child classes share common properties and behaviours, but some behaviours need to be implemented differently by each child class.

**Real-time example:**
Consider an Animal. Every animal makes a sound, but different animals make different sounds.

- Dog → Barks
- Cat → Meows
- Cow → Moos

We can define a common abstract class called `Animal`.

**Example of Abstract Class**
```java
abstract class Animal {

    // Abstract method
    abstract void sound();

    // Concrete method
    void eat() {
        System.out.println("Animal is eating");
    }
}

class Dog extends Animal {

    @Override
    void sound() {
        System.out.println("Dog barks");
    }
}

class Cat extends Animal {

    @Override
    void sound() {
        System.out.println("Cat meows");
    }
}

public class Main {
    public static void main(String[] args) {

        Animal a1 = new Dog();
        a1.sound();
        a1.eat();

        Animal a2 = new Cat();
        a2.sound();
        a2.eat();
    }
}
```
```bash
Dog barks
Animal is eating
Cat meows
Animal is eating
```

**Understanding the code**  
- `abstract class Animal`: We cannot directly create an object of this class.
- `abstract void sound()`: Method has no implementation.
- `void eat()`: Concrete method with implementation.
- `class Dog extends Animal`: Dog inherits the Animal class.
- Dog and Cat must implement the inherited abstract method `sound()`.

**Important Rules of Abstract Class**

| Rule              | Explanation                                                                      |
| ----------------- | -------------------------------------------------------------------------------- |
| Object creation   | Cannot create an object directly                                                 |
| Constructor       | Can have constructors                                                            |
| Abstract methods  | Can have abstract methods                                                        |
| Concrete methods  | Can have normal methods                                                          |
| Variables         | Can have instance, static and final variables                                    |
| Inheritance       | Can extend another class                                                         |
| Interface         | Can implement interfaces                                                         |
| Method overriding | Child class must implement inherited abstract methods unless it is also abstract |

**Can Abstract Class Have a Constructor?**  
Yes. An abstract class can have a constructor.  
The constructor executes when a child-class object is created.
```java
abstract class Animal {

    Animal() {
        System.out.println("Animal constructor");
    }

    abstract void sound();
}

class Dog extends Animal {

    Dog() {
        System.out.println("Dog constructor");
    }

    void sound() {
        System.out.println("Dog barks");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog d = new Dog();
        d.sound();
    }
}
```
```bash
Animal constructor
Dog constructor
Dog barks
```
Why? When we create a Dog object, the parent class constructor executes first, followed by the child class constructor.

**Can We Create an Abstract Class Reference?**  
Yes! We cannot create an abstract class object, but we can create its reference.
```java
abstract class Animal {

    abstract void sound();
}

class Dog extends Animal {

    void sound() {
        System.out.println("Dog barks");
    }
}

public class Main {
    public static void main(String[] args) {

        Animal a = new Dog();

        a.sound();
    }
}
```
```java
Dog barks
```
Interview point:

- `Animal a = new Animal();` → Not allowed.
- `Animal a = new Dog();` → Allowed.

This is an example of runtime polymorphism.

**Abstract Class vs Concrete Class**

| Abstract Class                    | Concrete Class                  |
| --------------------------------- | ------------------------------- |
| Declared using `abstract` keyword | Normal class                    |
| Cannot instantiate directly       | Can instantiate                 |
| Can contain abstract methods      | Cannot contain abstract methods |
| Can contain concrete methods      | Contains implemented methods    |
| Can have constructors             | Can have constructors           |


## Interface
It is used to achieve abstraction and supports multiple inheritance of type.  
An interface defines a contract that implementing classes must follow.  
We declare an interface using the `interface` keyword.

### Why do we use Interfaces?  
We use interfaces when different classes need to follow the same behaviour but can have different implementations.  
**Real-time example:** Payment System  
Consider different payment methods:  
- Google Pay
- PhonePe
- Credit Card

All payment methods perform payment, but their implementations are different.  
We can define a common interface called `Payment`.

**Basic Interface Example**
```java
interface Payment {

    void pay();
}

class GooglePay implements Payment {

    @Override
    public void pay() {
        System.out.println("Payment using Google Pay");
    }
}

class PhonePe implements Payment {

    @Override
    public void pay() {
        System.out.println("Payment using PhonePe");
    }
}

public class Main {

    public static void main(String[] args) {

        Payment p1 = new GooglePay();
        p1.pay();

        Payment p2 = new PhonePe();
        p2.pay();
    }
}
```
```bash
Payment using Google Pay
Payment using PhonePe
```

### Important Rules of Interfaces

| Rule             | Explanation                                |
| ---------------- | ------------------------------------------ |
| Object creation  | Cannot create an interface object directly |
| Variables        | By default `public static final`           |
| Abstract methods | By default `public abstract`               |
| Constructor      | Cannot have constructors                   |
| Inheritance      | Interface can extend multiple interfaces   |
| Implementation   | A class can implement multiple interfaces  |
| Default methods  | Supported from Java 8                      |
| Static methods   | Supported from Java 8                      |
| Private methods  | Supported from Java 9                      |

Variables declared inside an interface are automatically:
- `public`
- `static`
- `final`

Interview point: We cannot modify interface variables because they are final.

### Types of Methods in Interface  
Java interfaces support different types of methods.

**1. Abstract Method**  
A method without a body.
```java
interface Animal {
    void sound();
}
```
The implementing class must provide the implementation unless it is abstract.

**2. Default Method (Java 8)**  
A method with a body declared using the `default` keyword.
```java
interface Animal {

    default void eat() {
        System.out.println("Animal is eating");
    }
}

class Dog implements Animal {
}

public class Main {
    public static void main(String[] args) {

        Dog d = new Dog();
        d.eat();
    }
}
```
```java
Animal is eating
```

**Why do we use default methods?**  
To add new methods to existing interfaces without forcing every existing implementing class to implement them.

**3. Static Method (Java 8)**  
Static methods belong to the interface itself.
```java
interface Animal {

    static void info() {
        System.out.println("Animals have different sounds");
    }
}

public class Main {
    public static void main(String[] args) {

        Animal.info();
    }
}
```
```bash
Animals have different sounds
``` 
**Note:** To provide utility methods related to the interface without requiring an implementing class object.
Remember: Call static interface methods using the interface name.

**4. Private Method (Java 9)**  
Private methods are used to share common implementation inside an interface.
```java
interface Animal {

    private void display() {
        System.out.println("Animal information");
    }

    default void info() {
        display();
    }
}

class Dog implements Animal {
}

public class Main {
    public static void main(String[] args) {

        Dog d = new Dog();
        d.info();
    }
}
```
```bash
Animal information
```
Remember: Private interface methods cannot be accessed directly by implementing classes.

### Multiple Inheritance Using Interfaces
Java does not support multiple inheritance through classes, but it supports implementing multiple interfaces.
Example:
```java
interface Animal {
    void eat();
}

interface Pet {
    void play();
}

class Dog implements Animal, Pet {

    public void eat() {
        System.out.println("Dog is eating");
    }

    public void play() {
        System.out.println("Dog is playing");
    }
}

public class Main {

    public static void main(String[] args) {

        Dog d = new Dog();

        d.eat();
        d.play();
    }
}
```
```bash
Dog is eating
Dog is playing
```
Here, Dog implements two interfaces: Animal and Pet.


### Abstract Class vs interface
**When would you choose an abstract class instead interface?**  
If the classes have common state and common implementation, an abstract class may be more appropriate.

**When should we use an interface?**  
I would use an interface when I want to define a contract and allow multiple classes to provide different implementations. It helps achieve loose coupling, flexibility, and makes the code easier to test and maintain.

**Important interview comparison:**

| Abstract Class                         | Interface                                              |
| -------------------------------------- | ------------------------------------------------------ |
| Declared using `abstract class`        | Declared using `interface`                             |
| Can have constructors                  | Cannot have constructors                               |
| Can have instance variables            | Variables are `public static final` by default         |
| Can have abstract and concrete methods | Can have abstract, default, static and private methods |
| Supports single class inheritance      | Supports multiple interface implementation             |
| Can have different access modifiers    | Abstract methods are public by default                 |
| Extended using `extends`               | Implemented using `implements`                         |


### Important Interview Scenario: Same Method in Two Interfaces
**What happens when two interfaces contain the same default method?**
```java
interface A {

    default void display() {
        System.out.println("Interface A");
    }
}

interface B {

    default void display() {
        System.out.println("Interface B");
    }
}

class Test implements A, B {

    @Override
    public void display() {
        System.out.println("Test class");
    }
}

public class Main {

    public static void main(String[] args) {

        Test t = new Test();
        t.display();
    }
}
```
```bash
Test class
```
Why? The implementing class must override the conflicting default method and provide its own implementation (or explicitly choose one using `A.super.display()` or `B.super.display()`).

My suggestion: For your Java Developer interviews, focus especially on interface vs abstract class, multiple inheritance, default methods, static methods, and functional interfaces. These are commonly tested through coding questions.

