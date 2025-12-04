### Features

- **Widely used:** Java is one of the most popular programming languages, used in web applications, Android apps, enterprise systems, and more.
- **Widely available:** Java runs on nearly all platforms due to its “write once, run anywhere” philosophy.

## JDK, JRE, and JVM

- **JDK (Java Development Kit):** The full toolkit for developing Java applications. Includes the compiler (`javac`), JRE, and development tools.
- **JRE (Java Runtime Environment):** Allows you to run Java programs. Includes the JVM and standard Java libraries.
- **JVM (Java Virtual Machine):** Executes Java bytecode on any platform. Converts compiled `.class` files into machine code for the host system.

## Data Types

Java provides different kinds of values that can be stored and manipulated:

- **boolean:** Represents a truth value, either `true` or `false`.
- **int:** Represents integer numbers, e.g., `0`, `1`, `-47`.
- **double:** Represents real (floating-point) numbers, e.g., `3.14`, `1.0`, `-2.1`.
- **String:** Represents text, e.g., `"hello"`, `"example"`.

## Basic Function Structure

A simple Java function has the following structure:

```java
returnType functionName(parameters) {
    // statements
    return value; // if returnType is not void
}
```

Example:

```java
int add(int a, int b) {
    return a + b;
}
```

## Object-Oriented Programming (OOP) in Java

Java is an object-oriented language and supports the following key principles:

- **Classes and Objects:**
	- A class is a blueprint for objects.
	- An object is an instance of a class.

```java
class Car {
    String color;
    void drive() {
        System.out.println("Driving...");
    }
}
Car myCar = new Car();
myCar.drive();
```

- **Encapsulation:** Hiding data using private fields and providing public getters/setters.
- **Inheritance:** Allows a class to inherit fields and methods from another class.
- **Polymorphism:** Enables objects to take many forms, often through method overriding or interfaces.
- **Abstraction:** Hiding implementation details and exposing only necessary functionality through abstract classes or interfaces.