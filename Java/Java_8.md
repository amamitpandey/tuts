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
no access modifier, no name, no castType, no signature and optional return type. also called lamda expresion. 
  
### Functional interface(FI) : 
Ex : 
// expected return type
Runnable() ⇒ run()
// use to start thread, don't expected return type
Callable() => call()

Comparator => compareTo()

ActionLister ⇒ actionPerformed()

#### In interface or functional interface, we can use default and static method.
* @functionalInterface // for check Functional interface, it’s optional.it'll throw the error if found more abstract method

```
class TestClass {

   public static void main(String[] args) {
       MyInterface myInterface = (a, b) -> a + b;
       MyInterface myInterfaceForSubtract = (a, b) -> a - b;
       System.out.println("test " + myInterface.myOpreation(1, 2));
       System.out.println("test1 " + myInterfaceForSubtract.myOpreation(5, 2));
   }
}

@functionalInterface
interface MyInterface {
   // by default interface has abstract method
   public int myOpreation(int a, int b);

   // we can add more default method, optional
  
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

map: The map method is used to returns a stream consisting of the results of applying the given function to the elements of this stream.<br />
List number = Arrays.asList(2,3,4,5);
List square = number.stream().map(x->x*x).collect(Collectors.toList());

filter: The filter method is used to select elements as per the Predicate passed as argument.
List names = Arrays.asList("Reflection","Collection","Stream");
List result = names.stream().filter(s->s.startsWith("S")).collect(Collectors.toList());

sorted: The sorted method is used to sort the stream.
List names = Arrays.asList("Reflection","Collection","Stream");
List result = names.stream().sorted().collect(Collectors.toList());

Terminal Operations:
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


### Anonymous Inner class:
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

### Default method vs static method in interface :
- both method have body
- static method can't override but default can
- for use default method, need to create new instance like normal method, but in case of static method we can directly use like MyInterface.custStaticMethod()
- staic method use as a utility or helper, like isValidate()
```
static void isAmtMorethanZero(int i1){
retrurn i>0; }
```

```
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
```
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

### Optional:
introduced in java 8, better to handle to null exception, follow function style.
we have Optional.empty() - method to check but it'll not throw exception. if we are getting collection with null we can process it with.

there are some method:
- Optional.of("amit"): don't use of if null value expected throw nullpointException
- Optional.ofNullable(value): use of null value expected, don't throw nullpointerException.




## Refrence: Durga soft: https://www.youtube.com/watch?v=f4QZ12wMQO8&list=PLd3UqWTnYXOk5KW5drfvORu0uS4n5LTGU

## Code practice
```
import java.util.*;
import java.util.function.Function;
import java.util.stream.Collectors;
import java.util.stream.IntStream;
import java.util.stream.Stream;

