# Java Interview Questions

##  1. Core Java – Basics

### Java Basics and OOP Concepts

* What are the main features of Java 8?
* What are the important features introduced in Java 17 and 21?
* Why is Java platform-independent?
* What are the 4 pillars of OOP with real-time examples?
* Difference between **Abstraction vs Encapsulation**
* What is the difference between an abstract class and an interface?
* What is **Polymorphism**? Types?
* What is **Inheritance**? Types in Java

### Strings
* What is an immutable class? How do you create one?
* Why is `String` immutable?
* Difference between `==` vs `equals()`
* Difference between `String`, `StringBuilder`, `StringBuffer`
* What is String Pool?
  
---

## 2. Collections Framework (Very Important)

* Difference between **List, Set, Map**
* Difference between `ArrayList` vs `LinkedList`
* Difference between HashMap and ConcurrentHashMap.
* How does `HashMap` work internally?
* What is **hash collision**?
* What is **hashCode()** and why is it important?
* What is the difference between `equals()` and `hashCode()`?
* Difference between `HashMap` and `ConcurrentHashMap`
* What happens when two keys have the same hashcode?
* What is the difference between HashSet and TreeSet?
* What is the difference between HashMap and Hashtable?
* Why `HashSet` does not allow duplicates?
* What is **Comparable vs Comparator**?

👉 **Advanced follow-up:**

* How resizing happens in HashMap?
* What is load factor and threshold?

---

## 3. Exception Handling

* Difference between **Checked vs Unchecked exceptions**
* What is `try-catch-finally`?
* Can finally block not execute?
* What is `throw` vs `throws`?
* How do you create a custom exception?
* What is try-with-resources?

---

## 4. Multithreading & Concurrency (High Priority)

* What is a thread?
* What is multithreading?
* Difference between Thread and Runnable.
* Difference between `Runnable` and `Callable`
* What is synchronization?
* What is thread safety?

👉 **Advanced:**

* What is **Deadlock**? How to prevent it?
* What is **volatile keyword**?
* Difference between `wait()`, `sleep()`, `notify()`
* What is **ExecutorService**?
* What is **Thread Pool**?

👉 Real question:

> How do you make a class thread-safe?

---

## 5. JVM & Memory Management (Important for 3+ years)

* What is JVM architecture?
* Explain **Heap vs Stack**
* What is **Metaspace**?
* What is **Garbage Collection**?

👉 Advanced:

* Types of GC (G1, CMS)
* What causes **OutOfMemoryError**?
* How to debug memory issues in production?

---

## 6. Java 8+ Features (Must for Interviews)

* What are **Lambda expressions**?
* What is **Functional Interface**?
* What is **Stream API**?
* Explain map(), filter(), and collect()?
* What is the difference between map() and flatMap()?
* What is Optional in Java?
* 

👉 Advanced:

* Difference between `map()` vs `flatMap()`
* What is **Optional**?
* Parallel streams – pros/cons

---

## 7. Spring Boot (VERY IMPORTANT)

* What is Spring Framework?
* What is Spring Boot?
* Why do we use Spring Boot instead of traditional Spring?
* What is **@SpringBootApplication**?
* What is **Dependency Injection**?
* Explain constructor injection vs field injection.
* Why is constructor injection preferred over @Autowired?
* What is a Spring Bean?
* What is the Spring Bean lifecycle?
* What is @Component?
* Difference between @Component, @Service, and @Repository.
* What is @RestController?
* Difference between @Controller and @RestController.
* What is @Autowired?
* What is @Qualifier?
* What is @Primary?
* What is @Configuration?
* What is @Bean?
* What is Spring Boot auto-configuration?
* How **Auto-Configuration** works?
* What are Spring Boot starters?
* What is application.properties / application.yml?
* What are Spring Profiles?
* How do you configure different environments such as DEV, QA, and PROD?
* What is Spring Boot Actuator?
* What is @Value?
* What is @ConfigurationProperties?

---

## 8. REST API 

* What is REST?
* What are the principles of REST?
* Difference between REST and SOAP.
* What are HTTP methods?
* Difference between **GET, POST, PUT, PATCH, DELETE**
* What are HTTP status codes?
* What is **idempotent API**?
* What is idempotency?
* Which HTTP methods are idempotent?
* How do you create a REST API using Spring Boot?
* How do you consume another REST API from a Spring Boot application?
* What is OpenFeign?
* What is RestTemplate?
* What is WebClient?
* How do you handle exceptions globally in REST APIs?
* What is @ControllerAdvice?
* What is @ExceptionHandler?
* How do you validate request data?
* What is @Valid?
* What is @RequestBody?
* What is @PathVariable?
* What is @RequestParam?
* Difference between @PathVariable and @RequestParam.
* What is content negotiation?
* What is API versioning?
* How would you design a scalable REST API?

