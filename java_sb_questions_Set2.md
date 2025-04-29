Interview questions:
Core Java:
-	Difference between Encapsulation & Abstraction
-	What’s method hiding
-	Different types of Polymorphism
-	What’s Closeable Interface and usage. 
-	Can you change state of an object referenced by a final : yes,var is fix but obj can caontain dynamic value
-	Java parameters are passed by value or reference : passed by value but use referrance to pass
-	Difference between equal to operator (==) and equals() : == check refernce but equals check value
-	How can you modify a String : no, but we have string builder and string buffer to modify
-	Why String class has been made immutable in Java : for security and performance purpose, string may store password or filePath
-	What is finally : use with try,catch, finally(optinal), use for clean memory after work
-	Is finally always required in Java 8 : no - finally(optinal)
-	Which resources can be used in try-with-resources : filereader, stream, DB connection, Https connection
-	What is finalize : work with GC, auto clean some var, after java 9 deprecated replace with AutoCloseable interface 
-	What are the steps in Object creation
-	What happens with Class.forName method : load package or driver at runtime, part of java.reflection.util, like DB driver, Class<?> clazz = class.forName("com.example")
-	Can you explicitly destroy an object
-	What are the similarities between abstract class and an interface
-	Can we have concrete methods in Interface :yes after java 8
-	What’s enum & strict keyword
-	What’s transient & volatile keyword
-	What’s Marker Interface
-	What’s Serialization and how it works internally
-	Though Serializable is a Marker Interface without any methods, how does the JVM understands & does the serialization of the given object implementing Serializable interface?
-	How to read file and store its data in DB

Multithreading:
-	How to implement multithreading : use, new Thread(), extend thread or implement Runnerble, create it and using executor handle those
-	What’s synchronization 
-	Advantages & disadvantages of Synchronization: pros chain which are dependble resource, cons slow performance
-	How to implement synchronization without impact performance
-	What is thread deadlock. Explain with example: when two thread wait for same resouces 
- What’s ThreadLocalStorage class and its purpose: handle version and memory allocation of thread, provide isolation to work independent

Collections:
-	Different types of Collections
-	What all the Collections you used in the project or in your experience
-	What is Hashmap and how it works internally?
-	What’s Concurrent Hashmap and how it works?
-	Difference between Hashmap & Concurrent Hashmap?
-	What’s LinkedList and how it works
-	What collection will be used in the scenario for simultaneous read & add operation


ORM:
-	What’s ORM & advantages
-	What is a dialect in hibernate
-	What’s are the different mappings available in Hibernate with examples.
-	What’s POJO in Hibernate
-	What are the different states of the POJO in Hibernate


PL/SQL
-	What is the difference between varchar and varchar2
-	What is the purpose of NVL() function
-	What is the difference between primary key and unique key
-	How can we find current date and time in Oracle
-	What do you understand by database schema
-	What is a view
-	What is left outer join
-	What is right outer join
-	How to define trigger & its purpose
-	How to store data in DB
-	What’s optimistic & pessimistic locking
-	What’s versioning 

Spring Boot:
-	What is spring boot & its architecture
-	What are the advantages of spring boot
-	What’s the disadvantage of Spring boot
-	What’s the important configuration file in Spring boot
-	What is Spring Boot and What Are Its Main Features?
-	What Are the Differences Between Spring and Spring Boot?
-	What are Spring boot starter libraries?
-	What is Spring Initializr?
-	How to Disable a Specific Auto-Configuration?
-	What's the main configuration file in Spring boot application?
-	What's @Value annotation?
-	What do we define in @postConstruct method in Spring Initializer class?
-	What’s Actuator
-	How to migrate existing project to Springboot?
-	What are Springboot starters?
-	What is Starter Parent?
-	Compare Spring Boot vs Spring MVC?
- How can we find more information about Auto Configuration?
- Can you give examples of important starter projects?
- What are the different things that are defined in Starter Parent?
- How does Spring Boot enforce common dependency management for all its Starter projects?
- How can you add custom application properties using Spring Boot?
- What is @ConfigurationProperties?
- How do you have different configuration for different environments?
- How do you monitor web services using Spring Boot Actuator?
- What is a CommandLineRunner?

Spring MVC

-	How do you create an application context with Spring?
- Are Spring beans thread safe?
- How do you define a component scan in XML and Java Configurations?
- What are the other scopes available?
- What is the difference between XML and Java Configurations for Spring?
- What are the different kinds of matching used by Spring for Autowiring?
- How do you solve NoSuchBeanDefinitionException?
- What is CDI (Contexts and Dependency Injection)?
- Does Spring Support CDI?
- Would you recommed to use CDI or Spring Annotations?
- What are important Spring Modules?
- What are important Spring Projects?
- What is the simplest way of ensuring that we are using single version of all Spring related dependencies?
- Name some of the design patterns used in Spring Framework?
- What is Model 1 architecture?
- What is Model 2 architecture?
- What is Model 2 Front Controller architecture?
- Can you show an example controller method in Spring MVC?
- What is a ViewResolver?
- What is ModelAndView?
- What is a form backing object?
- How is validation done using Spring MVC?
- What is BindingResult?
- How do you map validation results to your view?
- What are Spring Form Tags?
- What is a Path Variable?
- What is a Model Attribute?
- What is a Session Attribute?
- What is a init binder?
- How do you set default date format with Spring?
- Why is Spring MVC so popular?
-	What’s Spring framework & advantages
-	What’s IOC(Inversion of Control)
-	Different ways of Dependency Injections
-	Difference between Constructor & Setter Injection
-	Difference between independent Singleton object & Spring Singleton Bean
-	What’s are different scopes of Spring Beans.
-	What’s autowiring & different modes
-	What's limitations of autowiring
-	What’s repository in Spring Data JPA
-	What’s Callback in DB
-	How to manage transactions in DB

