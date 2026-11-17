Since your background is mainly **Java + Spring Boot + Microservices**, I’ve marked the **⭐ high-priority questions** you should definitely prepare.

## Java — High Priority ⭐

### 1. What are the main features of Java 8?
### 2. Why Default & Static methods in interfaces?
**Default methods:** Add new methods to an existing interface without forcing every implementing class to implement them. <br>
**Static methods:** to provide utility methods related to the interface without requiring an implementing class object.

### 3. What is a lambda expression?
A lambda expression in Java is a short way to implement the abstract method of a functional interface without writing a separate class or method implementation.

### 4. What is the difference between JDK, JRE, and JVM?
### 5. Explain OOP concepts with real-time examples.

**1. Encapsulation**

Real-time example: Bank Account
A bank account balance should not be directly accessible or modified by anyone. We keep variables private and provide public methods to access or update them.

```java
class BankAccount {

    private double balance;

    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
        }
    }

    public double getBalance() {
        return balance;
    }
}

public class Main {
    public static void main(String[] args) {

        BankAccount account = new BankAccount();

        account.deposit(5000);

        System.out.println(account.getBalance());
    }
}
```

Output:
```
5000.0
```

**2. Inheritance**

Real-time example: Employee Management System
Suppose we have different types of employees: Developer and Manager. Both share common employee properties.
Instead of writing the same code in every class, we create a parent class.

```java
class Employee {

    int id;
    String name;

    void display() {
        System.out.println(id + " " + name);
    }
}

class Developer extends Employee {

    void writeCode() {
        System.out.println("Developer writes Java code");
    }
}

class Manager extends Employee {

    void conductMeeting() {
        System.out.println("Manager conducts meetings");
    }
}

public class Main {
    public static void main(String[] args) {

        Developer d = new Developer();
        d.id = 101;
        d.name = "John";

        d.display();
        d.writeCode();

        Manager m = new Manager();
        m.id = 102;
        m.name = "David";

        m.display();
        m.conductMeeting();
    }
}
```

Output:
```
101 John
Developer writes Java code
102 David
Manager conducts meetings
```

Interview points:

- Code reusability.
- Parent-child relationship.
- Achieved using `extends` keyword.
- Supports method overriding.

**3. Polymorphism**

Polymorphism means one thing behaving in different ways.
There are two types.
**A. Compile-time polymorphism (Method Overloading)**
Real-time example: Payment processing with different payment details.

```java
class Payment {

    void pay(int amount) {
        System.out.println("Cash payment: " + amount);
    }

    void pay(String upiId, int amount) {
        System.out.println("UPI payment: " + amount);
    }

    void pay(String cardNumber, int amount, String type) {
        System.out.println(type + " payment: " + amount);
    }
}

public class Main {
    public static void main(String[] args) {

        Payment p = new Payment();

        p.pay(1000);
        p.pay("user@upi", 2000);
        p.pay("123456", 3000, "Credit Card");
    }
}
```

Output:
```
Cash payment: 1000
UPI payment: 2000
Credit Card payment: 3000
```

**B. Runtime polymorphism (Method Overriding)**
Real-time example: Different payment methods process payments differently.

```java
class Payment {

    void makePayment() {
        System.out.println("Processing payment");
    }
}

class UpiPayment extends Payment {

    @Override
    void makePayment() {
        System.out.println("Processing UPI payment");
    }
}

class CardPayment extends Payment {

    @Override
    void makePayment() {
        System.out.println("Processing Card payment");
    }
}

public class Main {
    public static void main(String[] args) {

        Payment p;

        p = new UpiPayment();
        p.makePayment();

        p = new CardPayment();
        p.makePayment();
    }
}
```

Output:
```
Processing UPI payment
Processing Card payment
```

Interview points:

- Method overloading = compile-time polymorphism.
- Method overriding = runtime polymorphism.
- Achieved through inheritance and method overriding.
- Parent reference can hold a child object.

**4. Abstraction**
Real-time example: ATM Machine
When we withdraw money from an ATM, we only interact with the withdrawal option. We don't need to know the internal implementation of how the bank processes the transaction.
We can achieve abstraction using abstract classes and interfaces.

```java
abstract class ATM {

    abstract void withdraw(double amount);

    void checkBalance() {
        System.out.println("Checking account balance");
    }
}

class SBIATM extends ATM {

    @Override
    void withdraw(double amount) {
        System.out.println("Withdrawing Rs. " + amount);
    }
}

public class Main {
    public static void main(String[] args) {

        ATM atm = new SBIATM();

        atm.checkBalance();
        atm.withdraw(5000);
    }
}
```

Output:
```
Checking account balance
Withdrawing Rs. 5000.0
```

Interview points:
- Hides implementation details.
- Shows only essential functionality.
- Achieved using abstract classes and interfaces.
- Reduces complexity.


