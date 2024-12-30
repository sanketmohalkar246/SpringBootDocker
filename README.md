# SpringBootDocker
# Spring Boot Application with Docker

This guide provides instructions to create, build, and run a Spring Boot application in a Docker container.

---

## Steps to Build and Run

1. **Create a Spring Boot Application**: Generate a Spring Boot project with required dependencies (e.g., Spring Web). Add a simple controller with an API, such as


   @RestController
   @RequestMapping("/api")
   public class SampleController {
       @GetMapping("/hello")
       public String sayHello() {
           return "Hello, Docker!";
       }
   } 

---
2. **Create a Dockerfile**: Add a Dockerfile in the project root with the following content:

FROM openjdk:17
EXPOSE 8080
ADD target/spring-boot-docker.jar spring-boot-docker.jar
ENTRYPOINT ["java", "-jar", "/spring-boot-docker.jar"]

---
3. **Build the Application JAR**: Package the Spring Boot application:

mvn clean package

---
4. **Build the Docker Image**: Navigate to the directory with the Dockerfile and run:

docker build -t spring-boot-docker.jar .

---
5. **Verify the Image**: Check if the Docker image was created:

docker image ls

---
6. **Run the Application in a Container**: Start the container and map the application to port 9090:
docker run -p 9090:8080 spring-boot-docker.jar

---
7. **Access the Application**: Open a browser and go to:

http://localhost:9090/message

---
8. **You should see the message**:

Hello, Docker!


















