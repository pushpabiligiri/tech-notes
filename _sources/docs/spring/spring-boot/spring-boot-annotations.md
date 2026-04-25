# SpringBoot Annotations


## Core Spring Boot Annotations

> **@SpringBootApplication** <br>
> Main annotation used to start a Spring Boot application.
> It combines:
    > - `@Configuration `
    > - `@EnableAutoConfiguration`
    >- `@ComponentScan`

## Configuration & Bean Annotations

**@Configuration** <br>
Marks a class as a configuration class where Spring beans are defined.

**@Bean** <br>
Used inside @Configuration class to define a bean manually.
Spring will manage the returned object.

**@ComponentScan** <br>
Tells Spring to scan specific packages for components (@Component, @Service, etc.).

**@Import** <br>
Used to import other configuration classes into the current configuration.

## Stereotype Annotations

**@Component** <br>
Generic annotation to mark a class as a Spring-managed bean.

**@Service** <br>
Stereotype type annotation used in the service layer (business logic).

**@Repository** <br>
Used in the DAO layer for database operations.

**@Controller** <br>
Used in Spring MVC to handle web requests and return views.

**@RestController** <br>
Used for REST APIs (returns JSON/XML).
It combines: `@Controller` `@ResponseBody`
 
## REST API Annotations

**@RequestMapping** <br>
Maps HTTP requests to handler methods (supports all HTTP methods).

**@GetMapping** <br>
Handles HTTP GET requests (fetch data).

**@PostMapping** <br>
Handles HTTP POST requests (create data).

**@putMapping** <br>
Handles HTTP PUT requests (update full data).

**@DeleteMapping** <br>
Handles HTTP DELETE requests (remove data).

**@PatchMapping** <br>
Handles partial updates.

## Request Handling Annotations

**@PathVariable** <br>
Extracts values from URL path.
    Example: ``/user/{id}``

**@RequestParam** <br>
Extracts query parameters from URL.
    Example:``?id=10``

**@RequestBody** <br>
Converts JSON request body into Java object.

**@ResponseBody** <br>
Converts Java object into JSON response.

## Dependency Injection Annotations

**@Autowired** <br>
Automatically injects required dependencies by Spring.

**@Qualifier** <br>
Used to specify which bean to inject when multiple exist.

**@Primary** <br>
Marks a bean as default when multiple candidates exist.

**@Value** <br>
Injects values from ``application.properties`` or ``application.yml``.

## JPA / Database Annotations

**@Entity** <br>
Marks a class as a database table entity.

**@Table** <br>
Specifies table name in database.

**@Id** <br>
Marks primary key field.

**@GeneratedValue** <br>
Automatically generates primary key values.

**@Column** <br>
Maps field to a database column.

### Relationship Annotations
 > * @OneToOne → one-to-one mapping
 > * @OneToMany → one-to-many mapping
 > * @ManyToOne → many-to-one mapping
 > * @ManyToMany → many-to-many mapping

**@JoinColumn** <br>
Specifies foreign key column.

**@Transactional** <br>
Ensures a method executes inside a database transaction.

## Validation Annotations

**@NotNull** <br>
Value must not be null.

**@NotEmpty** <br>
Value must not be empty (for strings/collections).

**@NotBlank** <br>
String must not be null and not blank spaces.

**@Size** <br>
Sets length limit.

**@Min / @Max** <br>
Sets minimum and maximum numeric values.

**@Email** <br>
Validates email format.

## Testing Annotations

**@SpringBootTest** <br>
Loads full Spring application context for testing.

**@WebMvcTest** <br>
Used to test only controller layer.

**@MockBean** <br>
Creates mock objects for testing.

**@DataJpaTest** <br>
Used to test repository (JPA) layer.

**@Test**<br>
Marks a test method (JUnit).

## Caching & Scheduling

**@EnableCaching** <br>
Enables caching in Spring Boot.

**@Cacheable** <br>
Stores method result in cache.

**@CachePut** <br>
Updates cache.

**@CacheEvict** <br>
Removes cache data.

**@EnableScheduling** <br>
Enables scheduled tasks.

**@Scheduled** <br>
Runs method automatically at fixed time intervals.

## Microservices Annotations

**@FeignClient** <br>
Used for calling other microservices easily.

**@LoadBalanced** <br>
Enables client-side load balancing.

**@EnableEurekaClient** <br>
Registers service with Eureka server.

**@CircuitBreaker** <br>
Prevents failure propagation in microservices.