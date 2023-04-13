<!-- what is a class in java ?  -->

# What is a class in java ?

A **class is a logical blueprint/template** from which individual objects are created. It is a collection of variables and methods. It is a user defined data type.

It always starts with the keyword `class` followed by the name of the class. The name of the class should always start with a capital letter.


The `display()` method is used to display the details of the student. It is a member function of the class.

## Example

```java
public class StudentType {
    String name;
    int rollNo;
    String address;

    void display() {
        System.out.println("Name: " + name);
        System.out.println("Roll No: " + rollNo);
        System.out.println("Address: " + address);
    }
}
```

## Understanding Objects

An object is an instance of a class. It is a physical entity. It is a real world entity. Here are the properties of an object:

- It has a **state**. It is represented by the attributes of the class. For example, the name, roll no and address of the student are the attributes of the student object.
- It has a **behavior**. It is represented by the methods of the class. For example, the `display()` method is used to display the details of the student.
- It has an **identity**. It is represented by an address. It is a `unique` identifier.

## How to use this class using object ?

We can create an object of the class and access the variables and methods of the class using the object. The `student` object is created using the `new` keyword.

The `new` keyword is used to create an object of a class. It allocates memory for the object and returns a reference to the object.

```java
public class Main {
    public static void main(String[] args) {
        StudentType student1 = new StudentType();
        student1.name = "John";
        student1.rollNo = 1;
        student1.address = "New York";

        student.display();
    }
}
```

## Understanding the `new` keyword

```java
StudentType student1
```

This runs at **compile** time. It allocates memory for the object and returns a reference to the object. The reference is stored in the `student1` variable. Compile time is the time when the code is compiled.

```java
new StudentType();
```

This runs at **runtime**. It allocates memory for the object and returns a reference to the object. The reference is stored in the `student1` variable. Runtime is the time when the code is executed.

## How to manipulate the state of an object ?

We can manipulate the state of an object by using the methods of the class. The `display()` method is used to display the details of the student. It is a member function of the class.

```java
public class StudentType {
    String name;
    int rollNo;
    String address;

    void display() {
        System.out.println("Name: " + name);
        System.out.println("Roll No: " + rollNo);
        System.out.println("Address: " + address);
    }
}
```

# Java constructor

A constructor basically defines what will happen when your object will be created. When you don't have any constructor in your class, Java compiler creates a default constructor for you. But if you have defined a constructor in your class, then Java compiler will not create a default constructor for you.

```java
class StudentType {
    String name;
    int rollNo;
    String address;
}

public class OOPS{
    public static void main(String[] args) {
        StudentType student1 = new StudentType();
        student1.name = "John";
        student1.rollNo = 1;
        student1.address = "New York";
    }
}
```

Here `StudentType()` is a constructor. 

## Constructor overloading

```java

public class StudentType {
    String name;
    int rollNo;
    String address;

    public StudentType(String name, int rollNo, String address) {
        this.name = name;
        this.rollNo = rollNo;
        this.address = address;
    }

    public StudentType(String name, int rollNo) {
        this(name, rollNo, ""); // Call the three-argument constructor with empty address
    }

    public StudentType(String name) {
        this(name, 0, ""); // Call the two-argument constructor with rollNo=0 and empty address
    }

    public StudentType() {
        this("", 0, ""); // Call the three-argument constructor with empty name, rollNo=0, and empty address
    }
}

```

In this example, we have defined **four constructors** for the StudentType class with different parameter lists.

- The first constructor takes three parameters **name, rollNo, and address** and sets the corresponding instance variables.
- The second constructor takes **only name and rollNo** and sets address to an empty string.
- The third constructor takes **only name** and sets both rollNo and address to default values. The fourth constructor takes no arguments and sets all instance variables to default values.

# Pass by value, and Pass by reference in java

In Java, when passing an argument to a method, there are two ways to do it: pass by value and pass by reference.

- **Pass by value:** In Java, primitive data types such as int, float, char, etc., are passed by value. When a primitive value is passed to a method, a copy of the value is made and passed to the method. Any changes made to the parameter inside the method have no effect on the original value outside the method.

  ```java

  public static void main(String[] args) {
    int num = 10;
    increment(num);
    System.out.println(num); // Output: 10
  }
  public static void increment(int num) {
    num++;
    }
  ```

In the above example, the increment() method receives a copy of the num variable. Any changes made to the num variable inside the method are not reflected outside the method.


