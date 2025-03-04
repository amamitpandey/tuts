# Java 8 features

## Benefit: 
Reduce the code, accept funtion concept, improve performace by using new hardware like octo processer.

1. Lamda expression
2. funtional interface
 * Funtion
 * predicate
 * consumer
 * supplier
3. stream api
4. static method in interface
5. default method in interface
6. method refrence & construtor reference by double colon(::) oprator 
7. date & time api

### Lambda expression:
 in java 8, for concise the code we use lambda expression, when we using this we need to implement it through a functional interface. Functional interfaces implement a single abstraction method(SAM).  

 // using thread with lambda expression

```
public static void main(String[] args) {
   Runnable runnable = () -> {
       for (int i = 0; i < 5; i++) {
           System.out.println(" runnable interface " + i);
       }
   };
   Thread t = new Thread(runnable);
   t.start();
   for (int i = 0; i < 5; i++) {
       System.out.println(" main method " + i);
   }
}
```

#### Anonymous function :
no access modifier, no name, no castType, no signature and optional return type.
  
### Functional interface(FI) : 
Ex : 
Runnable() ⇒ run()

Callable() => call()

Comparator => compareTo()

ActionLister ⇒ actionPerformed()

#### In interface or functional interface, we can use default and static method.
* @functionalInterface // for check Functional interface, it’s optional.

```
class TestClass {

   public static void main(String[] args) {
       MyInterface myInterface = (a, b) -> a + b;
       MyInterface myInterfaceForSubtract = (a, b) -> a - b;
       System.out.println("test " + myInterface.myOpreation(1, 2));
       System.out.println("test1 " + myInterfaceForSubtract.myOpreation(5, 2));
   }
}

interface MyInterface {
   public int myOpreation(int a, int b);
}

```
PreDefined functional interface :
Present in java.util.funtion.*

### Predicate : for check/test, it alway return boolean type true or false

Predicate <Integer> p = (i)-> i%2==0;
System.out.println("test case 1 "+ p.test(11)); // false
System.out.println("test case 2 "+ p.test(10)); // true


Predicate joining 
// and(), 
p1.and(p2).test(obj);
//or(),
p1.or(p2).test(obj);
// negate() means !=

### Function :
it take input type and return type

Function<inputDatatype, returnDataType>

```
Function<Integer, String> f = (i1) -> {
   if (i1 % 2 == 0)
       return "prime no";
   return "non prime no";
};
System.out.println("calling fn0 " + f.apply(10)); // calling fn0 prime no
System.out.println("calling fn1 " + f.apply(11)); //calling fn1 non prime no
// chaining them
Function<Integer, Integer> f1 = (i2) -> i2 * i2;
Function<Integer, Integer> f2 = (i2) -> i2 + i2;
System.out.println(f1.andThen(f2).apply(2));// 8, run f1 then f2
System.out.println(f1.compose(f2).apply(3));// 36, run f2 then f1
```
### Consumer :
It’s only take/consume input,but not return type
consumer<inputType>
```
Consumer<Integer> c = (i1) -> System.out.println("only print value "+i1);
c.accept(23); //only print value 23

```
### Supplier :
Not required any input but required return type for output considered as return type integer.

```
Supplier<Integer> s = () -> 5;
System.out.println(s.get()); // 5

```
### BiPredicate :
BiPredicate<Integer, Integer> bp = (a,b)->(a+b)%2 ==0;
System.out.println("bp 0 "+ bp.test(10,20)); // bp 0 true
System.out.println("bp 1 "+ bp.test(10,25)); // bp 1 false

### Stream API :
For processing the data, like file, modify data we use stream api.

Intermediate Operations:
<br />
map: The map method is used to returns a stream consisting of the results of applying the given function to the elements of this stream.<br />
List number = Arrays.asList(2,3,4,5);
List square = number.stream().map(x->x*x).collect(Collectors.toList());
<br />
filter: The filter method is used to select elements as per the Predicate passed as argument.<br />
List names = Arrays.asList("Reflection","Collection","Stream");
List result = names.stream().filter(s->s.startsWith("S")).collect(Collectors.toList());
<br />
sorted: The sorted method is used to sort the stream.<br />
List names = Arrays.asList("Reflection","Collection","Stream");
List result = names.stream().sorted().collect(Collectors.toList());
<br />
Terminal Operations:<br />
collect: The collect method is used to return the result of the intermediate operations performed on the stream.
List number = Arrays.asList(2,3,4,5,3);
Set square = number.stream().map(x->x*x).collect(Collectors.toSet());
forEach: The forEach method is used to iterate through every element of the stream.
List number = Arrays.asList(2,3,4,5);
number.stream().map(x->x*x).forEach(y->System.out.println(y));
reduce: The reduce method is used to reduce the elements of a stream to a single value.
The reduce method takes a BinaryOperator as a parameter.
List number = Arrays.asList(2,3,4,5);
int even = number.stream().filter(x->x%2==0).reduce(0,(ans,i)-> ans+i);
toArray
min()
max()

