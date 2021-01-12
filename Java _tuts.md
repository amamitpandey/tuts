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

## Basic Java code

```

public class CustomeClass {

   // it's like a constructor call by itself by call this class
   public static void main(String[] args) {
       System.out.println("consoling in Custom class main");
       // to call a static method don't need to create instance
       StaticMethod();
       // to call a static method need to create instance
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