public class Java8 {
    public static void main(String[] args) {
        int[] intArray = {1,2,33,2};
        List<Integer> intList = Arrays.asList(1,3,3);
        List<Integer> intList1 = new ArrayList<>();
        intList1.add(2);
        intList1.add(5);

        // converting array to stream
        Arrays.stream(intArray).forEach(System.out::println);

        Comparator<Integer> integerComparator = (a, b) -> (b - a);
        // converting arrayList to stream
        // sorting in desending order
        intList.stream().sorted(integerComparator).collect(Collectors.toList());

        // direct using stream to print 1 to 20
        // seed means starting point
        Stream.iterate(1, x->x+1).limit(20).forEach(System.out::println);

        System.out.println("Filtering even nos");
        intList1.stream().filter(x->x%2==0).sorted().forEach(System.out::println);
        System.out.println("getting distinct");
        intList.stream().distinct().forEach(System.out::println);
        System.out.println("processing data using map");
        List<Integer> integers = intList.stream().map(x->x*3).collect(Collectors.toList());
        integers.forEach(System.out::println);

        // we can use filter instead of supplier, consumer, predicate

        //sum
        System.out.println(intList.stream().mapToInt(x->x).sum());
        System.out.println(Arrays.stream(intArray).sum());
        System.out.println(intList.stream().reduce(0,(a,b)->a+b)); // 0 is int so it'll return int otherwise return Optional[7]

        // add two array
        List<Integer> newStringList = new ArrayList<>();
        newStringList.addAll(intList);
        newStringList.addAll(intList1);
        System.out.println("demo of merger two array");
        System.out.println(newStringList);
        System.out.println("adding two array by concat");
        Stream.concat(intList.stream(), intList1.stream()).forEach(System.out::println);


        // get second highest no
        System.out.println(intList.stream().sorted(Comparator.reverseOrder()).skip(1).findFirst().get());


        // sort string based on string length
        List<String> stringList = Arrays.asList("name0", "name111","name2");
        stringList.stream().sorted(Comparator.comparing(String :: length)).forEach(System.out::println);


        // common element between two array
        List<String> stringList2 = Arrays.asList("name0", "name","name2");
        stringList.stream().filter(stringList2 :: contains).forEach(System.out::println);


        // reverse the words
        stringList.stream().map(word->new StringBuffer(word).reverse()).forEach(System.out::println);

        // reverse the array
        IntStream.rangeClosed(1,intList.size()).map(i-> intList.get(intList.size()-i)).forEach(System.out::println);

        // find the duplicates
        final HashSet<Integer> set0 = new HashSet<>();
        intList.stream().filter(x->!set0.add(x)).forEach(System.out::println);
        // find the duplicate word in string array
        HashSet<String> sList = new HashSet<>();
        stringList.stream().filter(x->!sList.add(x)).forEach(System.out::println);

        // Create a stream to generate Fibonacci numbers
        Stream.iterate(new int[]{0,1},f -> new int[]{f[1],f[0]+f[1]}) // Fibonacci logic: [a, b] -> [b, a+b]
                .limit(10)
                .map(f->f[0])
                .forEach(System.out::println);


        // split a sentance and reverse the string array
        String s1 = "My name is Amit";
        String[] stringList1 = s1.split(" ");
        IntStream.rangeClosed(1,stringList1.length).mapToObj(x->stringList1[stringList1.length-x]).forEach(System.out::println);




        //how to sort a object using java stream
        List<CustomModel> custList = new ArrayList<>();
        CustomModel customModel1 = new CustomModel();
        customModel1.setId(1);
        customModel1.setName("amit");
        CustomModel customModel2 = new CustomModel();
        customModel2.setId(5);
        customModel2.setName("pandey");
        CustomModel customModel3 = new CustomModel();
        customModel3.setId(2);
        customModel3.setName("amit");
        custList.add(customModel1);
        custList.add(customModel2);
        custList.add(customModel3);

        Comparator<CustomModel> custModelComparator = Comparator.comparingInt(CustomModel :: getId).reversed();
        custList.stream().sorted(custModelComparator).forEach(x-> System.out.println("id "+ x.getId()+" Name"+x.getName()));
        // if same name as groupby
        Map<String, List<CustomModel>> collect = custList.stream().collect(Collectors.groupingBy(CustomModel::getName));
        collect.forEach((item,list)-> System.out.println("item: "+item+" count "+list.size()));

        // Plindrome
        String string1 = new String("madam");
        System.out.println(IntStream.range(0, string1.length()).allMatch(i -> string1.charAt(i) == string1.charAt(string1.length() - i - 1)));

        // max() && min()
        System.out.println(intList1.stream().max(Integer::compareTo));
        System.out.println(custList.stream().max(custModelComparator)); // with a custom model

        // first no repeat word
        System.out.println(string1.chars()// string to stream
                .mapToObj(ch -> (char) ch) // convert string char
                .collect(Collectors.groupingBy(Function.identity(), LinkedHashMap::new, Collectors.counting()))
                .entrySet()
                .stream()
                .filter(x->x.getValue()==1)
                .map(x->x.getKey())
                .findFirst().get()
        );

        // print count of each word
        String string2 = new String("madam pandey");
        System.out.println(Arrays.stream(string2.split("")).collect(Collectors.groupingBy(Function.identity(), Collectors.counting())));

        // group by sample
        List<CustomModel> list = new ArrayList<>();

        list.add(new CustomModel(1,"02/01/2025","pencil"));
        list.add(new CustomModel(2,"05/01/2025","pen"));
        list.add(new CustomModel(3,"05/01/2025","copy"));


        list.stream().sorted(Comparator.comparing(CustomModel::getId)).forEach(x-> System.out.println(x.getId()+" "+x.getDate()));
        list.stream().collect(Collectors.groupingBy(CustomModel::getDate)).entrySet().stream()
                .forEach(x-> {
                    System.out.println(x.getKey());
                    x.getValue().forEach(y-> System.out.println(y.getId()+" "+y.getName()));
                });

    }


}


class CustomModel{

    int id;
    String name;
    String date;

    CustomModel(){}

    public CustomModel(int id, String date, String name) {
        this.id=id;
        this.date=date;
        this.name=name;
    }

    public int getId() {
        return id;
    }

    public void setId(int id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getDate() {
        return date;
    }

}



```







 