Spring Data

- What is Spring Data?
- What is the need for Spring Data?
- What is Spring Data JPA?
- What is a CrudRepository?
- What is a PagingAndSortingRepository?

Database Connectivity - JDBC, Spring JDBC & JPA

- What is Spring JDBC? How is different from JDBC?
- What is a JdbcTemplate?
- What is a RowMapper?
- How do you define an entity in JPA?
- What is an Entity Manager?
- What is a Persistence Context?
- How do you map relationships in JPA?
- What are the different types of relationships in JPA?
- How do you define One to One Mapping in JPA?
- How do you define One to Many Mapping in JPA?
- How do you define Many to Many Mapping in JPA?
- How do you define a datasource in a Spring Context?
- What is the use of persistence.xml
- How do you configure Entity Manager Factory and Transaction Manager?
- How do you define transaction management for Spring – Hibernate integration?
  
Junit:
-	What’s Mockito framework
-	How will you implement Junit
-	What all the use cases you implemented using JUnits
-	How does Spring Framework Make Unit Testing Easy?
- How do you do mock data with Mockito?
- What are the different mocking annotations that you worked with?
- What is MockMvc?
- What is @WebMvcTest?
- What is @MockBean?
- How do you write a unit test with MockMVC?
- What is JSONAssert?
- How do you write an integration test with Spring Boot?
- What is @SpringBootTest?
- What is @LocalServerPort?
- What is TestRestTemplate?


AOP
- What are cross cutting concerns?
- How do you implement cross cutting concerns in a web application?
- If you would want to log every request to a web application, what are the options you can think of?
- If you would want to track performance of every request, what options can you think of?
- What is an Aspect and Pointcut in AOP?
- What are the different types of AOP advices?
- What is weaving?
- Compare Spring AOP vs AspectJ?
  
SOAP Web Services
- What is a Web Service?
- What is SOAP Web Service?
- What is SOAP?
- What is a SOAP Envelope?
- What is SOAP Header and SOAP Body?
- Can you give an example of SOAP Request and SOAP Response?
- What is a SOAP Header? What kind of information is sent in a SOAP Header?
- Can you give an example of a SOAP Header with Authentication information?
- What is WSDL (Web Service Definition Language)?
- What are the different parts of a WSDL?
- What is Contract First Approach?
- What is an XSD?
- Can you give an example of an XSD?
- What is JAXB?
- How do you configure a JAXB Plugin?
- What is an Endpoint?
- Can you show an example endpoint written with Spring Web Services?
- What is a MessageDispatcherServlet?
- How do you configure a MessageDispatcherServlet?
- How do you generate a WSDL using Spring Web Services?
- How do you implement error handling for SOAP Web Services?
- What is a SOAP Fault?

RESTful Web Services

- What is REST?
- What are the key concepts in designing RESTful API?
- What are the Best Practices of RESTful Services?
- Can you show the code for an example Get Resource method with Spring REST?
- What happens when we return a bean from a Request Mapping Method?
- What is GetMapping and what are the related methods available in Spring MVC?
- Can you show the code for an example Post Resource method with Spring REST?
- What is the appropriate HTTP Response Status for successful execution of a Resource Creation?
- Why do we use ResponseEntity in a RESTful Service?
- What is HATEOAS?
- Can you give an Example Response for HATEOAS?
- How do we implement it using Spring?
- How do you document RESTful web services?
- Can you give a brief idea about Swagger Documentation?
- How do you automate generation of Swagger Documentation from RESTful Web Services?
- How do you add custom information to Swagger Documentation generated from RESTful Web Services?
- What is "Representation" of a Resource?
- What is Content Negotiation?
- Which HTTP Header is used for Content Negotiation?
- How do we implement it using Spring Boot?
- How do you add XML support to your RESTful Services built with Spring Boot?
- How do you implement Exception Handling for RESTFul Web Services?
- What are the best practices related to Exception Handling with respect to RESTful Web Services?
- What are the different error status that you would return in RESTful Web Services?
- How would you implement them using Spring Boot?
- What HTTP Response Status do you return for validation errors?
- How do you handle Validation Errors with RESTful Web Services?
- Why do we need Versioning for RESTful Web Services?
- What are the versioning options that are available?
- How do you implement Versioning for RESTful Web Services?


CI/CD:
-	What is Jenkins
-	Why is Jenkins used
-	Difference between freestyle & pipeline jobs
-	What’s CI/CD pipeline 
-	How to configure CI pipeline
-	How to build, test and deploy the application with Jenkins

REST API: 
-	What is REST web services
-	What are HTTP methods supported by REST
-	What’s JAX-RS
-	What’s @RestController
-	Difference between SOAP & REST Webservices
-	What different output types supported by REST
-	How request payload from Client request gets mapped to @RequestBody object – Jackson library
-	Best practices for creating REST URI.
-	What’s @PathParameter
-	What’s are Idempotent methods
-	How to create/implement REST API
-	How to expose Restful webservice
  


Project Related Questions:
-	Tell brief about the current project & your roles & responsibilities
-	Explain the project architecture
-	How will you migrate a legacy application to the newer technologies?





