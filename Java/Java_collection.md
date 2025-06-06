## Java collections
Holding data like an array, we use collections frameworks. Here we have more control than arrays.
Array fixed in size that wise performance wise good but less control in terms of sort and another operation.
Array contains hemogenous(one data type) while ArrayList/collection contain hetrogenous.
in arrayList, we get more method for oprations like add(), addall(), reoveFirst(), removeLast().

collection: is a interface, used to represent a group of variable as single Entity, we used List, set, map in most of cases. It’s cloneable(I) and serializable(I) mean easy to transportable and copyable. 
collections: is a class, use for serch, retreive etc.
collection framework: it contains group of interface, classes.

## There are 9 keys in collections.

collection
List
Set
SortedSet
Navigable set
Queue
Map
SortedMap
NavigableMap

## collection(Interface)(1.2 v)
### List (Duplicate & indexing allowed)(1.0)
-- ArrayList(1.2v)
-- LinkedList(1.2)
-- vector(1.0)(legacy list)
    --- stack (part of vector)
 
### Set (Duplicate & indexing not allowed)(1.2)
-- HashSet (1.2)
   -- LinkedHashSet(1.4)
   -- SortedSet(indexing allowed)(1.2)
	-- navigableSet(1.6)
		-- tree set(1.2)(heterogeneous data/ any data not allowed)
### Queue(1.5)
-- PriorityQueue
-- BlockingQueue
   -- PriorityBlockingQueue
   -- LinkedBlockingQueue
    	
## Map(I)(use KayPair)(1.2)(not comes in collection)
-- HashMap
	--- ConcurrentHashMap
-- LinkedMap
-- WeakHashMap
-- IdentityHashMap
-- HashTable(Legacy)(1.0)
--- properties
--- dictionary 

## Sorting : comparable(default) and comparator(custmizable)
## Cursors : Enumerator, iterator, ListIterator // getting object one by one
## Utility class : Collections, Arrays

*(heterogeneous data/ any data not allowed in treeSet and treeMap)
*(only AL and vector use Random Access)
* converting non-synchronized to synchronized
List l = Collections.synchronizedList(ArrayList arr);
List l = Collections.synchronizedSet(Set s);
List l = Collections.synchronizedMap(Map m);

## Collection

Default method in collection
.add(Object o)
.addAll(Collection c)
.remove(Object 0)
.removeAll(Collection c) // except c remove all
.clear()
.reatianAll(Collection c)
.isEmpty()
.size()
.contains(Object o)
.containsAll(Collection c)

// collection to array
Object[] a = c.toArray


## List 
Is child interface of collection, duplicate and indexing allowed 

### ArrayList : it’s good for retrieving/getting data. Indexing and duplicate are allowed. Default size is 10. Use Random Access, means get 1 and last element at same time.

Worst case : need swift all elements for insertion or deletion time, so its takes a lot of time.   

After completing 10th element new capacity will be = (currency capacity * 3/2) +1 
 
```
// initial constructor
List arr = new ArrayList();
arr.add("A");
arr.add("B");
arr.add("a");
arr.add(10);
arr.add(null);
arr.remove(1); //index wise
arr.set(2,"upadated a"); //index wise update value for replace value
System.out.println(arr);
System.out.println("Get first index where 'A' exit " + arr.indexOf("A"));
System.out.println("Get first Last where 'A' exit " + arr.lastIndexOf("A"));
System.out.println("Get object index " + arr.get(1));

// ArrayList Constructor or Declaration 
List arr = new ArrayList();
List arr = new ArrayList(int initialCapacity ); 
List arr = new ArrayList(Collection c);
```



### Difference between ArrayList and Vector
ArrayList
Every method present in arrayList are non synchronized
Work with multiple threads
Use multi thread, performance wise good
Introduced in 1.2
Vector
Synchronized
At a time only one thread works 
Use one thread at a time, performance wise not good
1.0 v 

