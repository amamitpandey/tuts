
# Java tuts

**Benefit of java**

- Performance - compilable language, use multi thread
- Security - secure it’s use JVM everything run within virtual machine
- robust/stronage - use garbage collector, auto remove unnecessary data
- Error handler - technically specific error handle rather than others language.  

JDK(java development kit) = JRE + additional lib
JRE(Java runtime Environment ) = JVM + operating system + other run environment.
** we can create a own JVM by using standard oracle/sun definition

**Java workflow**

Java code -> compiler -> java byte code (.class) -> JVM(interpreter+JIT) -> OS -> run
Code compile twice:
1. first time compile while running JAVAC part of JRE
2. Second time compile while JIT, JIT compile w.r.t OS and processer based. then code run at machine.

## Basic Java code

```

public class CustomeClass {

   // it's like a constructor call by itself by call this class
   public static void main(String[] args) {
       System.out.println("consoling in Custom class main");
       // to call a static method don't need to create instance
       StaticMethod();
       // to call a non static method need to create instance
       // first call call then obj or method
       CustomeClass customeClassObj = new CustomeClass();
       customeClassObj.NonStaticMethod();
   }

   public static void StaticMethod() {
       System.out.println("StaticMethod");
   }

   public void NonStaticMethod() {
       System.out.println("NonStaticMethod");
   }
}

``` 
## Access modifier 

- Default - if it’s blank, only access from package
- Public - it can be access in the world
- Private - only access from package
- Protected - it can access by sub class like number and double

## Non access modifier

- Static - create a instance and call method by class object for class, for variable treat as const
- Final - like const can’t change the value
- Abstract - calling an existing method of super call in sub call,need to declare both sub class and method as abstract.   
- Synchronised - threads work parallelly to make them work sync, use these keywords.   
- Volatile - maximum time variable use cache data and return old data, to use recent data of var we use these keywords. if we use multi thread and we want every thread updated value so use this. it'll not block current state. eg final volatile string s1="string";
- transient:  keyword is used to avoid serialized process, so it does not transmit over the network or file or JSON, like password has senstive data, we don't want share with any except db. eg: private transient String password;
- enum: it's a class, use to save variable like string, integer, here we have some predefine fn to use condition, short for enumeration, it's only read only, don't have remove fn, let say if we want return 1 for true and 0 for false.
  generally we use for switch cases.
  ```
  enum condEnum{
  true(1);
  false(0);}
  ```
  


  See below for diffrence between final and static, usually used with both static fineal

## primitive and non-primitive

Primitive is predefined data type like - String, int, double.
Non-primitive is user define data type like student bean.

## there is two way for serialize data

- first using getter and setter
- Second by using class and constructor
```

Name name = new Name("FirstName", "LastName"); // storing/setting data
System.out.println("Name is " + name.firstName + " " + name.LastName);// getting data

class Name {
   String firstName;
   String LastName;

   Name(String first, String second) {
       this.firstName = first;
       this.LastName = second;
   }
}

```

## Variable conversion
```
Explicit conversion :
double d = 10d
integer i = (int) d;
Data conversion
String s = ”343”;
integer i = interger.parseof(s)
```

## call by value : calling/invoking a method by passing argument 

## Method overloading is the same as polymorphism. 

## implement vs extends
```

public interface ExampleInterface { 
public void doAction(); 
public String doThis(int number); 
} 

public class sub implements ExampleInterface { 
public void doAction() { 
//specify what must happen 
} 
public String doThis(int number) {
 //specify what must happen } 
}

now extending a class
 
public class SuperClass { 
public int getNb() { 
//specify what must happen return 1; 
} 
public int getNb2() { 
//specify what must happen return 2; 
} } 

public class SubClass extends SuperClass { 
//you can override the implementation 
@Override 
public int getNb2() { 
return 3; 
} }

in this case
 
Subclass s = new SubClass(); 
s.getNb(); //returns 1 
s.getNb2(); //returns 3 

SuperClass sup = new SuperClass(); 
sup.getNb(); //returns 1 
sup.getNb2(); //returns 2
```

## Declare a Array
```
int a[] = new int[5];
// Assign a array value
int a[] = { a, b, 3, 4 }; 
// Multidimensional Array
int b[][] = {
{1,2},
{3,4}
}
```

**Mutable -> variable, immutable - > const**


