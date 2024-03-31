# Spring Framework
- [Dependency Injection (DI)](#dependency-injection-di)
  - [What is DI?](#what-is-di)
  - [DI in Spring](#di-in-spring)
    - [@Component](#component)
    - [@Autowired](#autowired)
    - [@Bean](#bean)
- [Spring Architecture](#spring-architecture)
  - [@Controller](#controller)
  - [@Service](#service)
- [Project Lombok](#project-lombok)
- [Profiles](#profiles)
  - [Environment-Specific Configuration File](#environment-specific-configuration-file)
  - [@ConfigurationProperties](#configurationproperties)
- [REST API Endpoints](#rest-api-endpoints)
  - [Spring Data REST](#spring-data-rest)
  - [@RestController](#restcontroller)


## Dependency Injection (DI)

Dependency Injection (DI) is a design pattern that promotes code reuse, simplifies testing, and enhances manageability within applications. It's one of core principles in the Spring Framework.

### What is DI?

In the simplest terms, DI is a feature that stores objects to be used throughout the application in a container, making them easily accessible from various classes. The objects placed in the DI container are called Beans.

### DI in Spring

Spring Boot simplifies managing application components using DI.

At application startup, Spring Boot scans for classes with annotations like `@Controller`, `@Service`, `@Component`, and more. These instances are stored in the **DI container**. This is like a big box where Spring keeps all the components your application can use.

#### @Component

`@Component` marks a class as a component. When Spring scans your application, it finds these classes and creates single instances (beans) of them, managing their lifecycle. This is a direct part of the DI mechanism, where Spring automatically creates and injects instances where needed.


Tells Spring to manage your class and make it ready for use.

```java
@Component
public class MyService {
    public String sayHello() {
        return "Hello, Spring!";
    }
}
```

#### @Autowired

Asks Spring for an instance of a class without manually creating it.

`@Autowired` lets Spring automatically inject the necessary instances into your class. For constructor injection, you don't even need to use `@Autowired`.

```java
@Component
public class MyController {
    private MyService myService;

    // @Autowired
    public MyController(MyService myService) {
        this.myService = myService;
    }

    public void doSomething() {
        System.out.println(myService.sayHello());
    }
}
```

Using `@Component` and `@Autowired` together makes it easy for your classes to work together, without worrying about how they get instances of each other.

#### @Bean
A bean is an object that is instantiated and managed in a DI container.

`@Bean` is used on a method to specify that the return value should be managed as a bean. It is usually declared in methods of Configuration classes, which is marked with `@Configuration`.

Unlike `@Component`, which auto-detects and creates beans, `@Bean` is used for manual bean definition due to control over the instantiation process.

## Spring Architecture

`@Controller` and `@Service` are specializations of `@Component` for use in MVC (Model-View-Controller) web applications. Both are managed by Spring and can be injected with `@Autowired` where needed in the DI system.

### @Controller

`@Controller` marks a class as a web controller, capable of handling HTTP requests and delegating business logic to services.When someone visits a web address linked to your application, the right method inside a `@Controller` class is called.

```java
@Controller
public class WebController {

    // when someone visits `/greeting`, the `greet` method is called
    @GetMapping("/greeting")
    @ResponseBody
    public String greet() {
        return "Hello, Web Visitor!";
    }
}
```

### @Service

`@Service` indicates that a class holds business logic. It's more about organization and readability, suggesting the class's role in the application architecture rather than adding new behavior.

```java
@Service
public class UserService {
    // fetch user details from a database.
    public String getUserDetails(String userId) {
        return "Details for user " + userId;
    }
}
```


## Project Lombok

- Java library that is used to minimize or remove the boilerplate code.
- The `@Data` annotation automatically generates the getters/setters and toString() etc.
```java
@Entity
@Data // Lombok
@Table(name = "product")
public class Product {
　:
```


## Profiles
In Spring Boot, the base configuration file is `application.properties`.

### Environment-Specific Configuration File
You can create multiple profiles for different environments with specific suffixes, such as `application-dev.properties` and `application-prod.properties`.

To set the active profile within the default `application.properties` file, add:
```
spring.profiles.active=dev
```

In this example, Spring Boot will load the configurations from `application-dev.properties`.

### @ConfigurationProperties

You can group configurable values into neat classes using `@ConfigurationProperties`.

1. Create a properties class**
`@ConfigurationProperties` annotation that tells Spring Boot to fill this class with properties from configuration files like `application.properties`.

```java
@Component
@ConfigurationProperties(prefix="service")
public class ServiceProperties {
    private String url;
    private int timeout;
    :
```

2. Add configurations in `application.properties`
```
service.url=https://example.com/api
service.timeout=30
```

3. Use the `ServiceProperties`

```java
@Service
public class MyService {
    private final ServiceProperties properties;

    @Autowired
    public MyService(ServiceProperties properties) {
        this.properties = properties;
    }

    public void connect() {
        System.out.println("Connecting to " + properties.getUrl() + " with timeout " + properties.getTimeout());
        // ...
    }
```

## REST API Endpoints

What's the difference between `RepositoryRestConfigurer` and `@RestController`, focusing on creating REST API endpoints?

### Spring Data REST

With Spring Data REST, you can quickly implement fundamental CRUD features via `RepositoryRestConfigurer`. It automatically generates RESTful APIs based on Spring Data repositories connected to a database.

### @RestController

`@RestController` is better suited for APIs that include complex business logic. It allows you to customize request methods, parameters, response formats, and HTTP status codes as needed.