1. ⭐ What is the difference between an abstract class and an interface?
2. ⭐ What is polymorphism? Explain compile-time and runtime polymorphism.
3. ⭐ What is method overloading vs method overriding?
4. ⭐ What is encapsulation?
5.  ⭐ What is inheritance?
6.  ⭐ What is an immutable class? How do you create one?
7.  ⭐ Why is String immutable in Java?
8.  ⭐ What is the difference between `==` and `equals()`?
9.  ⭐ What is the difference between `equals()` and `hashCode()`?
10. ⭐ Explain the Java Collections Framework.
11. ⭐ Difference between List, Set, and Map.
12. ⭐ Difference between ArrayList and LinkedList.
13. ⭐ Difference between HashMap and ConcurrentHashMap.
14. ⭐ How does HashMap work internally?
15. What happens when two keys have the same hashcode?
16. What is the difference between HashSet and TreeSet?
17. What is the difference between HashMap and Hashtable?
18. What is Stream API?
19. ⭐ Explain `map()`, `filter()`, and `collect()`.
20. What is the difference between `map()` and `flatMap()`?
21. What is Optional in Java?
22. What are functional interfaces?
23. What is a lambda expression?
24. What is the difference between checked and unchecked exceptions?
25. ⭐ Difference between `throw` and `throws`.
26. How do you create a custom exception?
27. What is try-with-resources?
28. What is multithreading?
29. Difference between Thread and Runnable.
30. What is ExecutorService?
31. What is synchronization?
32. What is the difference between synchronized and volatile?

---

# 2. Spring / Spring Boot ⭐⭐⭐

1. ⭐ What is Spring Framework?
2. ⭐ What is Spring Boot?
3. ⭐ Why do we use Spring Boot instead of traditional Spring?
4. ⭐ What is Dependency Injection?
5. ⭐ What is Inversion of Control?
6. ⭐ Explain constructor injection vs field injection.
7. ⭐ Why is constructor injection preferred over `@Autowired`?
8. ⭐ What is a Spring Bean?
9. ⭐ What is the Spring Bean lifecycle?
10. ⭐ What is `@Component`?
11. Difference between `@Component`, `@Service`, and `@Repository`.
12. ⭐ What is `@RestController`?
13. Difference between `@Controller` and `@RestController`.
14. ⭐ What is `@Autowired`?
15. What is `@Qualifier`?
16. What is `@Primary`?
17. What is `@Configuration`?
18. What is `@Bean`?
19. ⭐ What is Spring Boot auto-configuration?
20. What are Spring Boot starters?
21. What is `application.properties` / `application.yml`?
22. ⭐ What are Spring Profiles?
23. How do you configure different environments such as DEV, QA, and PROD?
24. What is Spring Boot Actuator?
25. What is `@Value`?
26. What is `@ConfigurationProperties`?

---

# 3. REST API ⭐⭐⭐

1. ⭐ What is REST?
2. ⭐ What are the principles of REST?
3. ⭐ Difference between REST and SOAP.
4. ⭐ What are HTTP methods?
5. ⭐ Difference between GET, POST, PUT, PATCH and DELETE.
6. ⭐ Difference between PUT and PATCH.
7. ⭐ What are HTTP status codes?
8. ⭐ Difference between 200, 201, 204.
9. ⭐ Difference between 400, 401, 403 and 404.
10. ⭐ Difference between 500 and 503.
11. ⭐ What is idempotency?
12. Which HTTP methods are idempotent?
13. ⭐ What is JSON?
14. Difference between JSON and XML.
15. ⭐ How do you create a REST API using Spring Boot?
16. ⭐ How do you consume another REST API from a Spring Boot application?
17. What is OpenFeign?
18. What is RestTemplate?
19. What is WebClient?
20. Difference between RestTemplate, WebClient and OpenFeign.
21. ⭐ How do you handle exceptions globally in REST APIs?
22. ⭐ What is `@ControllerAdvice`?
23. ⭐ What is `@ExceptionHandler`?
24. How do you validate request data?
25. What is `@Valid`?
26. What is `@RequestBody`?
27. What is `@PathVariable`?
28. What is `@RequestParam`?
29. Difference between `@PathVariable` and `@RequestParam`.
30. What is content negotiation?
31. What is API versioning?
32. How would you design a scalable REST API?

---

# 4. Microservices ⭐⭐⭐