## 9. Microservices
* What are microservices?
* What are the advantages of microservices?
* What are the disadvantages of microservices?
* How do microservices communicate with each other?
* What is **API Gateway**?
* What is **Service Discovery (Eureka)**?
* What happens if the downstream service is unavailable? / How do you handle failures between microservices?
* What is circuit breaker?
* What is Resilience4j?
* What is retry mechanism?
* What is timeout?
* What is fallback?
* How do you secure microservices?
* What is distributed tracing?
* What is centralized logging?
* What is Spring Cloud Config?
* How do you manage configuration across multiple environments?
* What is Saga pattern?
* What is synchronous vs asynchronous communication?
* How would you monitor microservices?
* Explain the architecture of your current project.

---

## 10. Spring Security

* What is Spring Security?
* What is authentication vs authorization?
* What is JWT?
* Explain JWT authentication flow.
* What are the three parts of a JWT?
* Where should JWT be sent in an HTTP request?
* What is Authorization: Bearer <token>?
* How do you implement JWT authentication in Spring Boot?
* What is a security filter?
* What is SecurityFilterChain?
* What is BCrypt?
* Why shouldn't we store passwords as plain text?
* How do you implement role-based authorization?
* Difference between authentication and authorization.
* What is CORS?
* What is CSRF?
* Difference between CORS and CSRF.
* How do you secure REST APIs?
* How do you handle expired JWT tokens?
* Where should secrets/passwords be stored?

---

## 11. OOP + Design Patterns

* Explain SOLID principles.
* What are design patterns?
* Which design patterns have you used in your project?
* Where would you use the Factory pattern?
* How does Spring use design patterns internally?
---

## 12. Database & SQL

* What is a relational database?
* What is primary key?
* What is foreign key?
* Difference between **SQL vs NoSQL**
* What is **Normalization**?
* Explain 1NF, 2NF and 3NF.
* Difference between INNER JOIN and LEFT JOIN.
* Difference between WHERE and HAVING.
* What are **Indexes**?
* Advantages and disadvantages of indexes.
* How do you improve a slow SQL query?
* What is a transaction?
* Explain ACID properties.
* What is transaction isolation?
* What is deadlock?
* How do you handle database deadlocks?
* What is connection pooling?
* What is HikariCP?
* How does Java connect to MySQL?
* What is JDBC?
* What is JPA?
* What is Hibernate?
* Difference between JPA and Hibernate.
* What is lazy loading?
* What is eager loading?
* What is **N+1 problem**?
* What is **JPA/Hibernate**?
* How do you handle transactions in Spring Boot?
* What does @Transactional do?
* What is pagination?

---
## 13. Docker & Kubernetes — Backend Deployment
1. What is Docker?
2. Why do we use Docker for backend applications?
3. Docker image vs container.
4. What is a Dockerfile?
5. How do you Dockerize a Spring Boot application?
6. What is Docker Compose?
7. What is Kubernetes?
8. What is a Kubernetes cluster?
9. What is a Pod?
10. What is a Deployment?
11. What is a Service?
12. Pod vs Deployment vs Service.
13. What is ConfigMap?
14. What is Secret?
15. What is replica count?
16. How do you check backend application logs in Kubernetes?
17. How do you troubleshoot a restarting Pod?

---

## Backend Scenario-Based Questions 
These are very important for a 3–4 year developer:
1. Your REST API is taking 10 seconds to respond. How will you troubleshoot it?
2. Your API suddenly starts returning 500 errors in production. What will you check?
3. One microservice is down. How will you prevent cascading failures?
4. A database query is taking 5 seconds. How will you optimize it?
5. Your API is receiving 10,000 requests per minute. How would you handle the load?
6. How would you implement pagination for a large database table?
7. How would you prevent duplicate requests from creating duplicate records?
8. How would you design an API for creating and retrieving employees?
9. How would you secure an API containing sensitive information?
10. A third-party API is intermittently failing. How would you handle it?
11. How would you implement retry without causing excessive load?
12. How would you handle concurrent updates to the same database record?
13. How would you troubleshoot memory issues in a Java application?
14. How would you troubleshoot high CPU usage in a Spring Boot application?
15. How would you handle a database connection pool getting exhausted?
16. How would you design communication between two microservices?
17. How would you handle API backward compatibility?
18. How would you design centralized exception handling?
19. How would you improve the performance of an existing backend service?
20. Explain a challenging backend issue you solved in your project.