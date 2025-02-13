### Java design pattern is a solution template of some problems which generally occur while coding.
As category it's devided in three part: Creational design pattern, stuctrual, behavior design pattern.
there are 23 type of design pattern, it depend on requiremnt which can use, don't use all in same times.

### 1. Creational design pattern
#### a. Singalton: every instace is create a single time or once, it's means it stop creating duplicate instance. at time of decalare use static and private key to do this. update of parent class obj is not allowed
it save obj in cache memoryand use multiple times. by using @bean, @Component in spring boot, can be use this concept.
example:

```
public class Main {

    public static void main(String[] args){
        System.out.println("Print main fn _ 1: "+AbcSingleton.getCustInstance());
        System.out.println("Print main fn _ 2: "+ AbcSingleton.getCustInstance()); 
        // calling two times but creating instance once
        // if it called twice value should be reassigned but its not, below output
        // obj is reassigned
        // Print main fn _ 1: 20
        // Print main fn _ 2: 20
    }

}

class AbcSingleton {
    private static int obj=0; // private static, means not recreate obj, create only once
    public static int getCustInstance(){
        if (obj==0){
            obj=20;
            System.out.println("obj is reassigned");
        }
        return obj;
    }
}

```

b. factory design pattern: in this design pattern we compose/process a obj by using inheritance concept, sub class obj can we modify, we try to achive loose couple things.  

#2. stuctrual 
#3. behavior design pattern