**Data type String vs StringBuffer vs StringBuilder**

** String is primitive/predefined data type whether StringBuffer and StringBuilder are class define
StringBuffer and StringBuilder has more flexibility to update like reverse(), capacity etc
StringBuffer is useful in case of threading.

**Integer vs int :**

Integer is class drive or wrapper class of int, Integer has more flexibility.  
 
**chaining call of constructor**
```
class TestClass {
   String name;
   int age;

   TestClass() {
       String stringNor = "dssds";
       StringBuffer stringBuffer = new StringBuffer("Happy");
       stringBuffer.reverse();
       System.out.println("stringBuffer " + stringBuffer);
       StringBuilder stringBuilder = new StringBuilder("Happy");
       stringBuilder.reverse();
       System.out.println("stringBuilder " + stringBuilder);
   }

   TestClass(String name) {
// calling next constructor 
       this(name, 25);
   }

   TestClass(String nameArg, int ageArg) {
// updating global value
       this.name = nameArg;
       this.age = ageArg;
   }

   public static void main(String[] args) {
// calling without params
       TestClass testClass = new TestClass();
       System.out.println("constructor chaning of testClass" + testClass.name + " " + testClass.age); // output testClass null 0
// calling with params
       TestClass testClass1 = new TestClass("dude");
       System.out.println("constructor chaining " + testClass1.name + " " + testClass1.age);
// output testClass dude 25
   }

}
```


## String pool:
is kind of memory allocation area where string literal (a string enclosed in double quotes like "hello") stores. JVM checks if same string already there then just share the refferance to another varible and improve the perfomance and save the heap memory.

```
public class StringPoolExample {
    public static void main(String[] args) {
        String s1 = "Hello";
        String s2 = "Hello"; // This will refer to the same object as s1

        System.out.println(s1 == s2); // Output: true (same reference)

        String s3 = new String("Hello"); // Explicitly creates a new string object
        System.out.println(s1 == s3); // Output: false (different reference)
    }
}
```
 
**String is blue print of array, store in array that why it's non-primitive**
**if we update it's save in heap memory**

```
String s1 = "test"; // save in stack memory
s1="test1"; // save in heap memory

```
## String vs String Buffer vs StringBuilder :

- String take less memory but give less option.
- String buffer has more option like, replace,reverse rather than string, most case use in threads, but slow.
- StringBuilder is good option than String, option like, replace, reverse but its is not useful in threads. 

**this**  keyword refer current class, current method like Javascript

## OOPS has four piller : PI EA

P : polymorphism
I : inheritance 
E : Encapsulation
A : abstraction

## Inheritance example
```
public class TestInheritance extends Car {
   public static void main(String[] args) {
       // can't call static class to non static class, need to static
       // carRun();
       TestInheritance testInheritance = new TestInheritance();
       testInheritance.carRun();
   }

   @Override // in latest version it's removed
   public void carRun() {
       System.out.println("car Run "+tiers);
       tiers = 22;
       System.out.println("after update car Run "+tiers);
   }


}

class Car {
   public int tiers = 4;
   public int doors = 4;
   public void carRun() {
       System.out.println("car Run");
   }

```
## inheritance use extends to call parent class.

**Inheretance type** 
- single a->b
- multi a->b, a->c
- multi level : a->b->c

**super keyword**
like this refer current method or current class, like super refer just parent class

```
    public void printSuper(){
        // car is super class for this method
        System.out.println("example of super key word" + super.tiers); // example of super key word 4
    }
    
    class Car {
    public int tiers = 4;
    }
 ```
### association, aggregation and composition 
Assocation is brother of inheritace, we are reusing of code, using dependenc injection or creating new instance touse this feature. part of oops concept
inheritance use (is-a)/blood relation use extends keyword, while Association use (has-a) try to use loose couple things.
- Association
   - aggregation (weak bond)
   - composition ( strong bond)