### LinkedList
Useful for if frequent operation is add and remove at middle or any where. Worse for retrieving data means return first fast but last element takes times. First object contain information of second object and third element contain info of third element and vice versa. 

### ArrayList vs LinkedList

#### ArrayList
* Good for retrieving data
* Not good for adding and removing
* Random access use for fast getting data
* Resizable and growable
#### LinkList
* Not good for getting the data
* Good for add and remove data
* Not use random access
* Doubly linked list



Specific methods : 
System.out.println("Get first index " + arr.getFirst());
System.out.println("Get getLast" + arr.getLast());
System.out.println("Get removeFirst " + arr.removeFirst());
System.out.println("Get removeLast " + arr.removeLast());

Constructor :
LinkedList arr = new LinkedList();
LinkedList arr = new LinkedList(Collection c);

## Vector
Synchronized 
Thread safe( only one thread at a time)
Random Access means, take less time to retrieve data

Constructor
// initial constructor
Vector arr = new Vector();
// default capacity is 10
// if out of capacity, increased capacity = current capacity * 2, means double
Vector arr = new Vector( int initialCapacity ); // 1000 => 1005 => 1010
Vector arr = new Vector( int initialCapacity, int increasementUnit);
Vector arr = new Vector( Collection c);

## Stack(LIFO)
Stack s = new Stack()

Method : push(), pop()

## Cursor 
Enumeration : 
Only applicable for legacy class
Only readable not removable operation

Worst : 
More old method included means landy names

Methods : hasMoreElement(), nextElement(), addElement(i)


      Vector dayNames = new Vector();
      
      dayNames.add("Sunday");
      dayNames.add("Monday");
      dayNames.add("Tuesday");
      dayNames.add("Wednesday");
      dayNames.add("Thursday");
      Enumeration days = dayNames.elements();
      
      while (days.hasMoreElements()) {
         System.out.println(days.nextElement()); 
      }

### Iterator : 
Universal cursor
Read and remove

Limitation :
Not able to add element
Not able to replace element
It’s flow only forward direction

Method : hasNext(), next(), remove()

```
        ArrayList<String> list = new ArrayList<String>(); 
  
        list.add("A"); 
        list.add("B"); 
        list.add("C"); 
        list.add("D"); 
        list.add("E"); 
  
        // Iterator to traverse the list 
        Iterator iterator = list.iterator(); 
  
        System.out.println("List elements : "); 
  
        while (iterator.hasNext()) 
            System.out.print(iterator.next() + " "); 
  
        System.out.println(); 
```

### ListIterator:
### Bi directional 
Add, remove, update features
It’s a child of an iterator.

Limitation :
Not a universal cursor
Available only for list collection

Method :
Forward method : 
hasNext(), next(), nextIndex()
Backward method :
hasPrevious(), previous(), peviousIndex()
Others:
remove(), set(), add()

```
            // Creating object of ArrayList<Integer> 
            ArrayList<String> arrlist = new ArrayList<String>(); 
  
            // adding element to arrlist 
            arrlist.add("A"); 
            arrlist.add("B"); 
            arrlist.add("C"); 
            arrlist.add("D"); 
  
        // print arrlist 
            System.out.println("ArrayList: "
                               + arrlist); 
  
            // using listIterator() method 
            ListIterator<String> 
                iterator = arrlist.listIterator(); 
  
            // Printing the iterated value 
            System.out.println("\nUsing ListIterator"
                               + " from Index 2:\n"); 
            while (iterator.hasNext()) { 
                System.out.println("Value is : "
                                   + iterator.next()); 
            } 
```



### Comparison of cursor

Enumeration                         Iterator                                            ListIterator
Applicable for Only for legacy      universal                                          List class
Movement Only forward               Only forward                                       Uni
Accessibility read                   read                                              remove
crud
Get it by
Vector dayNames = new Vector();
Iterator iterator = list.iterator(); 
ListIterator<String> 
                iterator = arrlist.listIterator();
