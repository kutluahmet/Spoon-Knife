# BACKBASE CODING CHALLENGE #

This is the explanation of the solution for Backbase Coding Exercise.

## Used Technologies and Libraries

+ Java 11
+ Spring Boot 2+ (REST API)
+ Maven 3+
+ Docker
+ Junit 5
+ Lombok
+ Swagger
+ Intellij IDEA

## Build and Run with Maven

To run the application on your local machine.

`mvn clean install`

`mvn spring-boot:run `

## Build and Run in Docker Container

To run the application in a docker container.

`docker build -t {image-name} .`

` docker run -d -p 8080:8080 -t  {image-name}`

## Swagger API Documentation ##

`http://localhost:8080/swagger-ui.html`


## Testing

Below functionalities and edge cases are unit tested and documented inside the application

+ Initialize Game

+ Play Game

+ Create Board

+ Distribute Stones

+ Perform Game rules

+ Determine winners