Example: Car class
            - musicPlayer, follow aggregation, both are independable, loss couple
            - Engine, follow composition, both are tighly couple, egine made for special model   

 ## final keyword
 - final class/variable can't modify, same or from another class 
 - final class are not extendble/inheritance 
 - final method can't override/update
 - can't use by another class, used only in same class
 - Preffered for more security otherwise not reccomended 
 
 ## final vs static
 - in same same class can't modify
 - from another class static variable are modifilable but final can't.
 - Static used for memory sharing, it'll create a new/copy a object and work
 - Static use take adavantage of inheritance. 
 
 ```
public class TestInheritance extends Car {

    public static void main(String[] args) {
        TestInheritance testInheritance = new TestInheritance();
        System.out.println("staticVar"+ testInheritance.staticVar);
        testInheritance.staticVar = 222;
        System.out.println("staticVa updated "+ staticVar);
        System.out.println("finalVar "+ testInheritance.finalVar);
        //testInheritance.finalVar = 333; // give compiler error
        System.out.println("finalVar updated "+ testInheritance.finalVar);
    }

}

class Car {
    final int finalVar = 20;
    static int staticVar = 30;
}

// output

staticVar30
staticVa updated 222
finalVar 20
finalVar updated 20


``` 
## Asbtract 

Abstract data means hide data what required just give same thing, like doctor required only name and age, not educational details
**interface is 100% abstract**
**class is 0-100% abstract depending on declaration** 

```

    public static void main(String[] args) {
         ...
        TestAbstractionClass car1 = new TestAbstractionClass();
        car1.printName();
    }
 
class Car {
    final int finalVar = 20;
    static int staticVar = 30;
}

class TestAbstractionClass extends AsbtractClass{
    static int staticVar = 30;
    void printName(){
        System.out.println("Print name");
    }
}

```
### Encapsulation 

is a like a capsule,container catain many chemical, element and serve all at a time.
Getter, setter is good example of encapsulation. Access modifier are makes role for data security.

##@ Interface

is a specification/structure, work as a inheritace.

```
interface Vehicle extends BMW,Plan{
    default public void drive(String name){
        System.out.println("drive name"+name);
    }
}

interface BMW {
    public void drive(String name);
}

interface Plan {
    int wheels= 10;
    default String returnName(String name){
        System.out.println("returnName "+name);
        return name;
    }
}

in main()
...
        TestInheritance vehicle = new TestInheritance();
        System.out.println("checking interface "+ vehicle.wheels);
        vehicle.drive(" fgf");
        vehicle.returnName("returnName");
...

//output
checking interface 10
drive name fgf
returnName returnName
```

## importing one package to another
import com.test.* // calling all classes within this package
import com.test.specificClass

## Error handler
- checked, at compilation type ex: IOexception, FileNotFoundException, SQLexception
- unchecked, at runtime ex: nullpointerexception, airthmeticexception

**to handle runtime error, can use try and catch or throws an throw**

### Try and catch

```
    int devider = 25, devident = 0;

    public static void main(String[] args)  {
        ErrorHandlerTest errorHandlerTest = new ErrorHandlerTest();
        errorHandlerTest.usingTryCatch();
        ...
        
        
            public void usingTryCatch() {
        try {
            System.out.println("print int try block " + devider / devident);
        } catch (Exception e) {
            System.out.println("print int catch block " + e);
        }
    }
    
```

### throws and throw

- throws used to wirte with method signature while throw write inside of method.

```
    int devider = 25, devident = 0;

    public static void main(String[] args)  {
        ErrorHandlerTest errorHandlerTest = new ErrorHandlerTest();
        try {
            errorHandlerTest.usingUnhandleException();
            errorHandlerTest.usingTryThrowsAndThrow();
        } catch (Exception e) {
            e.printStackTrace();
            System.out.println("main exception " + e);
        }
    }
    
    private void usingUnhandleException() throws InterruptedException {
        Thread.sleep(10000);
        System.out.println(" usingUnhandleException ");
    }

    private void usingTryThrowsAndThrow() throws Exception{
        if (devident == 0) {
            System.out.println("main exception 1--"+ devident );
            // it's like a return statement, after it nothing excute 
            throw new Exception(" Run time error");
        }
    }
    
  ```
## Thread:

Summary of Thread States:
New: Thread has been created but not yet started.
Runnable: Thread is ready and waiting for the CPU to run.
Blocked: Thread is blocked, waiting for a resource to be available.
Waiting: Thread is waiting indefinitely for another thread's action.
Timed Waiting: Thread is waiting for a specific time limit.
Terminated: Thread has finished execution.