Methods
2 methods
hasMoreElement()
nextElement()
3 methods
hasNext()
next()
remove()
9 methods
hasNext(), 
next(), nextIndex()
hasPrevious(), previous(), peviousIndex()
remove(), set(), add()
Introduces version
1.0v
1.2v
1.2v


### Set
HashSet :
Is child interface of collection, Best for searching duplicate allowed indexing are not allowed. Best for sorting, If duplicated found return false not exception

```
//## initial constructor
HashSet arr = new HashSet();
//## default capacity is 16
//## - fill ratio 0.75 or 75%, means after filling 75% it's auto generate size
//## like after filling 12th position increase size
//HashSet arr = new HashSet(20); // 20 is initial capacity
//HashSet arr = new HashSet(20, 10); // 20 is initial capacity, 10 fill ratio
//HashSet arr = new HashSet(Collection c); // 20 is initial capacity, 10 fill ratio

arr.add("A");
arr.add("A"); // return false
arr.add("a");
arr.add(10);
System.out.println(arr);

```
 

# SortedSet(I)
As name suggest it can store object sort order wise/name wise with preserved insertion order

Method : 
first(), 
last(), 
headSet()// above then upper,
tailSet(),
subSet()// below the params,
subSet(obj1,obj2)// within the limit

Example : 
{ 100,101,103,104,107,110,115 }
first() -> 100
last() -> 115
headSet() -> [ 100,101,103 ]
tailSet(103) -> [ 104, 107,110,115 ]
subSet(103,110) -> [103,104,107]
Comparator() -> null

Comparator() // describe underlying sorting technique, default Asending for int, default alphabetic for char. 

TreeSet :   
Store underlying data is balanced tree
Heterogeneous/any data not allowed 
Null allowed, but only once

Constructor 
```

   //## initial constructor
   TreeSet arr = new TreeSet();
   //## default use Natural sorting order(DNSO)
   //TreeSet arr = new TreeSet(Comparator c);
   //## create an customized order like salary-wise
   //TreeSet arr = new TreeSet(Sorted s);
   //TreeSet arr = new TreeSet(Collection c);

   arr.add("A");
   arr.add("A"); // return false
   arr.add("a");
   //arr.add(10); // Heterogeneous is not allowed
   System.out.println(arr); // output - > A, a // unicode -> 90, unicode -> 67 
  //## default use Natural sorting order(DNSO)

 ```

CompareTo
Return 3 value -ve, +ve, 0

// compareTo in build fn in comparable
System.out.println(       "test --> " + "A".compareTo("a"));  // -ve // -32
System.out.println(       "test --> " + "a".compareTo("A"));  // +ve // +32
System.out.println(       "test --> " + "a".compareTo("a"));  // 0 // 0
System.out.println(       "test --> " + "a".compareTo(null));  // nullPointer exception

Comparator(I) 
Use two method CompareTo() and equalTo()

Using of comparator for descending order
```
class TestClass {

   public static void main(String[] args) {
       //## initial constructor
       TreeSet arr = new TreeSet(new UseComparatorClass());

       arr.add(10);
       arr.add(0);
       arr.add(1);
       arr.add(1);// return false // duplicates not allowed

   }
}

class UseComparatorClass implements Comparator {

   //@Override
   public int compare(Object o, Object t1) {
       Integer integer1 = (Integer) o;
       Integer integer2 = (Integer) t1;
       if( integer1 > integer2 ){
           return  -1;
       }
       if( integer1 < integer2 ){
           return  +1;
       }
       else {
           return 0;
       }
   }
}
// output = [10, 1, 0]
```

Comparable
Comparator
For customized comparison Like for use stringBuffer, salary based sort, By default compare inbuild, Like int has ascending default natural sorting order, Comparator don’t use stringBuffer.
Use comparTo()
Use compare() and equals()
Use for primitive data String, integer
Use for non-primitive data, like string buffer
No need to import anything, by default it’s in java package
In java.utils.*