- **Pass by reference:** In Java, objects are passed by reference. When an object is passed to a method, a copy of the reference to the object is passed to the method, not a copy of the object itself. This means that any changes made to the object inside the method are also reflected outside the method.

```java
public static void main(String[] args) {
    StringBuilder sb = new StringBuilder("Hello");
    appendString(sb);
    System.out.println(sb); // Output: Hello, World!
}

public static void appendString(StringBuilder sb) {
    sb.append(", World!");
}

```

In the above example, the `appendString()` method receives a copy of the reference to the `sb` StringBuilder object. Any changes made to the `sb` object inside the method are also reflected outside the method.

It's important to note that in Java, although objects are passed by reference, the reference itself is passed by value. This means that if you assign a new value to the reference inside the method, it does not affect the original reference outside the method.


# Wrapper Classes

In Java, a wrapper class is a class that allows you to **use primitive data types as objects.** 

For example, you can use an `Integer` object to represent an `integer` value instead of using the primitive `int` data type. Wrapper classes are used when you need to work with **objects instead of primitives**, for example, when you want to store integer values in a collection.

Java provides the following eight wrapper classes:

- Byte - represents a byte value
- Short - represents a short value
- Integer - represents an int value
- Long - represents a long value
- Float - represents a float value
- Double - represents a double value
- Character - represents a char value
- Boolean - represents a boolean value



```java
import java.util.ArrayList;

public class WrapperExample {
    public static void main(String[] args) {
       Integer a = 10;
       Integer b = 20;

       swap(a, b);
    }
}
```

If we tried swapping with `int a` and `int b`, it would not work. Because `int` is a primitive data type and it is passed by value. So, the values of `a` and `b` will not be swapped. 

But, if we use `Integer` instead of `int`, it will work. Because `Integer` is a wrapper class and it is passed by reference. So, the values of `a` and `b` will be swapped.



# The `final` keyword

In Java, the `final` keyword is used to declare a variable, method, or class as immutable, which means it cannot be changed or modified after it has been initialized.

For example, if a variable is declared as `final`, its value cannot be altered once it has been assigned a value. Similarly, if a method is declared as `final` it cannot be overridden by any subclass. And if a class is declared as `final` it cannot be subclassed.

```java
public class FinalExample {
    public static void main(String[] args) {
        final int a = 10;
        a = 20; // Error: cannot assign a value to a final variable
    }
}
```

# Packages

In Java, a package is a way to organize related classes, interfaces, and sub-packages into a single namespace. This makes it easier to manage and reuse code, as well as avoid naming conflicts with classes from other packages.

The `java.util` package is a built-in package in Java that provides a collection of useful utility classes and interfaces. 

This package contains classes for data structures such as arrays, lists, sets, maps, and iterators, as well as classes for working with dates, times, and other common utility classes.

```java

import java.util.ArrayList;

public class MyArrayListExample {
    public static void main(String[] args) {
        // create a new ArrayList of strings
        ArrayList<String> list = new ArrayList<>();

        // add some elements to the list
        list.add("apple");
        list.add("banana");
        list.add("orange");

        // print the list
        System.out.println(list);
    }
}
```

`import java.util.*` imports all the classes in the `java.util` package. This is called a wildcard import.

# The `import` statement

In Java, the import statement is used to make classes and interfaces from other packages available in your code. 

The import statement tells the Java compiler which classes or interfaces you want to use in your code and where to find them.

```java
import java.util.ArrayList;
import java.util.List;
```

# The `static` keyword

In Java, the `static` keyword is used to create variables, methods, and inner classes that belong to the class itself rather than to instances of the class. 

- This means that static members are shared by all instances of the class, and you don't need to create an object of the class to access them.

- On the other hand, `non-static` members are specific to each instance of the class. When you create an object of the class, each instance has its own copy of the non-static members.

```java
public class MyClass {
    static int staticVariable = 0;
    int nonStaticVariable = 0;

    static void staticMethod() {
        System.out.println("Static method");
    }

    void nonStaticMethod() {
        System.out.println("Non-static method");
    }
}
```

In this example, `staticVariable` and `staticMethod()` are declared as static, while nonStaticVariable and `nonStaticMethod()` are not. This means that you can access `staticVariable` and `staticMethod()` using the class name MyClass, while you need to create an instance of MyClass to access `nonStaticVariable` and `nonStaticMethod()`:

```java
// Access static members
MyClass.staticVariable = 1;
MyClass.staticMethod();

// Access non-static members
MyClass myObject = new MyClass();
myObject.nonStaticVariable = 2;
myObject.nonStaticMethod();

```


# PolyMorphism in Java

