# Spring Boot Annotations, IoC, DI, and ApplicationContext

## Overview
This repository provides an overview of commonly used Spring Boot annotations along with explanations of Inversion of Control (IoC), Dependency Injection (DI), and ApplicationContext.

## Table of Contents
- [Spring Boot Annotations](#spring-boot-annotations)
- [Spring Security Annotations](#spring-security-annotations)
- [Spring Data JPA Annotations](#spring-data-jpa-annotations)
- [Inversion of Control (IoC)](#inversion-of-control-ioc)
- [Dependency Injection (DI)](#dependency-injection-di)
- [ApplicationContext](#applicationcontext)
- [Resources](#resources)

---

## Spring Boot Annotations
Spring Boot provides several annotations to simplify the development process. Below are some important annotations and their usage:

| Annotation | Description |
|------------|------------|
| `@SpringBootApplication` | Marks the main class of a Spring Boot application. Combines `@Configuration`, `@EnableAutoConfiguration`, and `@ComponentScan`. |
| `@RestController` | A combination of `@Controller` and `@ResponseBody`, used to define RESTful web services. |
| `@RequestMapping` | Maps HTTP requests to handler methods. Can be used at both the class and method levels. |
| `@GetMapping`, `@PostMapping`, `@PutMapping`, `@DeleteMapping` | Specialized forms of `@RequestMapping` for HTTP GET, POST, PUT, and DELETE requests. |
| `@Component`, `@Service`, `@Repository` | Marks a class as a Spring-managed component, service, or repository. |
| `@Autowired` | Enables automatic dependency injection. |
| `@Qualifier` | Used along with `@Autowired` to specify the exact bean to inject when multiple options exist. |
| `@Value` | Injects values from application properties. |
| `@Bean` | Declares a method as a bean provider within a `@Configuration` class. |
| `@Configuration` | Indicates that a class contains Spring configuration. |
| `@EnableAutoConfiguration` | Enables Spring Boot's auto-configuration mechanism. |
| `@Transactional` | Marks a method or class as transactional. |

---

## Spring Security Annotations
Spring Security provides several annotations to handle authentication and authorization.

| Annotation | Description |
|------------|------------|
| `@EnableWebSecurity` | Enables Spring Security's web security support. |
| `@EnableGlobalMethodSecurity` | Enables method-level security. Deprecated in newer versions, replaced by `@EnableMethodSecurity`. |
| `@EnableMethodSecurity` | Enables method-level security in Spring Security 6+. |
| `@PreAuthorize` | Defines access control before method execution. |
| `@PostAuthorize` | Defines access control after method execution. |
| `@Secured` | Specifies security constraints at the method level. |
| `@RolesAllowed` | Similar to `@Secured`, defines role-based access control. |
| `@AuthenticationPrincipal` | Injects the currently authenticated user into a controller method. |

---

## Spring Data JPA Annotations
Spring Data JPA simplifies database interactions through annotations.

| Annotation | Description |
|------------|------------|
| `@Entity` | Marks a class as a JPA entity. |
| `@Table(name = "table_name")` | Specifies the table name for an entity. |
| `@Id` | Marks a field as the primary key. |
| `@GeneratedValue(strategy = GenerationType.IDENTITY)` | Auto-generates primary key values. |
| `@Column(name = "column_name")` | Maps a field to a specific database column. |
| `@OneToOne`, `@OneToMany`, `@ManyToOne`, `@ManyToMany` | Defines relationships between entities. |
| `@JoinColumn(name = "column_name")` | Specifies the foreign key column for relationships. |
| `@Repository` | Marks a class as a repository to handle data persistence. |
| `@Transactional` | Ensures database operations are executed within a transaction. |

---

## Inversion of Control (IoC)
IoC is a design principle where the control of object creation and dependency management is shifted from the application code to the Spring framework. The IoC container handles object instantiation, configuration, and dependency resolution, making the application loosely coupled.

### Benefits of IoC:
- Reduces dependency management complexity.
- Enhances modularity and testability.
- Promotes better separation of concerns.

---

## Dependency Injection (DI)
DI is a design pattern that allows injecting dependencies into an object rather than creating them within the object itself. Spring supports DI through:

1. **Constructor Injection** (Preferred for required dependencies):
   ```java
   @Service
   public class UserService {
       private final UserRepository userRepository;

       @Autowired
       public UserService(UserRepository userRepository) {
           this.userRepository = userRepository;
       }
   }
   ```

2. **Setter Injection** (Optional dependencies):
   ```java
   @Service
   public class UserService {
       private UserRepository userRepository;

       @Autowired
       public void setUserRepository(UserRepository userRepository) {
           this.userRepository = userRepository;
       }
   }
   ```

3. **Field Injection** (Not recommended due to poor testability):
   ```java
   @Service
   public class UserService {
       @Autowired
       private UserRepository userRepository;
   }
   ```

---

## ApplicationContext
`ApplicationContext` is the central interface in Spring that manages the lifecycle and configuration of beans. It extends `BeanFactory` and provides additional features like:

- Bean lifecycle management
- Internationalization support
- Event propagation
- Environment abstraction

### Example of `ApplicationContext` usage:
```java
import org.springframework.context.ApplicationContext;
import org.springframework.context.annotation.AnnotationConfigApplicationContext;

public class MainApplication {
    public static void main(String[] args) {
        ApplicationContext context = new AnnotationConfigApplicationContext(AppConfig.class);
        UserService userService = context.getBean(UserService.class);
        userService.doSomething();
    }
}
```

---

## Resources
- [Spring Framework Documentation](https://docs.spring.io/spring-framework/docs/current/reference/html/beans.html)
- [Spring Boot Official Guide](https://spring.io/projects/spring-boot)
- [Baeldung: Spring Annotations](https://www.baeldung.com/spring-annotations)

---

## Contributing
Feel free to open issues or submit pull requests if you find any errors or have suggestions for improvement.


---

### Author
[Alaa Eldin Apuelsoad](https://github.com/alaaeldin-apuelsoad)

