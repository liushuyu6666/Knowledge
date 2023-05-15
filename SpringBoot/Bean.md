# Overview
In Spring Boot, a bean is an object that is instantiated and managed by the Spring IoC (Inversion of Control) container. The properties and behavior of a bean are defined by its class, and its configuration is often specified using annotations.  

During the startup of the Spring Boot application, the container reads the application's configuration and creates instances of the beans that are defined. The container initializes the properties of the beans based on the configuration specified in the annotations and other configuration files.

# Number of bean
The number of bean instances generated for a class in Spring Boot depends on how the class is annotated and configured.

In general, a Spring Boot application will generate one bean instance for each class that is annotated with `@Component`, `@Service`, `@Repository`, or `@Controller`. These annotations are used to indicate that a class should be managed by the Spring IoC container as a bean.

If a class is annotated with `@Configuration`, it can define one or more bean methods that create and configure beans. Each method that is annotated with `@Bean` will create a new bean instance, and the bean name will be derived from the name of the method.

It's also possible to have multiple bean instances of the same class with different names or configurations by using the `@Qualifier` annotation or by defining separate configuration classes.