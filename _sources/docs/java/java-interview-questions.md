# Java Interview Questions

##  1. Core Java – Basics (Must be Strong)

### OOP Concepts

* What are the 4 pillars of OOP?
* Difference between **Abstraction vs Encapsulation**
* What is **Polymorphism**? Types?
* What is **Inheritance**? Types in Java

### Java Basics

* Why is Java platform-independent?
* What is JVM, JRE, and JDK?
* Difference between **== vs equals()**
* What is **hashCode()** and why is it important?

### Strings

* Why is `String` immutable?
* Difference between `String`, `StringBuilder`, `StringBuffer`
* What is String Pool?

---

## 2. Collections Framework (Very Important)

* Difference between **List, Set, Map**
* Difference between `ArrayList` vs `LinkedList`
* How does `HashMap` work internally?
* What is **hash collision**?
* Difference between `HashMap` and `ConcurrentHashMap`
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

---

## 4. Multithreading & Concurrency (High Priority)

* What is a thread?
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

👉 Advanced:

* Difference between `map()` vs `flatMap()`
* What is **Optional**?
* Parallel streams – pros/cons

---

## 7. Spring Boot (VERY IMPORTANT)

* What is Spring Boot?
* What is **@SpringBootApplication**?
* What is **Dependency Injection**?

👉 Core annotations:

* `@Component`, `@Service`, `@Repository`
* `@Autowired`
* `@RestController`

👉 Advanced:

* How **Auto-Configuration** works?
* What is **Spring Bean lifecycle**?
* What is **@Bean vs @Component**?
* What is **Spring Boot Actuator**?

---

## 8. REST API & Microservices

* What is REST?
* Difference between **GET, POST, PUT, DELETE**
* What is **idempotent API**?

👉 Advanced:

* How do microservices communicate?
* What is **Feign Client**?
* What is **API Gateway**?
* What is **Service Discovery (Eureka)**?

👉 Real scenario:

> How will two microservices communicate? (REST vs Messaging Queue)

---

##  9. Database & SQL

* Difference between **SQL vs NoSQL**
* What is **Normalization**?
* What are **Indexes**?

👉 Advanced:

* How to optimize slow queries?
* What is **N+1 problem**?
* What is **JPA/Hibernate**?

---

## 10. System Design (Basic Level for 3+ yrs)

* How would you design a **URL shortener**?
* How to design a **scalable REST API**?
* What is **Caching**?

👉 Tools:

* Redis
* Kafka / RabbitMQ

---

## 1.  Coding / Problem Solving

* Reverse a String
* Remove duplicate characters
* Find first non-repeating character
* LRU Cache implementation
* Multithreading problems

---

## 1.  Real-Time Scenario Questions (VERY IMPORTANT)

These are asked most for 3+ years 👇

* Your API is slow in production. How will you fix it?
* Your application has memory leak. What will you do?
* How do you handle high traffic in your system?
* How do you ensure thread safety in real applications?
* How do you design logging in microservices?

---

# 🔥 Pro Tip (Important for You)

Since you are targeting **Java Backend (Spring Boot)** roles:

👉 Focus more on:

* Collections internal working
* Multithreading
* JVM memory
* Spring Boot internals
* Microservices communication

---
