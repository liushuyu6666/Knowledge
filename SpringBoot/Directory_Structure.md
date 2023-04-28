# Overview
The recommended directory structure best practices can be found on the [official website](https://docs.spring.io/spring-boot/docs/current/reference/html/using.html#using.structuring-your-code.locating-the-main-class).

# Directory Structure
```text
com
 +- example
     +- myapplication
         +- Application.java
         |
         +- customer
         |   +- Customer.java
         |   +- CustomerController.java
         |   +- CustomerService.java
         |   +- CustomerRepository.java
         |
         +- order
             +- Order.java
             +- OrderController.java
             +- OrderService.java
             +- OrderRepository.java
```
According to the official Spring Boot documentation, the main application class (`Application.java`) should be located in a root package that is higher than other packages. Typically, the `@SpringBootApplication` annotation is applied to the main application class.

Other feature classes should be organized by their respective entities. For example, in this project, we have two feature classes - 'Customer' and 'Order' - each of which includes an entity, repository, service, and controller.