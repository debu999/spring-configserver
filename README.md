# Spring Config Server

```markdown
# Spring Config Server

## Overview

The Spring Config Server provides an externalized configuration in a distributed system. With the
Config Server, you can manage shared configuration across multiple applications and environments.

## Setup and Installation

1. Add the Spring Cloud Config Server dependency in your `pom.xml`:

```xml
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-config-server</artifactId>
</dependency>
```

2. Annotate your main application class with `@EnableConfigServer`:

```java

@SpringBootApplication
@EnableConfigServer
public class ConfigServerApplication {

  public static void main(String[] args) {
    SpringApplication.run(ConfigServerApplication.class, args);
  }
}
```

3. Configure your application properties in `application.yml` or `application.properties`:

```yml
spring:
  cloud:
    config:
      server:
        git:
          uri: https://github.com/your-repo/config-repo
```

## Usage

To use the Config Server, your client applications need to have the Spring Cloud Config Client
dependency and point to the Config Server's URL in their bootstrap configuration.

## Client Setup

1. Add the Spring Cloud Config Client dependency in your `pom.xml`:

```xml

<dependency>
  <groupId>org.springframework.cloud</groupId>
  <artifactId>spring-cloud-starter-config</artifactId>
</dependency>
```

2. Configure your bootstrap properties in `bootstrap.yml` or `bootstrap.properties`:

```yml
spring:
  cloud:
    config:
      uri: http://localhost:8888
```

Now, your client applications can consume the externalized configuration provided by the Config
Server.

## Refreshing Configuration

To refresh the configuration at runtime, you can expose the `/actuator/refresh` endpoint in your
client applications and trigger a POST request to it.

## Security

You can secure your Config Server using Spring Security. Please refer to the official Spring
Security documentation for more details.

## Further Reading

For more detailed information, please refer to the
official [Spring Cloud Config documentation](https://cloud.spring.io/spring-cloud-config/reference/html/).

```

This `README.md` provides a basic overview, setup instructions, usage details, and additional resources for a Spring Config Server.