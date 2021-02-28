---
id: 5c779a9e-83fe-48e9-a0bd-2e4bad5a04bf
title: Spring Boot up and Running
desc: ''
updated: 1614551166802
created: 1614538231072
---

## Chap 1: in nutshell

3 foundational features:

1. starters for dependency management
1. Executable JARs for Simplified Deployment
    - instead of **shading** (combining dependency + app JARs into one), **nest JARs**
    - can run the app 
        - simple `java -jar <SpringBootAppName.jar>`
        - make the Jar self-executable
1. convention over configuration
    - autoconfig
    - defaults favor local dev environment

## Chap 2: Choosing Tools and Getting Started

- Maven vs Gradle
  - Maven:
    - project structure strict convention
      - rigic declarative -> consistency -> less issues
  - Gradle:
    - Incremental compilation, only compile changes
    - allows scripting/programming
    - flexibility -> more tweaking and troubleshooting
- Java vs Kotlin
  - Kotlin
    - benefits:
      - less verbose
      - safe: by default no null values
      - define own syntax with "extension function" and "infix" - more readable

## Chap 3: REST API

- use https://httpie.io/ to test REST APIs (over Curl, postman)
- Use class-level @RequestMapping annotation for shared URL portion

  ```java
  @RestController
  @RequestMapping("/coffees")
  class RestApiDemoController {
  ```

- Use ResponseEntity to include status codes.

  ```java
  @PutMapping("/{id}")
  ResponseEntity<Coffee> putCoffee(@PathVariable String id,
          @RequestBody Coffee coffee) {
      
      ...
      
      return (coffeeIndex == -1) ?
              new ResponseEntity<>(postCoffee(coffee), HttpStatus.CREATED) :
              new ResponseEntity<>(coffee, HttpStatus.OK);
  }
  ```

## Chap 4: DB access
- `@entity` on model, no-arg constructor, setters on all fields
- **Repository**
  - `CrudRepository` with generic CRUD operations
  - `JpaRepository` extends `CrudRepository` 
  
## Chap 5: Config
- `@ConfigurationProperties(prefix = "greeting")`
- `@ConfigurationPropertiesScan` 
- need `spring-boot-configuration-processor` dependency
- Autoconfiguration Report
  - `java -jar bootapplication.jar --debug`
  - `java -Ddebug=true -jar bootapplication.jar`
  - `export DEBUG=true` in shell
  - add `debug=true` to `application.properties` file
- Actuator
  - runtime info get/set
  - need `spring-boot-starter-actuator` dependency
  - secure by default with little info
  - opening it up
    - `management.endpoints.web.exposure.include`
    - `management.endpoint.health.show-details=always`  or `when_authorized`
  - query
    - `/actuator/env` - get env variable and where config props comes from
    - `/actuator/beans` - all beans created
    - `actuator/health` - Health info (basic or expanded, depending on settings)
    - `/actuator/loggers` 
      -  `echo '{"configuredLevel": "TRACE"}'  | http :8080/actuator/loggers/org.springframework.data.web` change logger level on the fly
    - `/actuator/mappings`
    - `/actuator/heapdump` and `/actuator/threaddump`
    - `/actuator/metrics`