In Java, polymorphism is the ability of an object to take on many forms. The most common use of polymorphism in Java is when a parent class reference is used to refer to a child class object.

- Poly means many
- Morph means forms

```java
class Student{
    String name;
    int age;

    public void printInfo(String name){
        System.out.println(name);
    }
    
     public void printInfo(int age){
        System.out.println(age);
    }
}
```

This is called polymorphism because the `printInfo()` method can be used to print the name and age of the student but in different forms.

Now if from somewhere we'd call `s1.printInfo("John")` and `s1.printInfo(20)` then it would print the name and age of the student. So the same method is used to print different things. Run and compile times are kinda like js and ts.


## Compile Time Polymorphism

Compile time polymorphism is also known as static polymorphism. This is achieved by method overloading or operator overloading.

- Method overloading is when we have multiple methods with the same name but different parameters.

- Operator overloading is when we use the same operator for different purposes.

```java
class Student{
    String name;
    int age;

    public void printInfo(String name){
        System.out.println(name);
    }
    
     public void printInfo(int age){
        System.out.println(age);
    }
}
```

In this example, we have two methods with the same name `printInfo()` but different parameters. So, we can use the same method to print the name and age of the student. This is called method overloading.

🙊 We can't just have the same ` public void printInfo(String name){` method twice. We need to have different parameters or different number of parameters or different data types of parameters or return types to overload a method.


## Run Time Polymorphism

Run time polymorphism is also known as dynamic polymorphism. This is achieved by method overriding. 

- Method overriding is when we have two methods with the same name and parameters.

```java
class Student{
    String name;
    int age;

    public void printInfo(String name){
        System.out.println(name);
    }
    
     public void printInfo(int age){
        System.out.println(age);
    }
}
```

In this example, we have two methods with the same name `printInfo()` and same parameters. So, we can use the same method to print the name and age of the student. This is called method overriding.

🙊 We can't just have the same ` public void printInfo(String name)` method twice. We need to have different parameters or different number of parameters or different data types of parameters or return types to overload a method.


# Inheritance in Java

In Java, inheritance is a mechanism in which one class acquires the properties (methods and fields) of another. With the use of inheritance, the information is made manageable in a hierarchical order.

- Inheritance is a way to reuse code. We can reuse the code of an existing class when we create a new class. This is called inheritance.

- The class whose properties are inherited is called the superclass (base class, parent class).
  
- The class that inherits the properties of another class is called the subclass (derived class, child class).


```java
class Animal{
    String name;
    int age;

    public void eat(){
        System.out.println("Eating");
    }
    
    public void sleep(){
        System.out.println("Sleeping");
    }
}
```

In this example, we have a class `Animal` which has two properties `name` and `age` and two methods `eat()` and `sleep()`. Now, we can create a new class `Dog` which inherits the properties of the `Animal` class.

```java
class Dog extends Animal{
    String breed;

    public void bark(){
        System.out.println("Barking");
    }
}
```

In this example, we have a class `Dog` which inherits the properties of the `Animal` class. It has one additional property `breed` and one additional method `bark()`. So, we can create a new object of the `Dog` class and access all the properties and methods of the `Animal` class as well as the `Dog` class.

```java
class Main{
    public static void main(String[] args){
        Dog d1 = new Dog();
        d1.name = "John";
        d1.age = 5;
        d1.breed = "German Shepherd";
        d1.eat();
        d1.sleep();
        d1.bark();
    }
}
```

In this example, we have created a new object of the `Dog` class and accessed all the properties and methods of the `Animal` class as well as the `Dog` class.

🙊 In Java, we can only inherit from one class. We can't inherit from multiple classes. But we can implement multiple interfaces.


# Access Modifiers

In Java, access modifiers are keywords that set the accessibility or scope of a field, method, constructor, or class. There are four types of access modifiers in Java:


### Public Modifier

The access level of a public modifier is everywhere. It can be accessed from within the class, outside the class, within the package and outside the package.

The `main` class is always public because it is the entry point of the program. The compiler looks for the `main` method in the `main` class. So, the `main` class must be public.

```java
package p1;
public class A
{
public void display()
	{
		System.out.println("GeeksforGeeks");
	}
}

```

```java
package p2;
import p1.*;
class B {
	public static void main(String args[])
	{
		A obj = new A();
		obj.display();
	}
}
```



### Protected Modifier

The protected access modifier is specified using the keyword **protected**.

The methods or data members declared as protected are accessible **within the same package or subclasses in different packages**.

