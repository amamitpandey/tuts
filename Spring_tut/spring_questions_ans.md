InterView questions :
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

Type of Dependency Injection.

Constructor injection: This is the most common type of DI in Spring Boot. In constructor injection, the dependency object is injected into the dependent object’s constructor.

Setter injection: In setter injection, the dependency object is injected into the dependent object’s setter method

Field injection : In field injection, the dependency object is injected into the dependent object’s field.

You can read more on dependency injection and IOC in my answer :- You can find advantages and applications of the concepts here.

# Can you give few examples of Dependency Injection?
dependentObject= new DependentClass();
  dependentObject.someMethod();

# put vs post vs patch method
put use for update info fully
Patch use for update only one field
Post use for create new info

# What is Auto Wiring? 
Kind fo DI to use another class element


# What are the important roles of an IOC Container?
Initiate dependency obj for use using new key words

# Context
Is just environment, scope where var method exit, can access by this keyword. 

# What are Bean Factory and Application Context?
Can you compare Bean Factory with Application Context?

# BeanFactory and ApplicationContext:
both are spring container, ApplicationContext extends BeanFactory. BeanFactory provide basic and normal features and used in simple application.
In short, BeanFactory provides basic Inversion of control(IoC) and Dependency Injection (DI) features while ApplicationContext provides advanced features.

## What’s the difference Between @Controller, @Component, @Repository, @SpringBootApplication and @Service Annotations in Spring?
@component : it's bean, it's for general purpose, either we can use as repository, service or as mmodel for easy to use.
@controller : behave as a logic controller build for normal html, js whether @RestController by default return xml/json response.
@Repository : use with JPA interface for gather info form db, a persistence layer of connection 
@service :  Serice layer is use for write busineess logic, it's specific for bussiness logic purpose, we are getting more option like @transaction etc, more readble.   

### @SpringBootApplication : 
@Configuration to enable Java-based configuration like bean and package
@ComponentScan to enable component scanning like services, repository.
@EnableAutoConfiguration to enable Spring Boot's auto-configuration feature like dependency and libraries.

## What is @Primary and @Qualifier?
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

## Can you explain a simple flow in Spring MVC?
just explain Model view and controller, spring also support frontend and backend part 

## What is the default scope of a bean?
singleton is first and default, after that we have prototype, request(HTTP), session(HTTP), and application(HTTP) scopes

## @mockbean vs @mock
1. mockbean is part of spring framework used with @springboottest while mock is part of mockito framework used with @RunWith(MokitoRunner)
2. Mockbean intract with spring context but mock interat with java obj
3. both use for mocking/isolate of components, repository, services
4. mock used for only unit Test case while mockbean used for unit and integration testcase.

## Spring boot layer
1. Presentation layer: handle all http requests like put, post
2. bussines layer: handle all bussiness logic
3. presistance layer: interacting with DB usign JPA
4. Database layer: crud operation 