Set Comparison 
   
Property 
HashSet
LinkedHashSet
TreeSet
DataType
HashTable
LinkedSet+HashTable(Hybrid)
Balanced tree
Insertion order
not
Yes
no
Sorting order
no
no
yes
Heterogeneous
no
no
no
Duplicate data
no
no
no
null
yes(Only once)
yes(Only once)
yes(for empty tree only)


### NavigableSet
It’s child set of sorted sets defines several methods for navigation purposes.
It provides nearby values like train time around 10am.

SortedSet -> navigableSet(1.6v) -> TreeSet

method() : { 00:10, 1:45, 2:30, 5:30, 8:30, 9:15, 9:45, 10:15, 10:30, 11:45 }
floor(e) // return highest element is <= e, floor(10) //9:45
lower(e) // return highest element is >= e, floor(10) // 10:15
ceiling(e) // return highest element is >= e, ceiling(10) // 10:15
higher(e) // return highest element is >e, higher(10) // 10:15

PollFirst() // return and remove first element
PollLast() // return and remove last element
descendingSet()// return reverse Set


TreeSet t = new TreeSet();
t.add(1000);
t.add(3000);
t.add(2000);
t.add(4000);
t.add(5000);
System.out.println(t);
System.out.println(t.ceiling(2000));  // 2000
System.out.println(t.higher(2000));  // 3000
System.out.println(t.floor(3000)); // 3000
System.out.println(t.lower(3000)); //2000
System.out.println(t.pollFirst()); //1000
System.out.println(t.pollLast());  // 5000
System.out.println(t); // 2000,3000,4000


## Map
used to represent a group of key-value pair objects, map does not come in collection interface, dictionary and properties are not a child of map. 
Duplicate keys are not allowed but value allowed.
Each value is called Entry objects.
Heterogeneous / any data allowed.
Searchable and cloneable.

Method :
m.put(key, value)
m.putAll(map)
m.remove(key)
containKey(key)
containsValue(value)
isEmpty()
size()
clear()
Set set()
Collection values()
Set entrySet()

Entry(I) : Every key and value is entry.
Method :
getKey()
getValue()
getValues(obj)



Map
HashMap(1.2)
-- linked hashMap
- weakedHashMap(1.2)
- identityHashMap
- sortedMap(I)(1.2)
- -navigateMap(1.2)
-TreeMap(1.2)

HashMap
Underlying hashtable data structure 
Insertion order is not preserved
Best choice for search operation

Constructor() :
HashMap map = new Hashmap()
// default size is 16
// fill ration 0.75/75%
HashMap map = new Hashmap(initailCapcity)
HashMap map = new Hashmap(initailCapcity, fillration)
HashMap map = new Hashmap(Map m)


HashMap
HashTable
Not synchronized
synchronized
Insertion order preserved
Not preserved
Performance high
Low Performance
Key can null once,value can be null
Key can not null,value can’t be null
1.2
1.0(Legecy)

### ConcurrentHashMap:
it's good for work with multi thread, don't block the thread, multi thread can work together.
Inserting null objects is not possible in ConcurrentHashMap as a key or value.
When you need atomic operations like putIfAbsent, remove, or replace to avoid race conditions.



### LinkedList:
Used underlying data structure hybrid ( linkedlist + hashtable)
Insertion order preserved
Used for cache app
1.4v
Child class of hashMap
Difference between (==) and dotEqual(.equals()) 
(==) : compare address
.equals() : compare value e.g “s1”.equals(“s1”)

Integer I1 = new Integer(10);
Integer I2 = new Integer(10);

system.out.println(I1==I2) // false
system.out.println(I1.equals(I2)) // true

