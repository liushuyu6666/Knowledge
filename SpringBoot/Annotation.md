# Overview
Annotations in Spring are used to provide metadata to the Spring container, which is responsible for managing the application's beans, dependencies, and other components. During the startup of the application, the Spring container scans the classes in the application's classpath and execute the annotations.  

For example, the `@SpringBootApplication` annotation is used to mark the main class of a Spring Boot application, which allows the Spring container to identify the application's entry point and initialize it. Similarly, annotations like `@Controller`, `@Service`, and `@Repository` are used to mark classes that should be managed as Spring components, allowing them to be automatically registered and wired to other components in the application.  

This page provides an overview of several frequently used annotations.

## `@Value`
what is the default folder, where does this default folder defined. 

## `@Repository`
This annotation is used to mark a class that encapsulates data access logic, such as interacting with a database or other persistent storage mechanism.