```
public class ThreadLifeCycleExample {
    public static void main(String[] args) throws InterruptedException {
        Thread t = new Thread(() -> {
            try {
                System.out.println("Thread running...");
                Thread.sleep(2000); // Timed Waiting
                System.out.println("Thread finished sleeping.");
            } catch (InterruptedException e) {
                System.out.println("Thread interrupted.");
            }
        });

        System.out.println("Thread state: " + t.getState());  // New
        t.start();  // Moves to Runnable state
        System.out.println("Thread state after start: " + t.getState());
        
        Thread.sleep(1000);  // Waits for 1 second

        System.out.println("Thread state during execution: " + t.getState());  // Runnable or Timed Waiting
        
        t.join();  // Wait for thread to finish
        System.out.println("Thread state after completion: " + t.getState());  // Terminated
    }
}
```
### difference between the methods sleep() and wait()

wait: it belongs to obj, use for pause, throw InterruptedException when another thread try to run it, it's interrupable.

Sleep: it belongs to class, use for delau in process, does not throw InterruptedException.

### Thread pool:
it's collection of thread worker, make sure fixed number of thread work parallel, no new thread create, instead of creating new assign task old thread to save memory and enhance the performance.  

### Diamond problem:
when we are using multiple inheritace using interface, this problem occur.
suppose, there are two interface implemented by one impl class and both have same method, then it'll generate compilar error.
to solve this issue either we can 1. override a method or use super keyword like interfaceName.super.methodName();

```
public class DiamondIssue {
    public static void main(String[] args) {
        left left = new left();
        left.methodName();
    }
}

interface InterfaceLeft{
    default void methodName() {
        System.out.println(" InterfaceLeft print");
    }
}
interface InterfaceRight{
    default void methodName(){
        System.out.println(" right ");
    }
}

class left implements InterfaceLeft,InterfaceRight{

    @Override
    public void methodName() {
        //System.out.println("left class"); // override the menthod
        InterfaceLeft.super.methodName(); // user super and default method concept
    }
}
```

### Executor:
Executor is a framwork used by interface which manage or control thread, executor handle thread life cycle creating and terminating.
there are two method submit() and shutdown();

### Solid priciple
  S: Single responsibility principle
  O: Open-close principle
  L: Liskov Substitution principle
  I: interface segregation principle
  D: Dependency inversion principle

  Open-close Principle: Open to extend but close for modification, extend old and base class.
  
  Liskov substitution: Should be loosely couple, any time class can be remove sustitude code.
  
  Interface segregation principle: Keep interface small as possible, that can use anywhere, like conversion of data type.
  
  Dependecy inversion principle: Should be loosely couple, use dependecy injection instead of creating a new instance.
  
### Interface vs abstraction class
Interface:
* don't have constuctor
* only contain public and abstract method(without body) which can be override
* support multiple inhritance by implement method

Abstraction:
* this behave like a class
* it's has constructor
* it's has all key access modifier like public, private
* it may contain narmal method with body(concern method) and abstract method without body
* don't support multi inhretance, just support single inhritance by extent keyboard. 
  
### Using int Instead Of String: 
public static void main (int[] args) : at starting jvm only accept String[]. If try than give - "please define the main method as: public static void main(String[] args)”

Alternative we can define another main :

public class IntArgsTest { 
public static void main(int[] args) { IntArgsTest iat = new IntArgsTest(args); } 
public IntArgsTest(int[] n) { System.out.println(n[0]); }; 

public static void main(String[] args) { int[] intArgs = new int[args.length]; for (int i : intArgs) { try { intArgs[i] = Integer.parseInt(args[i]); } catch (NumberFormatException e) { System.err.println("Failed trying to parse a non-numeric argument, " + args[i]); } } main(intArgs); } }

### Can a constructor be made final in Java? 
No, by default constructor can’t be override. and final method cannot be overridden by any subclasses so there are no use of it.

### Can a abstract method be made final in Java? 
no, because final method or var cann't be override.

### Can a constructor be made private in Java? 
Yes, to prevent use in subclass, can’t create instant from outsider class, use in design singleton pattern. 

### Type of polymorphism :
Overloading : method name will same but params will differ, if there is any mistake it’s give run time error.
Overriding : method signature, name, parameter will same, it can be overwritten. Give compile time error.   

### Difference between Inversion of Control & Dependency Injenction

Inversion of Control: is manage bean state to run the application with dependecy injenction use to archive loose coupling in java programming

### DI(Dependency Injection):
Dependency injection is a pattern used to create instances of objects that other objects rely upon without knowing at compile time which class will be used to provide that functionality or simply the way of injecting properties to an object is called dependency injection.

