Interview questions :
### Benefit of using spring boot:
* auto config like start config
* auto embeded server
* DB is added like H2
* Dev tool is enabled for quick running
* Actutor is available for monitoring purpose like health check
  
### IOC(Inversion Of Control):
Giving control to the container to create and inject instances of objects that your application depend upon, means instead of you are creating an object using the new operator, let the container do that for you. Inversion of control relies on dependency injection because a mechanism is needed in order to activate the components providing the specific functionality

The two concepts work together in this way to allow for much more flexible, reusable, and encapsulated code to be written. As such, they are important concepts in designing object-oriented solutions.

Example for Dependency injection

Previously we are writing code like this
```
Public MyClass{
 DependentClass dependentObject
 /*
  At somewhere in our code we need to instantiate 
  the object with new operator  inorder to use it or perform some method.
  */ 
  dependentObject= new DependentClass();
  dependentObject.someMethod();
}

//With Dependency injection, the dependency injector will take off the instantiation for us

Public MyClass{
 /* Dependency injector will instantiate object*/
 DependentClass dependentObject

 /*
  At somewhere in our code we perform some method. 
  The process of  instantiation will be handled by the dependency injector
 */ 

  dependentObject.someMethod();
}
```

The above process of giving the control to some other (for example the container) for the instantiation and injection can be termed as Inversion of Control

#### Type of Dependency Injection.

Constructor injection: This is the most common type of DI in Spring Boot. In constructor injection, the dependency object is injected into the dependent object’s constructor.

Setter injection: In setter injection, the dependency object is injected into the dependent object’s setter method

Field injection : In field injection, the dependency object is injected into the dependent object’s field.

You can read more on dependency injection and IOC in my answer :- You can find advantages and applications of the concepts here.
#### What is @AutoWiried? 
Kind fo DI to use another class element.

### put vs post vs patch method
put use for update info fully
Patch use for update only one field
Post use for create new info

### Context
Is just environment, scope where var method exit, can access by this keyword. 

### devtools use for hotload, normal restart time 9 sec but hotload time could be 2 sec

### dispatcherServlet  is responsible  for search controller and revert back
### dow is equivalent as repo like interaction with data base
### get data type:
// System.out.println(customUid.getClass());

### using HASH MAP object return multi type JSON
```

            Map<String, Object> finalData = new HashMap();
            finalData.put("type", "success");
            finalData.put("message", "User updated successfully");
            finalData.put("data", DataLoc);
            return finalData;
```
            
### using HASH MAP type genric/any return multi type JSON
```
// for define any type data type also called genric :  <T> T

            Map<String, T> finalData = new HashMap();
            finalData.put("type", (T) "success");
            finalData.put("message", (T) "User deleted successfully");
            finalData.put("data", (T) returnValue); // returnValue is kind of obj
            return (T) finalData;
```

        
### bean has inbuild default constructor with zero argument, don’t need to write construct in bean
```
Ex : 
public class Alpha {
}

public class Beta {
  public Beta() {}
}
```

// In Alpha the default constructor is implicit; in Beta it is explicit. Both have default public constructors as per the JavaBean spec


### DAO:
(data access object) is a kind of bean

### What are Bean Factory and Application Context?
both are spring container, ApplicationContext extends BeanFactory. BeanFactory provide basic and normal features and used in simple application.
In short, BeanFactory provides basic Inversion of control(IoC) and Dependency Injection (DI) features while ApplicationContext provides advanced features.

### What’s the difference Between @Controller, @Component, @Repository, @SpringBootApplication and @Service Annotations in Spring?
@component : it's bean, it's for general purpose, either we can use as repository, service or as mmodel for easy to use.
@controller : behave as a logic controller build for normal html, js whether @RestController by default return xml/json response.
@Repository : use with JPA interface for gather info form db, a persistence layer of connection 
@service :  Serice layer is use for write busineess logic, it's specific for bussiness logic purpose, we are getting more option like @transaction etc, more readble.   

### @SpringBootApplication : 
@Configuration to enable Java-based configuration like bean and package
@ComponentScan to enable component scanning like services, repository.
@EnableAutoConfiguration to enable Spring Boot's auto-configuration feature like dependency and libraries.

### What is @Primary and @Qualifier?
if you have two beans with same interface, then these anotation decide which will get more prefrence.
@qualifier will get more value. 
@Primary indicates that a bean should be given preference when multiple candidates are qualified to autowire a single-valued dependency.