### IdentityHashMap :
this is kind of map which use (==) compare address for checking key compare 
```
Integer I1 = new Integer(10);
Integer I2 = new Integer(10);

HashMap m = new HashMap();
m.put(I1, “I1”)
m.put(I2, “I2”)
sop(m) // {10 = I2}

// For Identity map

IdentityMap m = new IdentityMap();
m.put(I1, “I1”)
m.put(I2, “I2”)
sop(m) // {10 = I1, 10 = I2} 
// inserted repeated value
```
### WeakHashMap:
As the name suggests it's a weak map. If the value of any key is null then the garbage collector removes that element but in case of any other map the garbage collector(gc) can’t.

```

class TestClass {

   public static void main(String[] args) {
       Temp k = new Temp();
       //## initial constructor
       WeakHashMap arr = new WeakHashMap();
       //HashMap arr = new HashMap();
       arr.put("k1",10);
       arr.put(k,null);
       k = null;
       System.gc();
       try {
           Thread.sleep(1000);
       } catch (InterruptedException e) {
           e.printStackTrace();
       }
       System.out.println(arr);
       // in case WeakHashMap print
       // finalized gc
       //{k1=10}
       // in case of HashMap, Hash map stronger than garage collector
       // print {temp=null, k1=10}
   }
}

class Temp {
   public String toString() {
       return "temp";
   }
   public void finalize() {
       System.out.println(" finalized gc ");
       // print when garbage collector works properly
       // in case wekHashMap garbage collector remove null valued element
   }
}

```

### SortedMap
methods():					// { 101=A, 103=B, 104=C, 107=D, 125=E, 136=F }
FirstKey() // {101=A}
lastkey() //{ 136=F }
headMap(107)  // { 101=A, 103=B, 104=C }
tailMap(125) // { 136 = F }
subMap(103,107) // { 104=C }
Comparator comparator() -> null // follow DNSO

### TreeMap
Data type - red black tree
Indexing not allowed
Duplicate key not allowed
Duplicated value allowed
Key store as default natural sorting
Key should be same data type and data type for value can be any
Only allowed only once

Constructor()

TreeMap t = new TreeMap()
TreeMap t = new TreeMap( Comparator c)
TreeMap t = new TreeMap(Map m)
TreeMap t = new TreeMap(SortedMap m)

t.put(100,”ZZZ”)
t.put(99,”ZZZ11”)
t.put(“sss”,”ZZZs1”)
sop(t) // { 99=ZZZ11,100=ZZZ }

### NavigableMap(1.6) :
Search should be based on key

TreeMap<String,String> t = new TreeMap<String,String>();
t.put("b", "banana");
t.put("c", "cat");
t.put("g", "gun");
t.put("d", "dog");
System.out.println(t); // DNSO // {b=banana, c=cat, d=dog, g=gun}
System.out.println(t.ceilingKey("c"));  // c
System.out.println(t.higherKey("e"));  // g
System.out.println(t.floorKey("e")); // d
System.out.println(t.lowerKey("e")); //d
System.out.println(t.pollFirstEntry()); // b=banana
System.out.println(t.pollLastEntry());  // g=gun
System.out.println(t.descendingMap());  // {d=dog, c=cat}
System.out.println(t); // {c=cat, d=dog}


### HashTable
Underlying data structure is hashtable
Insertion order not preserved
Heterogeneous/any type allowed for key/value
Thread safe
Synchronized
Best for search operation  
Based on hashcode key
Null not allowed for key value
Serializable and cloneable 
Default size is 11 and fill ratio - .75/75%
// working principle 
// print top to bottom, right to left
10
9
8
7
6
5  5=A,16=F
4
15=D
3
2
1
23=E
0


Hashtable hashtable = new Hashtable();
hashtable.put(5,"A");
hashtable.put(2,"B");
hashtable.put(6,"C");
hashtable.put(15,"D"); // 15 % 11 = 4
hashtable.put(23,"E"); // 23 % 11 = 1
hashtable.put(16,"F"); // 16 % 11 = 5
System.out.println(hashtable);

output
// {6=C, 16=F, 5=A, 15=D, 2=B, 23=E}


Constructor :

