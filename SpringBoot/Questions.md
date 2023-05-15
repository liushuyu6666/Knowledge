# Overview
Raising questions here, help me to deeply understand the Spring Boot by raising and answering questions.

This is a draft, will be removed.

# Questions
1. annotation `@value`.
2. where did the code define the location of `application.properties`, can we move it to somewhere else.
3. what if I want three `application.properties`, one for remote_example, one for local, one for real remote (included in .gitignore)
4. why I run the application, an error prompted up 
   Caused by: org.springframework.beans.factory.BeanCreationException: Error creating bean with name 's3Service': Injection of autowired dependencies failed; nested exception is java.lang.IllegalArgumentException: Could not resolve placeholder 'aws.S3.properties.endpointUrl' in value "${aws.S3.properties.endpointUrl}"
I want to know the life circle, why the "${aws.S3.properties.endpointUrl}" is required when run the application. 
5. what build tool I am using, Maven ? or another build-in tool in the IntelliJ?
6. What is access point for aws s3
7. https://docs.spring.io/spring-boot/docs/1.0.1.RELEASE/reference/html/boot-features-external-config.html
8. When executing, what's the difference and relationship between `@service` and `@controller`, need to get answer after 手写spring boot.
9. What happens when we add a dependency in the `build.gridle` and click the elephant icon, like in nodejs, it will add the dependency in the node_modules, but where is it here? Is there any advice in the official website to add the dependency? Can we use cli instead of the elephant icon to build new added dependency?
10. When I use `FileService fs = new FileService()`. The `@Value` in `FileService` cannot work and return null. Meanwhile, we I use `@autowired` it could work, so my guess is that the container will not register the FileService as a been when using `new`, that's why `@value` can't work. More investigation need to be done - what is container. 手写spring boot and source code analysis. https://stackoverflow.com/questions/53482633/value-in-springboot-returns-null
11. When I use the postman to upload files to S3, get an error "The bucket does not allow ACLs". why? it should use the same credential in my spring boot jupiter restaurant. However, when I use `aws s3 cp /Desktop/test_image s3://jupiter-restaurant/` it works. Take a look at this [website](https://docs.aws.amazon.com/AmazonS3/latest/userguide/access-control-overview.html).
12. What is ACL, what is policy. what's the hierarchy (object owner and bucket owner).
13. Can we define it in the terraform?
14. It's more a about a Java question: I remember in a project (maybe it is Regex_Java), we have the dependency file under `.idea/libraries/junit.xml`. Does that mean the IntelliJ is using its own automation tool to build the project?