@Qualifier indicates specific bean should be autowired when there are multiple candidates.
```
public interface BeanInterface {

    String getName();
}


public class Bean1 implements BeanInterface {
    @Override
    public String getName() {
        return "bean 1";
    }
}


public class Bean2 implements BeanInterface {
    @Override
    public String getName() {
        return "bean2";
    }
}

// Here is our service.

@Service
public class BeanService {

    @Autowired
    private BeanInterface bean; // it'll get error by say you havemore then one bean
}

```

```
// solution

@Bean("bean1")
@Primary
public BeanInterface bean1() {
    return new Bean1();
}
```

### Application context:
it handleer all kind or bean context at time creation, deletion.

## What is the default scope of a bean?
singleton is first and default, after that we have prototype, request(HTTP), session(HTTP), and application(HTTP) scopes

## @mockbean vs @mock
1. mockbean is part of spring framework used with @springboottest while mock is part of mockito framework used with @RunWith(MokitoRunner)
2. Mockbean intract with spring context but mock interat with java obj
3. both use for mocking/isolate of components, repository, services
4. mock used for only unit Test case while mockbean used for unit and integration testcase.
   
### Can you explain a simple flow in Spring MVC?
just explain Model view and controller, spring also support frontend and backend part 

### Spring boot layer
1. Presentation layer: handle all http requests like put, post
2. bussines layer: handle all bussiness logic
3. presistance layer: interacting with DB usign JPA
4. Database layer: crud operation

### Spring boot life cycle:
1. Application startup: use SpringApplication.run(), baiscally see main method and inside method. create applicationContext:add spring container, like IOC and BeanFactory
2. Enviroment Prepration: setup application.properites, many env properties files and enviromet variable files
3. Context creation: setup load bean, auto config, componenent scan
4. Bean inilization: DI, @PostCostruct, call beans, initialize custom bean
5. Application ready: ApplicationRunner bean run, applicationReadyEvent fired, now ready to serve request
6. Runnnig state: Tomcat accepting req and responding
7. Shuntdown: shutdown hook register, @preDestroy method call, ContextClose event is published.

       
### AOP:
Aspect oriented programming; it's concept like OOPs, maintain code quality, use to handle centrized logging sys, security and trasaction sys.

```
@Aspect
@Component // Make the aspect a Spring-managed bean
public class LoggingAspect {

    // This will run before the method execution
    @Before("execution(* com.example.service.*.*(..))") 
    public void logBefore(JoinPoint joinPoint) {
        System.out.println("Logging before method: " + joinPoint.getSignature().getName());
    }

    // This will run after the method execution
    @After("execution(* com.example.service.*.*(..))") 
    public void logAfter(JoinPoint joinPoint) {
        System.out.println("Logging after method: " + joinPoint.getSignature().getName());
    }

    // This will run around the method execution (you can control when the method is called)
    @Around("execution(* com.example.service.*.*(..))") 
    public Object logAround(ProceedingJoinPoint joinPoint) throws Throwable {
        System.out.println("Before method execution: " + joinPoint.getSignature().getName());
        Object result = joinPoint.proceed(); // Proceed with the method execution
        System.out.println("After method execution: " + joinPoint.getSignature().getName());
        return result;
    }
}
// after that need to config each file @EnableAspectJAutoProxy

```
### Caching in Spring Boot:
is one of the easiest ways to improve performance — especially for slow methods like database queries, remote API calls, or expensive computations.

multiple cache way like:
Simple (default): uses a ConcurrentHashMap
Ehcache, Caffeine
Redis, Hazelcast, etc.
- add dependecy : spring-boot-starter-cache
- enable in main:
```
@SpringBootApplication
@EnableCaching
public class MyApp {
    public static void main(String[] args) {
        SpringApplication.run(MyApp.class, args);
    }
}
```
```
@Service
public class ProductService {

    @Cacheable("products")
    public Product getProductById(Long id) {
        simulateSlowService();
        return new Product(id, "MacBook Air");
    }

    private void simulateSlowService() {
        try {
            Thread.sleep(3000); // pretend it's a slow DB/API call
        } catch (InterruptedException e) {
            throw new IllegalStateException(e);
        }
    }
}
```
### Configure two DB in spring boot
- add both in application.yml
- create two config file with trasaction manager(@EnableTransactionManagement), add @primary with main DB and another config file don't add @primary