Hashtable hashtable = new Hashtable();
Hashtable hashtable = new Hashtable(intialSize);
Hashtable hashtable = new Hashtable(intialSize, fillRatio);
Hashtable hashtable = new Hashtable(Map m);



Sorting in Collection
List - > Collection.sort()
Map -> PriorityTreeMap()
Set -> TreeSet()

Collection.sort()

-	for default natural sorting order
- 	for customized sorting
- 	if there is null, give caseType Exception 

Collection.sort(List l, Comparator c)

ArrayList<String> al = new ArrayList<String>();
al.add("b");
al.add("c");
al.add("a");
al.add("d");
Collections.sort(al); // [a, b, c, d]
System.out.println("Normal sort" + al);
Comparator<String> c = (s1,s2) -> s2.compareTo(s1) ;
Collections.sort(al,c);
System.out.println("customized sort" + al); // [d, c, b, a]

Binary Search:
Before using this, we need to sort first then search.

For Collections

ArrayList<String> al = new ArrayList<String>();
al.add("b");
al.add("c");
al.add("a");
al.add("d");
// Collections.sort(al); // [a, b, c, d]
System.out.println(" Existing element search " + Collections.binarySearch(al, "c")); // 1 // if found, give +ve no with index
System.out.println(" Not existing element search " + Collections.binarySearch(al, "z")); // -5 // if not found, give -ve no with insertion order where item can be placed
Comparator<String> c = (s1,s2) -> s2.compareTo(s1) ;
Collections.sort(al,c);
System.out.println(" customized sort " + al); // [d, c, b, a]
Collections.reverse(al);
System.out.println(" Collections.reverse " + al); // [a, b, c, d]
Collections.reverseOrder(c); // reverse order for comparator
Collections.sort(al,c);
System.out.println(" Collections.reverseOrder " + al); // [a, b, c, d]


Arrays :

Sort:
Arrays.sort(al)
Arrays.sort(al, c);

Arrays.asList(iArray) : 
only for view purpose
Can’t add or remove original/List element
Can replace element 

String[] al = {"b", "c", "a", "d"};
Arrays.sort(al); // [a, b, c, d]
for (String s : al) {
   System.out.print(s); // abcd
}
System.out.println("For exiting element " + Arrays.binarySearch(al, "a")); // 0 // if found, give +ve no with index
System.out.println("For not exiting element " + Arrays.binarySearch(al, "z")); // -5 // if not

### how HashMap works internally
- using key.hasCode(), try to find hash code
- using has code hashcodeKey && (n-1), fing bucket index, at staritng HashMap start with 16 index allocated, reflection value is .75/75%, if exit add another 16 index
- using bucket index, jvm try to push key value pair and pointer as a linked list, if some value already exit there, it compare with .equal to method of key then push new value in same index.
- retrive data in same way, find hashcode, find bucket index, compare key with equals() and get back there

```  
//hashMap based on node, in every linked list contain these things
node
key
value
next()

There are three method available
equals(): compare key if found then replace otherwise replace
hashcode() : return a reference/address/Integer where element is inserted.
buckets(): node of array.

```

Steps for retrieve data:
Get the index, if key found in that index return value
In index, value is not found then search for next(use next fn) and return value.   

### optional:
when we want to work with null value, good way to use optional.
there we have two method of and nullable
Optional.ofNullable() // if found null value return empty
optional.of() // if found null throw null pointer exception


### Fail fast Fail safe
* Fail fast: we one collection is working in loop and in between we modifiy, then it throw concernModificationException(). it's fast, good for if we try to avoid modification in between. normally work with ArrayList and some collections
* Fail Safe: if we want to modify collection in between without exception we can go with ConcernHasMap, it also work with multi thread, it's slower.
  


## Tuts refrence: Durga software(https://www.youtube.com/watch?v=rI3VkItC0eA&list=PLd3UqWTnYXOkVR3OR9UZGyEt9RFUbaTMZ)

