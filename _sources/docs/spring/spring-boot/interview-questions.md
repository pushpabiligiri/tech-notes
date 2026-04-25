Spring Boot Interview Question
==============================

How does JVM memory structure work?
-----------------------------------
The **JVM (Java Virtual Machine)** divides memory into different areas to manage execution efficiently. <br> The main parts are: <br>
* Heap
* Stack
* Metaspace
  
**1. Heap Memory:** Used to store **objects and instance variables**

**2. Stack Memory:** Used for **method execution**
* Each thread has its own stack
* **it Stores :** Local variables, Method calls, Object references
* Works in **LIFO (Last In First Out)**

**3. Metaspace:** Stores **class-level information**
* Class metadata
* Method metadata
* Static variables
* Uses **native memory (outside heap)**
* Introduced in Java 8 (replaced PermGen)


How SpringBoot Auto-Configuration works?
----------------------------------------
``@SpringBootApplication`` is the entry point of a Spring Boot application. 

It internally includes:
* ``@Configuration``
* ``@EnableAutoConfiguration`` 
* ``@ComponentScan`` <br>
``@EnableAutoConfiguration`` automatically configures beans based on classpath dependencies using conditional annotations, which reduces manual configuration.”


What is a Spring Bean?
----------------------
A Spring Bean is an object that is created and managed by the Spring IoC container.

What are Spring Boot Starters?
---------------------------------
Spring Boot Starters are predefined dependency bundles that help developers quickly add common functionalities

Explain the different fetch types — EAGER vs LAZY?
--------------------------------------------------
*	**FetchType.EAGER**: Loads data immediately along with the parent entity
*	**FetchType.LAZY**: Loads data only when it is accessed

What is CascadeType and when do you use it?    
-----------------------------------------------       
Any operations performed on a parent entity should be automatically applied to its related (child) entities
It is useful when the child entity’s lifecycle depends on the parent.

What is the difference between save() and saveAndFlush()?
---------------------------------------------------------
* **The save():** stores the entity in the persistence context and writes it to the database at transaction commit
* **saveAndFlush():** saves the entity and immediately flushes the changes to the database

How can you perform pagination and sorting in Spring Data JPA?
-----------------------------------------------------------------
Pagination is implemented using the Pageable interface, which allows fetching data in pages. 
Sorting is implemented using the Sort class.
 Both can be combined using PageRequest to retrieve paginated and sorted data efficiently. The result is returned as a Page object, which includes metadata like total elements and total pages.

Difference between Pageable and Page?
* Pageable → input (request) 
* Page → output (response with data + metadata)

What is @Query and @Param used for?
-------------------------------------
* @Query is used to write custom JPQL or native SQL queries inside a repository interface.
* @Param is used to bind method parameters to query parameters in @Query.






