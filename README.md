# Spring Bootiful Dashboards

Practice with reference https://spring.io/blog/2016/12/07/spring-tips-bootiful-dashboards

## Step 1. Start Eureka Service

### Generate Project by [SPRING INITIALIZR](http://start.spring.io/)
- Artifact: eureka-service
- Dependencies: Eureka Server

### EurekaServiceAppliation.java
```
@EnableEurekaServer
```

### application.properties
```
spring.application.name=eureka-service
server.port=8761
```

## Step 2. Start Client Application

### 2-1. Generate Client A Project by SPRING INITIALIZR
- Artifact: client-a
- Dependencies: Eureka Discovery, Web, Actuator

### ClientAAppliation.java
```
@EnableDiscoveryClient
@RestController

@GetMapping("/")
public String name() {
    return "a";
}
```

### application.properties
```
spring.application.name=client-a
server.port=8080
management.security.enabled=false
```

### 2-2. Generate Client B Project by SPRING INITIALIZR
- Artifact: client-b
- Dependencies: Eureka Discovery, Web, Actuator

### ClientBAppliation.java
```
@EnableDiscoveryClient
@RestController

@GetMapping("/")
public String name() {
    return "b";
}
```

### application.properties
```
spring.application.name=client-b
server.port=8081
management.security.enabled=false
```

## Step 3. Start Admin Server

### Generate Project by SPRING INITIALIZR
- Artifact: spring-boot-admin
- Dependencies: Eureka Discovery, Web, Actuator
- **spring-boot 1.4.4** (not supoort 1.5.x)

### pom.xml
```
<dependency>
    <groupId>de.codecentric</groupId>
    <artifactId>spring-boot-admin-server</artifactId>
    <version>1.4.4</version>
</dependency>
<dependency>
    <groupId>de.codecentric</groupId>
    <artifactId>spring-boot-admin-server-ui</artifactId>
    <version>1.4.4</version>
</dependency>
```

### SpringBootAdminApplication.java
```
@EnableAdminServer
@EnableDiscoveryClient
```

### application.properties
```
spring.application.name=spring-boot-admin
server.port=8082
```

## Step 4. Start Microservice Dashboard

### Generate Project by SPRING INITIALIZR
- Artifact: microservices-dashboard
- Dependencies: Eureka Discovery, Web, Actuator
- **spring-boot 1.4.4** (not supoort 1.5.x)

### pom.xml
```
<dependency>
    <groupId>be.ordina</groupId>
    <artifactId>microservices-dashboard-server</artifactId>
    <version>1.0.1</version>
</dependency>
```

### SpringBootAdminApplication.java
```
@EnableMicroservicesDashboardServer
@EnableDiscoveryClient
```

### application.properties
```
spring.application.name=microservices-dashboard
server.port=8083
```