In this example, we will create two packages p1 and p2. Class A in p1 is made public, to access it in p2. The method display in class A is protected and class B is inherited from class A and this protected method is then accessed by creating an object of class B.


```java
package p1;

// Class A
public class A
{
protected void display()
	{
		System.out.println("GeeksforGeeks");
	}
}
``` 

```java
package p2;
import p1.*; // importing all classes in package p1

// Class B is subclass of A
class B extends A
{
    public static void main(String args[])
    {
	    B obj = new B();
	    obj.display();
    }
}
```

### Default Modifier

The access level of a default modifier is only within the package. It cannot be accessed from outside the package. If you do not specify any access level, it will be the default.

```java
package p1;

// Class Geek is having Default access modifier
class Geek
{
	void display()
	{
		System.out.println("Hello World!");
	}
}

```

```java
// Java program to illustrate error while
// using class from different package with
// default modifier
package p2;
import p1.*;

// This class is having default access modifier
class GeekNew
{
	public static void main(String args[])
	{
		// Accessing class Geek from package p1
		Geek obj = new Geek();

		obj.display();
	}
}
```
# Interfaces in Java

An Interface in Java programming language is defined as an abstract type used to specify the behavior of a class. An interface in Java is a blueprint of a behaviour. A Java interface contains static constants and abstract methods.

```java

class Laptop
{
    public void start()
    {
        System.out.println("Laptop started");
    }
}

class Developer
{
    public void code(Laptop lap)
    {
        lap.start();
        System.out.println("Developer is coding");
    }
}

```

## Multiple Inheritance using interfaces

To achieve multiple inheritance using interfaces, you can create two or more interfaces with different sets of abstract methods, and then create a class that implements all the interfaces. By doing so, the class will inherit the abstract methods from all the interfaces it implements.

```java

interface AnimalEat {
   void eat();
}
interface AnimalTravel {
   void travel();
}
class Animal implements AnimalEat, AnimalTravel {
   public void eat() {
      System.out.println("Animal is eating");
   }
   public void travel() {
      System.out.println("Animal is travelling");
   }
}
public class Demo {
   public static void main(String args[]) {
      Animal a = new Animal();
      a.eat();
      a.travel();
   }
}
```

- The interface AnimalEat and AnimalTravel have one abstract method each i.e. eat() and travel(). The class Animal implements the interfaces AnimalEat and AnimalTravel.

- In the method main() in class Demo, an object a of class Animal is created. Then the methods eat() and travel() are called.

- The class Animal implements both the interfaces AnimalEat and AnimalTravel. So the class Animal inherits the methods eat() and travel() from both the interfaces and that is how multiple inheritance is achieved in Java.
  

# Abstraction

Data Abstraction is the property by virtue of which only the essential details are displayed to the user. The trivial or the non-essential units are not displayed to the user. 

- Ex: A car is viewed as a car rather than its individual components.


## What is Abstract class in Java?

Java abstract class is a class that can not be initiated by itself, it needs to be subclassed by another class to use its properties. An abstract class is declared using the “abstract” keyword in its class definition.

```java

abstract class Shape 
{
    int color;
    // An abstract function
    abstract void draw();
}
```

In Java, the following some important observations about abstract classes are as follows:

- An instance of an abstract class can not be created.
- Constructors are allowed.
- We can have an abstract class without any abstract method.
- There can be a final method in abstract class but any abstract method in class(abstract class) can not be declared as final  or in simpler terms final method can not be abstract itself as it will yield an error: “Illegal combination of modifiers: abstract and final”
- We can define static methods in an abstract class
- We can use the abstract keyword for declaring top-level classes (Outer class) as well as inner classes as abstract
- If a class contains at least one abstract method then compulsory should declare a class as abstract 
- If the Child class is unable to provide implementation to all abstract methods of the Parent class then we should declare that Child class as abstract so that the next level Child class should provide implementation to the remaining abstract method

Data Abstraction may also be defined as the process of identifying only the required characteristics of an object ignoring the irrelevant details. The properties and behaviors of an object differentiate it from other objects of similar type and also help in classifying/grouping the objects.

Consider a real-life example of a man driving a car. The man only knows that pressing the accelerators will increase the speed of a car or applying brakes will stop the car, but he does not know how on pressing the accelerator the speed is actually increasing, he does not know about the inner mechanism of the car or the implementation of the accelerator, brakes, etc in the car. This is what abstraction is. 


# Relationship in Classes Java


If there are 2 different classes in java then there can be some relationship between them. 

