# Overview
A Spring Boot IoC (Inversion of Control) container is the environment in which the Spring Boot application runs. It is responsible for managing the application's beans, dependencies, and other components. The container is created during the startup of the Spring Boot application and remains active until the application is terminated.  

The Spring Boot container uses annotations to identify and manage the beans in the application. By default, the container automatically detects and configures most beans based on their classpath and the annotations they use. However, it is also possible to manually configure beans and their dependencies using Java configuration classes.

# Order of Annotation execution
The order of execution of annotations during the startup of the container is determined by their respective priorities.

The priorities of the commonly used annotations are as follows:

1. `@ConfigurationProperties`: This annotation binds the properties defined in the `application.properties` or `application.yml` file to a corresponding Java class. It has the highest priority and is executed first.

2. `@ComponentScan`: This annotation is used to specify the package(s) that should be scanned by the Spring container for components such as `@Component`, `@Service`, and `@Repository`.

3. `@EnableAutoConfiguration`: This annotation enables Spring Boot's auto-configuration mechanism, which automatically configures the application based on the classpath and other conditions. This annotation has a lower priority than `@ConfigurationProperties` and `@ComponentScan`.

4. `@SpringBootApplication`: This annotation is a combination of `@Configuration`, `@ComponentScan`, and `@EnableAutoConfiguration`. It has the lowest priority and is executed last.

The execution of annotations in Spring Boot results in the initialization of beans associated with their respective classes. The `@SpringBootApplication` annotation serves as the entry point for the project, but its associated bean is executed after other component beans. This is because the component beans must be generated first in order to satisfy dependencies, before the `@SpringBootApplication` bean can be initialized. 

It's important to note that the execution order of these annotations can vary depending on their usage and other factors in the application's configuration. However, in general, the order described above is a commonly used and reasonable default order.