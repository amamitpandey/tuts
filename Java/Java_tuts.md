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
- Volatile - maximum time variable use cache data, to use recent data of var we use these keywords.
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
  ## Singletone design
  
  - use for create only one instance 
  - use private constructor 
  - by default it generate on instance in jvm, if required or not
  
  - https://www.geeksforgeeks.org/java-singleton-design-pattern-practices-examples/
  - https://dzone.com/articles/singleton-in-java
  
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
  
  
  
