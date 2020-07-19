# TextKernel Integration Test Assignment

## Used Technologies and Libraries

+ Java 11
+ Spring Boot 2+ (MVC)
+ Spring 5 (WebFlux)
+ Mongo DB (Embedded Reactive)
+ Junit 5
+ Lombok
+ Swagger
+ Maven 3+
+ Docker
+ Postman / Curl
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

## CURL Commands

Generate Access Token

`curl --location --request GET http://localhost:8080/accesstoken --header Authorization:"Basic dGVzdHVzZXI6P1kqYmJMN0dtWExU" `

Submit CV to be Parsed

`curl --location --request POST localhost:8080/submit?access_token={generatedToken} --form uploaded_file=@"{pathToCVFile}"
`

Get CV or Status

`curl --location --request GET localhost:8080/retrieve/{processId}?access_token={generatedToken}`

## Sample Run
`{
    "processId": "347b83e7-e283-48e8-9df3-c41d5f8c2fee",
    "profile": {
        "address": {
            "city": "",
            "postalCode": "",
            "streetName": "",
            "streetNumberBase": ""
        },
        "lastName": "Ntshinka",
        "firstName": "Andiswa"
    }
}`

## Design Choices and Basic Algorithms

The application is written in reactive programming using Spring WebFlux framework and embedded reactive MongoDB.
For security Basic Authentication and URL Based token (Json web token) authentications are implemented. Once the application
runs it loads a mock user into database which will be used to perform basic authentication. After a successful GET call to /accesstoken a JSON Web Token with an expiration time will be generated. POST /submit call will take a multipart file (CV) and create a Process Object and return it's ID to the client while in the background it will send CV to CV Parser Service. Once CV parser complete it's job it will save CV into Database as JSON documents as well as update the corresponding Process object by changing its status from IN PROGRESS to COMPLETE. Finally, GET /retrieve/{processId} will return a JSON object according to the status of process Id.


## Gold
