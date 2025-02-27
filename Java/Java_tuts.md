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
- enum: it's a class, use to save variable like string, integer, here we have some predefine fn to use condition, let say if we want return 1 for true and 0 for false.
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


**Sting pool is kind of memory allocation**
**String is blue print of array, store in array that why it's non-primitive**
**if we update it's save in heap memory**

```
Sting s1 = "test"; // save in stack memory
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
## Encapsulation 

is a like a capsule,container catain many chemical, element and serve all at a time.
Getter, setter is good example of encapsulation. Access modifier are makes role for data security.

## Interface

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
- checked, at compilation type
- unchecked, at runtime
- error, at runtime

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
Executor is a interface which manage or control thread, executor handle thread life cycle creating and terminating.
there are twomethod submit() and shutdown();

## Solid priciple
  S: Single responsibility principle
  O: Open-close principle
  L: Liskov Substitution principle
  I: interface segregation principle
  D: Dependency inversion principle

  Open-close Principle: Open to extend but close for modification, extend old and base class.
  
  Liskov substitution: Should be loosely couple, any time class can be remove sustitude code.
  
  Interface segregation principle: Keep interface small as possible, that can use anywhere, like conversion of data type.
  
  Dependecy inversion principle: Should be loosely couple, use dependecy injection instead of creating a new instance.
  

  
# Using int Instead Of String: 
public static void main (int[] args) : at starting jvm only accept String[]. If try than give - "please define the main method as: public static void main(String[] args)”

Alternative we can define another main :

public class IntArgsTest { 
public static void main(int[] args) { IntArgsTest iat = new IntArgsTest(args); } 
public IntArgsTest(int[] n) { System.out.println(n[0]); }; 

public static void main(String[] args) { int[] intArgs = new int[args.length]; for (int i : intArgs) { try { intArgs[i] = Integer.parseInt(args[i]); } catch (NumberFormatException e) { System.err.println("Failed trying to parse a non-numeric argument, " + args[i]); } } main(intArgs); } }

# Can a constructor be made final, abstract in Java? 
No, a constructor can’t be made final. A final method cannot be overridden by any subclasses.
# Can a constructor be made private in Java? 
Yes, to prevent use in subclass, can’t create instant from outsider class, use in design singleton pattern. 
# Type of polymorphism :
Overloading : method name will same but params will differ, if there is any mistake it’s give run time error.
Overriding : method signature, name, parameter will same, it can be overwritten. Give compile time error.   

# Loose coupling :

 In simple words, loose coupling means they are mostly independent. If the only knowledge that class A has about class B, is what class B has exposed through its interface, then class A and class B are said to be loosely coupled. ... The examples of Loose coupling are Interface,DI

# Difference between Inversion of Control & Dependency Injection

These are patterns to achieve loose coupling in java programming

DI(Dependency Injection):
Dependency injection is a pattern used to create instances of objects that other objects rely upon without knowing at compile time which class will be used to provide that functionality or simply the way of injecting properties to an object is called dependency injection.

We have three types of Dependency injection

Constructor Injection
Setter/Getter Injection
Interface Injection

Spring will support only Constructor Injection and Setter/Getter Injection.

### Garbage collection
This process remove unused/unreachble variable or object from heap memory to inhance the app performace. it's automatic process.

// can be remove two way Major: remove heap memory from JVM Minor: Remove obj for heap memory In java it's automatic but in C manually handle it, so Java is better in this case.

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

   
