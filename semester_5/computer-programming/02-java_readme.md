Java Basics Overview

This README introduces core concepts in Java programming, including data types, variables, functions, and object-oriented programming (OOP).

1. Introduction to Java  
    Java is a high-level, object-oriented programming language. It is platform-independent thanks to the Java Virtual Machine (JVM).

2. Data Types and Variables  
    Java has primitive data types and reference types.


Primitive Data Types:

|Type|Size|Example|
|---|---|---|
|int|4 bytes|42|
|long|8 bytes|123456789L|
|float|4 bytes|3.14f|
|double|8 bytes|3.14159|
|char|2 bytes|'A'|
|boolean|1 bit|true/false|
|byte|1 byte|127|
|short|2 bytes|32000|

Reference Types:

- Objects, arrays, and classes.
- Example:

```java
String name = "Alice";
```

3. Variables and Constants

```java
int age = 25;               // variable
final double PI = 3.14159;  // constant
```

- `final` keyword makes a variable immutable.
- Naming conventions: camelCase for variables, ALL_CAPS for constants.

4. Functions (Methods)  
    Functions in Java are called methods. They can return values or be void.

```java
public int add(int a, int b) {
    return a + b;
}

public void greet(String name) {
    System.out.println("Hello, " + name);
}
```

- `public` – accessible from anywhere.
- `static` – belongs to the class, not an instance.
- `void` – method returns nothing.

5. Static vs Instance

- Static members belong to the class.
- Instance members belong to an object of the class.

```java
class MathUtils {
    static double square(double x) {
        return x * x;
    }
}

System.out.println(MathUtils.square(5)); // No object needed
```

6. Object-Oriented Programming (OOP)  
    Java is OOP-based. Core concepts:

a. Classes and Objects

```java
class Person {
    String name;
    int age;

    void introduce() {
        System.out.println("Hi, I'm " + name);
    }
}

Person p = new Person();
p.name = "Alice";
p.introduce();
```

b. Encapsulation

- Use `private` fields and public getters/setters.

```java
class Person {
    private int age;
    
    public int getAge() { return age; }
    public void setAge(int age) { this.age = age; }
}
```

c. Inheritance

- `extends` allows a class to inherit from another.

```java
class Employee extends Person {
    double salary;
}
```

d. Polymorphism

- Methods can be overridden in subclasses.

```java
class Person {
    void speak() { System.out.println("I speak"); }
}

class Student extends Person {
    @Override
    void speak() { System.out.println("I study"); }
}
```

e. Abstraction

- Use `abstract` classes or `interface` to define contracts.

```java
abstract class Animal {
    abstract void makeSound();
}
```

7. Control Flow

- `if`, `else`, `switch` for conditions.
- `for`, `while`, `do-while` for loops.
- `break` and `continue` for loop control.

8. Arrays and Collections

```java
int[] numbers = {1, 2, 3, 4};
String[] names = new String[3];

List<String> list = new ArrayList<>();
list.add("Alice");
list.add("Bob");
```

9. Exception Handling

```java
try {
    int result = 10 / 0;
} catch (ArithmeticException e) {
    System.out.println("Cannot divide by zero");
} finally {
    System.out.println("This always executes");
}
```

10. Entry Point  
    All Java programs start with a main method:

```java
public class Main {
    public static void main(String[] args) {
        System.out.println("Hello, Java!");
    }
}
```