### Java design pattern:
is a solution template of some problems which generally occur while coding.
As category it's devided in three part: Creational design pattern, stuctrual, behavior design pattern.
there are 23 type of design pattern, it depend on requiremnt which can use, don't use all in same times.

### 1. Creational design pattern:
as name suggest handle all kind creation jaa obj, in a flexible and reusable manner
#### A. Singalton: 
every instace is create a single time or once, it's means it stop creating duplicate instance. at time of decalare use static and private key to do this. update of parent class obj is not allowed
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

#### B. factory design pattern:
in this design pattern we compose/process a obj by using inheritance concept, sub class obj can we modify, we try to achive loose couple things. 

Code example:
```
public class FactoryDesignPattern {
    public static void main(String[] args) {
        EmployeeFactory employeeFactory = new EmployeeFactory();
        employeeFactory.client("web");
    }
}

class EmployeeFactory{
    static void client(String devType){
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
#### C. Abstraction design pattern:
we are adding extra layer of a interface or factory design pattern. its similar type of factory design pattern, try to achive loose couple. 

Below code example:
client call AbstractFactory and AbstractFactory will call AdroidDevloperFactory and WebDevloperFactory, so there are two factory and one additional layer

Employee infterface is independeble, and based on requirment second factory call employee.


```
package AbstractionDesignPattern;

public class AbstractDesignPattern {
    public static void main(String[] args) {
        // client want a android dev so factory prepare android dev
        Employee employee1 = new AdroidDevloperFactory().chooseEmployee();
        employee1.name();

        // client want a web dev so factory prepare android dev
        Employee employee2 = new WebDevloperFactory().chooseEmployee();
        employee2.name();

    }
}

class EmployeeFactory{
    public Employee chooseFactory(AbstractFactory abstractFactory) {
        return abstractFactory.chooseEmployee();
    }
}

abstract class AbstractFactory{
    abstract Employee chooseEmployee();
}

class AdroidDevloperFactory extends EmployeeFactory{

    public Employee chooseEmployee() {
        return new AdroidDevloper();
    }
}

class WebDevloperFactory extends EmployeeFactory{

    public Employee chooseEmployee() {
        return new WebDevloper();
    }
}

class WebDevloper implements Employee {

    @Override
    public void name() {
        System.out.println("this is web developer");
    }
}

class AdroidDevloper implements Employee {
    @Override
    public void name() {
        System.out.println("this is AdroidDevloper");
    }
}

interface Employee {
    void name();
}

```

## 2. stuctrual :
Based on code stucture or project structure, we deside the code pattern, relationships between objects and classes.
## 3. behavior design pattern :
this design pattern manage two object interaction behavior.  

### Based on populality there are four pattern used in common.
1. Singleton (Use Case: Database connection, logging, configuration management)
2. factory design pattern  
3. Observer design pattern(Use Case: Event listeners in Java (like GUI components))
4. Strategy design pattern(Use Case: Sorting strategies (Comparator interface), Payment strategies, Sorting)

### Observer design pattern:
Defines a one-to-many dependency where multiple objects get notified when the state of one object changes
```
import java.util.*;

interface Observer {
    void update(String message);
}

class Subscriber implements Observer {
    private String name;
    public Subscriber(String name) { this.name = name; }
    public void update(String message) { System.out.println(name + " received: " + message); }
}

class Publisher {
    private List<Observer> observers = new ArrayList<>();
    public void subscribe(Observer observer) { observers.add(observer); }
    public void notifyObservers(String message) {
        for (Observer o : observers) o.update(message);
    }
}

public class Main {
    public static void main(String[] args) {
        Publisher news = new Publisher();
        Observer user1 = new Subscriber("User1");
        Observer user2 = new Subscriber("User2");

        news.subscribe(user1);
        news.subscribe(user2);
        news.notifyObservers("New Video Uploaded!");
    }
}

```

### Strategy Pattern (Behavioral):
Defines a family of algorithms and lets the client choose one at runtime, benefit loose couple, open-ended
```
interface PaymentStrategy {
    void pay(int amount);
}

class CreditCardPayment implements PaymentStrategy {
    public void pay(int amount) { System.out.println("Paid $" + amount + " with Credit Card."); }
}

class PayPalPayment implements PaymentStrategy {
    public void pay(int amount) { System.out.println("Paid $" + amount + " using PayPal."); }
}

class ShoppingCart {
    private PaymentStrategy strategy;
    public void setPaymentStrategy(PaymentStrategy strategy) { this.strategy = strategy; }
    public void checkout(int amount) { strategy.pay(amount); }
}

public class Main {
    public static void main(String[] args) {
        ShoppingCart cart = new ShoppingCart();
        cart.setPaymentStrategy(new CreditCardPayment());
        cart.checkout(100);

        cart.setPaymentStrategy(new PayPalPayment());
        cart.checkout(50);
    }
}

```
### jdk internally use gang of four classic design pattern and also use above and varoius design pattern 



to be complete later..
https://www.youtube.com/watch?v=D0d2TsfGY2E&list=PL0zysOflRCek8kmc_jYl_6C7tpud7U2V_&index=5
