# Overview
[Spring Cloud for AWS official website](https://docs.awspring.io/spring-cloud-aws/docs/2.4.1/reference/html/index.html)

# Configuration
To configure Spring Cloud AWS, more details in [Configuration in Spring Cloud for AWS official website](https://docs.awspring.io/spring-cloud-aws/docs/2.4.1/reference/html/index.html#spring-boot-auto-configuration)
## Configure AWS Credentials
AWS Credentials consists of `secret-key` and `access-key` Generally, there are two ways:
1. Store in the Spring Boot configuration files, `application.properties` or `application.yml`.
2. Store the credentials in `~/.aws/credentials` and use an alias in the configuration files.

**In aws credentials**
1. Store the credentials in `~/.aws/credentials` with an alias.
    ```text
    [springboot]
    aws_access_key_id=KEY
    aws_secret_access_key=SECRET
    ```
2. In the configuration file.
   ```yaml
    cloud:
        aws:
            credentials:
                profile-name: stratospheric
   ```


## References
1. Getting started with Spring Boot on AWS: [Part 1](https://aws.amazon.com/blogs/opensource/getting-started-with-spring-boot-on-aws-part-1/), [Part 2](https://aws.amazon.com/blogs/opensource/getting-started-with-spring-boot-on-aws-part-2/)