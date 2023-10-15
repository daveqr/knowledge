# Spring Boot

* Use [Spring Initializer](https://start.spring.io/) to generate a project. This will create a zip, which you download and unzip.
* The class with the `@SpringBootApplication` annotation is the entrypoint. Run this class.
* [http://localhost:8080](http://localhost:8080) is the default address
* By default you will see a login page. Login is `user` and password is generated. You can find the password by looking for something like this in the console: `Using generated security password: a4ac90b4-4f00-4299-b33f-217e04c2e31f`
* This is basic authentication and should be changed for a real application
* To enable hot reload, add `devtools` to `build.gradle`
    ```groovy
     compileOnly("org.springframework.boot:spring-boot-devtools")
    ```
    And check `File –> Setting –> Build, Execution, Deployment –> Compiler –> Build Project Automatically` in Intellij. When you make a change, it will take a few seconds to reload.


## Cors config

```java
@Configuration
@EnableWebMvc
public class CorsConfig implements WebMvcConfigurer {

    @Override
    public void addCorsMappings(CorsRegistry registry) {
        registry.addMapping("/**")
                .allowedOrigins("*") // Set your allowed origins here
                .allowedMethods("GET", "POST", "PUT", "DELETE") // Allowed HTTP methods
                .allowedHeaders("*") // Allowed headers
                .maxAge(3600); // Max age (seconds) of the pre-flight request
    }
}
```