We have three types of Dependency injection

Constructor Injection
Setter/Getter Injection
Interface Injection

Spring will support only Constructor Injection and Setter/Getter Injection.


### Garbage collection
This process remove unused/unreachble variable or object from heap memory to inhance the app performace. it's automatic process.
// can be remove two way Major: remove heap memory from JVM Minor: Remove obj for heap memory In java it's automatic but in C manually handle it, so Java is better in this case.
Memory mangement are related to each other, memory mangment changes as per GC.
1. Serial GC: used to remove unused obj one by one, block/pause application, work with one core process, slow good for simple app.
2. Prallel GC: little fast than serial GC, use two core of process, prallel remove obj, use multi thread
3. CMS(concurret mark sweep):same work as praller GC, but faster, deprecated in java 9, removed in java 14, good for trading app, or real time app
4. G1GC: introduced in java 9, heap memory>4gb
5. ZGC(Z gen GC): introduced in java 11 and auto enable, less pause time, heap > 16GB
6. Shenandoah GC: introduced in java 12 and auto enable, less pause time.

### Memory mangement changes:
- Permgen optimization - java 7
- Stack and MataSpace memmory management - java 8
- G1GC - java 9
- ZGC - java 11
- SGC - Java 12

## Memory type:
Stack memory: it's static memory, variable starting for static keywords and declare method, stored in this memory, once worked finished in scope, JVM auto remove them, follow LIFO.
Heap memory: it's dynamic memory, hold/catche obj starting with new keywords, hold new created instance, work with GC
MataSpace: introduced in java 8, native memory, no limit of extended 
// legacy
PermGen: before in java 8, or upto java 7, part of heap memory, limit memory 


### outOfMemoryError:
When heap memory full, than we get this error
#### Causes:
1. Memory leakage: due to exiting refrence of obj, GC unable to removed them
2. using large data set like ArrayList, hashmap
3. Excessive new obj creation
#### Solution:
1. there are some tools like visualJVM, identify code block and optimize the code
2. increase heap memory size
3. enable garbage collection logging then identify the issue, optimize the code  

### Javabean:
* Mostly contains properties of variable, getter, setter. maintain by IOC, DI in spring
* State of bean: Instantiation(create by @component, @Service), DI(configure like autowired), Post-Initialization(setting all methid by @PostConstruct), Ready to use, and Destruction(by @preDestroy).
* scope of bean: The rule is create a bean every time of request, available for all application and after using bean destroy the bean in scope.

### POJO vs javabean
POJO: as name suggest (plain old java obj) is a old thing, don't provide setter, serialization others advace things
```
public class Person {
    private String name;
    private int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public int getAge() {
        return age;
    }
}

```
Javabean: advance version of POJO, support default constructor, getter, setter, serialization. 
```
import java.io.Serializable;

public class Person implements Serializable {
    private String name;
    private int age;

    // No-argument constructor
    public Person() {}

    // Getter and Setter methods
    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }
}

```
### Composite key: pair of tow parimary key form two table, like student_id+course_id, purpose is make a unique key in colume
in java, we can use @mbeddable and @EmbeddedId
```
@Embeddable
public class OrderId implements Serializable {
    private Long userId;
    private Long productId;

    // equals, hashCode, getters, setters
}

@Entity
public class Order {
    @EmbeddedId
    private OrderId id;

    private int quantity;
    // ...
}

```
in sql, we can use
```
CREATE TABLE orders (
    user_id INT,
    product_id INT,
    order_date DATE,
    quantity INT,
    PRIMARY KEY (user_id, product_id)
);

```


### class loading process:
JVMuse to load by below process
1. loading: try to load all package and libraries internal or external
2. linking: in this process JVN try to preparation, varification and resolve, custome class or written class
3. initialization: start the application.

### class loading order:
1. Bootstrap: add all basic libraries like Java.util, java.lang
2. Extension class loader: add all external libraries in jre/lib/ext like feignclient
3. application loader: it load all class written by coder
4. custom class loader(optional): it add all additional classes like server config, DB config, or loose couple things.

### Java 17 benefit:
1. update JVM and garbage collection to improve compile, building and compile time.
2. interface is updated with sealed class
3. introduce with records and Pattern matching.
4. as normal we see it's enhance the performance, sercurity and LTS(long term support) time.
   
