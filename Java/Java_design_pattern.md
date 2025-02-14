### Java design pattern:
is a solution template of some problems which generally occur while coding.
As category it's devided in three part: Creational design pattern, stuctrual, behavior design pattern.
there are 23 type of design pattern, it depend on requiremnt which can use, don't use all in same times.

### 1. Creational design pattern
#### a. Singalton: every instace is create a single time or once, it's means it stop creating duplicate instance. at time of decalare use static and private key to do this. update of parent class obj is not allowed
it save obj in cache memoryand use multiple times. by using @bean, @Component in spring boot, can be use this concept.
example:

```
public class SingletonDesignPattern {
    // to make single ton class follow two steps
    // constructor should be private
    // constructor should call once so only one obj should create


    public static void main(String[] args){
        AbcSingleton obj1 = AbcSingleton.getCustInstance();
        System.out.println("Print main fn _ 1: "+ obj1.hashCode());
        AbcSingleton obj2 = AbcSingleton.getCustInstance();
        System.out.println("Print main fn _ 2: "+ obj2.hashCode());
        // calling two times but creating one instance
        // if it called twice value but due to if cond only one instance added, below output
        // same hashcode id means not created duplicate
/*        obj is reassigned
        Print main fn _ 1: 1828972342
        Print main fn _ 2: 1828972342*/
    }

}

class AbcSingleton {
    private static AbcSingleton obj=null; // private static, means not recreate obj from outside, create only once

    private AbcSingleton(){
    } // calling constructor with new key word means creating a new instance.


    public static AbcSingleton getCustInstance(){
        if (obj==null){ // if instance is already created it'll avoid creating new instance
            obj= new AbcSingleton();
            System.out.println("obj is reassigned");
        }
        return obj;
    }
}
```

b. factory design pattern: in this design pattern we compose/process a obj by using inheritance concept, sub class obj can we modify, we try to achive loose couple things. 

Code example:
```
public class FactoryDesignPattern {
    public static void main(String[] args) {
        client();
    }
    static void client(){
        String devType="web";
        Employee dev;
        if(devType.equals("web")){
            dev = new WebDevloper();
        }else {
            dev = new AdroidDevloper();
        }
        dev.name();

    }
}

interface Employee {
    void name();
}

class WebDevloper implements Employee{

    @Override
    public void name() {
        System.out.println("this is web developer");
    }
}

class AdroidDevloper implements Employee{
    @Override
    public void name() {
        System.out.println("this is AdroidDevloper");
    }
}

```

#2. stuctrual :
Based on code stucture or project structure, we deside the code pattern
#3. behavior design pattern :
this design pattern manage two object interaction behavior.  
