### Object-Oriented Programming Principles:
- Abstraction
- Polymorphism
- Inheritance
- Encapsulation

### Abstraction

Abstraction is the process of hiding unnecessary or complicated details to reduce complexity. 
This allows users to access more functionality on top of the provided abstraction.

For example, let’s consider the use of an ArrayList. An ArrayList offers dynamic resizing, constant time access to the iᵗʰ element, constant (amortized) insertion, and built-in functions. 
All of this functionality can be obtained by creating an ArrayList. Engineers are able to build more complex programs using ArrayLists by building on top of the provided ArrayList.

We can implement abstraction using **abstract classes**, **abstract methods**, and **interfaces**. Abstract classes cannot be instantiated. 
Rather subclasses use inheritance to extend these abstract classes. Abstract methods contain a function signature but no implementation. 
The implementation is left to the subclasses.

**Example Abstract Class**
```
abstract class Mammal {
  public String type = "Mammal";
  public String name;
  
  Mammal(String name) {
    this.name = name;
  }
  
  void printName() {
    System.out.println(this.name);
  }
  
  abstract void run();
}
```

The above is an abstract class. We can implement subclasses as below. We use the extends keyword to access the Mammal class and we use the 
Override keyword to denote we are overriding an abstract method.

We can use an interface to implement abstraction. An interface can be thought of as the blueprint for a Class. It can contain member variables and 
functions but not implementations for these functions. We have a MammalActions interface below. We use the implement keyword to denote the 
implementation of a certain interface.

**Example interface**
```
interface MammalActions {
  void bark();
  void eat();
  void sleep();
}
```

Suppose we have a Dog subclass and our Mammal parent class. We can access properties in our subclass (i.e. Dog) and in our parent class (i.e. Mammal). 
We know the myDog object must implement all methods in the interface, so we can call those as well. We use the super() keyword to access our parent class.

```
public class Dog extends Mammal implements MammalActions {
  Dog(String name) {
    super(name);
  }
  
  @override
  void run() {
    System.out.println("4 legs");
  }
  
  
  public void bark() {System.out.println("Woof");}
  public void eat() {System.out.println("Munch");}
  public void sleep() {System.out.println("Sleep");}
}
```

The above helps us to organize our code, reduce complexity, and group similar objects together (usually in a hierarchical structure).

### Polymorphism
Polymorphism allows the same method or variable to take on a different form depending on the context.

There are two kinds of polymorphism- run-time polymorphism and compile-time polymorphism. 
They are named based on when the polymorphism is resolved — either at run-time or compile-time.

Below is an example of run-time polymorphism, which is also known as method overriding. Both printDescription() methods have the same method signature 
but they are called by different objects. The drive() method is able to take on multiple forms based on the object calling it.

```
class Automobile {
  void print() {
    System.out.println("Auto");  
  }
}

class Car extends Automobile {
  @override
  void print() {
    System.out.println("Car");  
  }
}
```

We mentioned the concept of a method signature above — a method signature includes the access modifier (public, private, and protected), the static modifier, 
the return type (void, int[], String, etc.), and the method arguments (Integers, chars, Arrays, etc.).

Method overloading is when two methods have the same name but different arguments. 
The same object can call these methods and depending on the arguments given, the compiler can resolve which method has been called. 
This is compile-time polymorphism or method overloading.

```
class Automobile {
  void print() {
    System.out.println("Auto");  
  }
  
  void drive(int mph) {
    System.out.println("Driving at " + mph + " miles per hour");  
  }
  
  void drive(String brand) {
    System.out.println("Driving a " + brand);  
  }  
}

class Car extends Automobile {
  @override
  void print() {
    System.out.println("Car");  
  }
}
```

```
Car car = new Car();
car.drive(50);
car.drive("Nissan");
```

### Inheritance

Inheritance is the process where a subclass assumes the variables, properties, and methods of a parent class. We have already seen an example of inheritance. The Dog class inherited the Mammal class. 
In doing so, the Dog class had the member variable type and the function printName. Inheritance is achieved by using the extends keyword.

Inheritance is broken down into three types — single, multiple, and multilevel. Single inheritance is when a subclass extends a parent class and this parent class has no parent class of its own. Multilevel inheritance is when a child class extends a parent class and that parent class extends another parent class. This can be thought of as multiple levels (multilevel) of single inheritance.

Multiple inheritance is when a subclass inherits two or more parent classes but these parent classes have no relationship.

Java does not support multiple inheritance. Suppose, in the above example, that the Mammal Class and Pet Class both had an eat() method with the same arguments. If a Dog object calls eat(), Java would have no way to resolve this call. This ambiguity is one reason why Java does not support multiple inheritance.

### Encapsulation

The final key principle of object-oriented programming is encapsulation — the practice of binding method data and method functions in one single method. We can think of a method as a capsule that contains data and the code that manipulates this data. This process of data-hiding makes sure our data is only being accessed as we expected throughout the program.

Encapsulation in Java is achieved by making the member variables of a Class private and only allowing them to change through the use of getter and setter methods. These aptly named methods set the values of our member variables and get (and return) these values as well.