1. ⭐ What are microservices?
2. ⭐ Monolithic architecture vs microservices.
3. ⭐ What are the advantages of microservices?
4. ⭐ What are the disadvantages of microservices?
5. ⭐ How do microservices communicate with each other?
6. ⭐ What is service discovery?
7. What is Eureka?
8. ⭐ What is API Gateway?
9. Why do we use an API Gateway?
10. ⭐ What is OpenFeign?
11. ⭐ How does one microservice call another microservice?
12. What happens if the downstream service is unavailable?
13. ⭐ What is circuit breaker?
14. What is Resilience4j?
15. What is retry mechanism?
16. What is timeout?
17. What is fallback?
18. ⭐ How do you handle failures between microservices?
19. ⭐ How do you secure microservices?
20. What is distributed tracing?
21. What is centralized logging?
22. What is Spring Cloud Config?
23. ⭐ How do you manage configuration across multiple environments?
24. What is database-per-service?
25. Why shouldn't multiple microservices directly share the same database?
26. What is eventual consistency?
27. What is Saga pattern?
28. What is synchronous vs asynchronous communication?
29. How would you monitor microservices?
30. ⭐ Explain the architecture of your current project.

---

# 6. Spring Security ⭐⭐⭐

1. ⭐ What is Spring Security?
2. ⭐ What is authentication vs authorization?
3. ⭐ What is JWT?
4. ⭐ Explain JWT authentication flow.
5. What are the three parts of a JWT?
6. ⭐ Where should JWT be sent in an HTTP request?
7. What is `Authorization: Bearer <token>`?
8. ⭐ How do you implement JWT authentication in Spring Boot?
9. What is a security filter?
10. What is SecurityFilterChain?
11. What is BCrypt?
12. Why shouldn't we store passwords as plain text?
13. ⭐ How do you implement role-based authorization?
14. Difference between authentication and authorization.
15. What is CORS?
16. What is CSRF?
17. Difference between CORS and CSRF.
18. How do you secure REST APIs?
19. How do you handle expired JWT tokens?
20. Where should secrets/passwords be stored?

---

# 7. OOP + Design Patterns ⭐⭐

1. ⭐ Explain SOLID principles.
2. ⭐ What is Single Responsibility Principle?
3. ⭐ What is Open/Closed Principle?
4. What is Liskov Substitution Principle?
5. What is Interface Segregation?
6. What is Dependency Inversion?
7. ⭐ What are design patterns?
8. What is Singleton pattern?
9. What is Factory pattern?
10. What is Builder pattern?
11. What is Strategy pattern?
12. What is Observer pattern?
13. ⭐ Which design patterns have you used in your project?
14. Where would you use the Factory pattern?
15. How does Spring use design patterns internally?

---

# 8. MySQL / MariaDB ⭐⭐⭐

1. ⭐ What is a relational database?
2. ⭐ What is primary key?
3. What is foreign key?
4. What is normalization?
5. Explain 1NF, 2NF and 3NF.
6. ⭐ Difference between INNER JOIN and LEFT JOIN.
7. Difference between WHERE and HAVING.
8. ⭐ What is an index?
9. Advantages and disadvantages of indexes.
10. What is a composite index?
11. ⭐ How do you improve a slow SQL query?
12. What is a transaction?
13. ⭐ Explain ACID properties.
14. What is transaction isolation?
15. What is deadlock?
16. How do you handle database deadlocks?
17. What is connection pooling?
18. What is HikariCP?
19. ⭐ How does Java connect to MySQL?
20. What is JDBC?
21. What is JPA?
22. What is Hibernate?
23. ⭐ Difference between JPA and Hibernate.
24. What is lazy loading?
25. What is eager loading?
26. What is N+1 query problem?
27. ⭐ How do you handle transactions in Spring Boot?
28. What does `@Transactional` do?

---

# 9. Docker ⭐⭐

1. ⭐ What is Docker?
2. Why do we use Docker?
3. Docker vs Virtual Machine.
4. What is a Docker image?
5. ⭐ What is a Docker container?
6. Difference between Docker image and container.
7. What is Dockerfile?
8. ⭐ Explain a basic Dockerfile for a Spring Boot application.
9. What is Docker Compose?
10. What is Docker Hub?
11. What is a Docker volume?
12. What is a Docker network?
13. How do you check running containers?
14. How do you view container logs?
15. How do you expose a port in Docker?
16. How do you pass environment variables to Docker?
17. ⭐ How would you Dockerize a Spring Boot application?

---

# 10. Kubernetes ⭐⭐

1. ⭐ What is Kubernetes?
2. Why do we use Kubernetes?
3. ⭐ What is a Kubernetes cluster?
4. What is a node?
5. ⭐ What is a Pod?
6. What is a Deployment?
7. ⭐ What is a Service?
8. Difference between Pod, Deployment and Service.
9. What is ConfigMap?
10. What is Secret?
11. ⭐ What is replica count?
12. What happens when a Pod crashes?
13. How does Kubernetes maintain desired replicas?
14. What is horizontal pod autoscaling?
15. What is Ingress?
16. What is namespace?
17. ⭐ How do you check Pod logs?
18. How do you troubleshoot a failed Pod?
19. What is `kubectl`?
20. What is Helm?
21. What is a Helm chart?
22. What is `values.yaml`?
23. ⭐ How do you deploy a Spring Boot application to Kubernetes?

---