##### Some example
```
       int[] ints = {1,2,33};
        // converting array to stream
        Arrays.stream(ints).forEach(System.out::println);
        // converting arrayList to stream
        List<Integer> list = Arrays.asList(1,3,3);
        Comparator<Integer> integerComparator = (a,b) -> (b - a);
        list.stream().sorted(integerComparator).collect(Collectors.toList());

        // direct using stream to print 1 to 20
        // seed means starting point
        Stream.iterate(1,x->x+1).limit(20).forEach(System.out::println);

        List<Integer> intArray = new ArrayList<>();
        intArray.add(2);
        intArray.add(5);
        intArray.add(1);
        intArray.add(0);
        intArray.add(2);

        Stream<Integer> data = intArray.stream().sorted();
        System.out.println("Sorting array");
        data.forEach(System.out::println);
        System.out.println("Filtering even nos");
        intArray.stream().filter(x->x%2==0).sorted().forEach(System.out::println);
        System.out.println("getting distinct");
        intArray.stream().distinct().forEach(System.out::println);
        System.out.println("processing data using map");
        List<Integer> integers = intArray.stream().map(x->x*3).collect(Collectors.toList());
        integers.forEach(System.out::println);
        // we can use filter instead of supplier, consumer, predicate
```
Using filter :
```
ArrayList<Integer> al = new ArrayList<Integer>();
al.add(2);
al.add(4);
al.add(3);
al.add(7);
al.add(10);
List l = al.stream().filter(x -> x >= 7).collect(Collectors.toList());
System.out.println(l);// [7,10]

```
Using comparator in Stream

ArrayList<Integer> al = new ArrayList<Integer>();
al.add(2);
al.add(4);
al.add(3);
al.add(7);
al.add(10);
Comparator<Integer> c = (i1,i2)->(i1>i2)?-1:1;
List l = al.stream().sorted(c).collect(Collectors.toList());
System.out.println(l); // [10, 7, 4, 3, 2]

```
al.stream().forEach(System.out :: println); // for printing the obj
```

Anonymous Inner class:
A interface where we can rewrite/override interface code, it’s create new instant and within that we can write the code, e.g
Runnable r = new Runnable(){
...
}

Runnable r = new Runnable() {
   @Override
   public void run() {
       for (int i = 0; i < 5; i++) {
           System.out.println("running runnable");
       }
   }
};
Thread t = new Thread(r);
t.start();

# using Lambda expression

Runnable r = () -> {
   for (int i = 0; i < 5; i++) {
       System.out.println("running runnable");
   }
};
Thread t = new Thread(r);
t.start();

Default method and static method in interface :

class TestClass implements I1{

   public static void main(String[] args) {
       TestClass t = new TestClass();
       t.defaultMethod();
       I1.staticMethod(); // for calling static method
   }
   // for override
   public void defaultMethod() {
       System.out.println("defaultMethod updated");
   }
}

interface I1 { 
   default void defaultMethod() {
       System.out.println("defaultMethod");
   }

   static void staticMethod() {
       System.out.println("staticMethod");
   }
}

### Method reference and consturctor reference : 
Method reference: is introduce in java 8, use with lamda expression, use for short code ex: (sysytem.out :: println)
where consturctor reference, we use "new" keyword like StringBuilder::new.
For code reusability

Restriction : can’t pass value
Public void m1() // no argument 
Public void run() // no argument 
```
public static void main(String[] args) {
   staticCustomMethod(); // normal call
   TestClass : staticCustomMethod(); // direct call by method reference
   TestClass testClass = new TestClass();
   CustomInterface customInterface = testClass :: nonStaticCustomMethod; // class reference
   customInterface.say();
}

interface CustomInterface {
   void say();
}

public static void staticCustomMethod(){
   System.out.println("staticCustomMethod");
}

public void nonStaticCustomMethod(){
   System.out.println("nonStaticCustomMethod");
}

```




## Refrence: Durga soft: https://www.youtube.com/watch?v=f4QZ12wMQO8&list=PLd3UqWTnYXOk5KW5drfvORu0uS4n5LTGU







 