![](https://i.ibb.co/xYNjRFV/2023-04-12-11-22.png)


## Advantages of relationship in classes

- Code reusability. If class B extends class A, then class B can use all the methods and variables of class A. So, there is no need to write the same code again and again.
- Cost cutting. 
- Reduced redundancy.


## Inheritance (IS-A relationship)

Inheritance is a mechanism in which one object acquires all the properties and behaviors of a parent object except the constructors and private members.

```java 

    class Vehicle{
        void run(){
            System.out.println("Vehicle is running");
        }
    }

    class Bike extends Vehicle{
        public static void main(String args[]){
            Bike obj = new Bike();
            obj.run();
        }
    }

```

**Therefore the bike `IS-A` vehicle.**

## Association (HAS-A relationship)

Association is another fundamental relationship between classes that is informally known as “Has-A” relationship.

When an object of one class is created as data member inside another class, it is called association relationship in java or simply Has-A relationship.

```java

class Student
{
    String name;
    int roll;
}
```

The Student `HAS-A` name and roll.

```java

class Engine{
    int cc;
    String type;
}

class Car{
    String name;
    Engine c = new Engine();
}

```

The 2 classes are not tightly coupled, but associated with each other. The Car `HAS-A` Engine.

If 2 classes have a weak bonding we can call it as **Aggregation** else we can call it as **Composition**.

![](https://i.ibb.co/Xs7gRTn/2023-04-12-11-55.png)

![](https://i.ibb.co/NmgV09V/2023-04-12-11-51.png)


## Dependencies (Use, call)

In Java, a class can depend on another class in order to use its functionality or to call its methods. This relationship between classes is known as a dependency.

There are two types of dependencies that can occur between classes:

- Use dependency: This occurs when one class uses another class as a parameter or return type of a method. For example, if a method in class A takes an object of class B as a parameter, then class A has a use dependency on class B.

- Call dependency: This occurs when one class directly invokes a method of another class. For example, if a method in class A calls a method of class B, then class A has a call dependency on class B.

Dependencies between classes are important to consider when designing and organizing a Java program. Too many dependencies can lead to tight coupling between classes, making it difficult to modify or maintain the code. 

In general, it's a good practice to minimize dependencies between classes and to use interfaces to decouple classes from each other as much as possible. This helps to make the code more modular and easier to maintain in the long run.

```java
// Class A depends on class B
public class A {
    public void doSomething(B b) { // use dependency on class B
        b.someMethod(); // call dependency on class B
    }
}

// Class B
public class B {
    public void someMethod() {
        // do something
    }
}

// Main class
public class Main {
    public static void main(String[] args) {
        B b = new B(); // create an instance of class B
        A a = new A(); // create an instance of class A
        a.doSomething(b); // use class B in class A
    }
}
```
**Explanation**

In this example, we have two classes: class A and class B. Class A has a use dependency on class B because it uses an object of class B as a parameter in the `doSomething()` method. Class A also has a call dependency on class B because it calls the `someMethod()` method of class B.

In the `main()` method of the Main class, we create instances of class A and class B, and then use class B in class A by calling the `doSomething()` method with the object of class B as a parameter. This illustrates how one class can depend on another class in Java.


# Relationship between objects in Java

In Java, relationships among objects are established through instantiation and links.

Instantiation is the process of creating an object from a class. When an object is instantiated, memory is allocated for it and the object is initialized with the default values of its instance variables.

```java
// Class definition
public class MyClass {
    private int myNumber;
    private String myString;
    
    public MyClass(int number, String string) {
        myNumber = number;
        myString = string;
    }
}

// Instantiation
MyClass obj = new MyClass(10, "Hello");
```

In this example, we define a class **MyClass** with two instance variables **myNumber** and **myString**. 

We then create an instance of **MyClass** using the new keyword and passing arguments **10** and **"Hello"** to the constructor. The resulting object obj is an instance of **MyClass** with myNumber set to 10 and **myString** set to **"Hello"**.

Once objects are instantiated, they can be linked to each other to establish relationships among them. There are several ways to link objects in Java, including:

- Method calls: Objects can call methods on each other to exchange information or perform actions.

- Composition: One object can contain another object as an instance variable, creating a "has-a" relationship between the two.

- Inheritance: One object can be a subclass of another object, inheriting its properties and behaviors and forming an "is-a" relationship.

- Association: Objects can have a reference to each other, allowing them to interact with each other as needed.

Understanding these relationships among objects is important for creating effective and efficient object-oriented programs in Java. By carefully designing these relationships, you can create code that is easy to read, understand, and maintain.