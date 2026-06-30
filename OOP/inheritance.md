# Inheritance in Java

## 1. Definition

Inheritance is an Object-Oriented Programming concept where one class can acquire the properties and methods of another class.

In Java, inheritance is used to create a parent-child relationship between classes.

- Parent class is also called superclass or base class.
- Child class is also called subclass or derived class.

Inheritance is achieved using the `extends` keyword.

Example:

```java
class Animal {
    void eat() {
        System.out.println("Animal is eating");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("Dog is barking");
    }
}
```

Here:

- `Animal` is the parent class.
- `Dog` is the child class.
- `Dog` inherits the `eat()` method from `Animal`.

---

## 2. Use Case

Inheritance is used when multiple classes have common properties or methods.

Instead of writing duplicate code in every class, we can place common code in a parent class and reuse it in child classes.

### Real-life example

Suppose we are building an employee management system.

Common fields for all employees:

- name
- email
- salary

Different employee types:

- Developer
- Manager
- Tester

We can create a common parent class:

```java
class Employee {
    String name;
    String email;
    double salary;

    void work() {
        System.out.println(name + " is working");
    }
}
```

Then child classes can inherit common fields and methods:

```java
class Developer extends Employee {
    void writeCode() {
        System.out.println(name + " is writing code");
    }
}

class Manager extends Employee {
    void manageTeam() {
        System.out.println(name + " is managing team");
    }
}
```

This avoids duplicate code and improves reusability.

---

## 3. Example

```java
class Vehicle {
    String brand;

    void start() {
        System.out.println(brand + " vehicle is starting");
    }
}

class Car extends Vehicle {
    void drive() {
        System.out.println(brand + " car is driving");
    }
}

public class Main {
    public static void main(String[] args) {
        Car car = new Car();

        car.brand = "Toyota";
        car.start();
        car.drive();
    }
}
```

### Output

```text
Toyota vehicle is starting
Toyota car is driving
```

### Explanation

In this example:

- `Vehicle` is the parent class.
- `Car` is the child class.
- `Car` inherits the `brand` variable and `start()` method from `Vehicle`.
- `Car` also has its own method `drive()`.

---

## 4. Types of Inheritance in Java

Java supports these types of inheritance using classes:

### 1. Single Inheritance

One child class inherits from one parent class.

```java
class Animal {
}

class Dog extends Animal {
}
```

---

### 2. Multilevel Inheritance

A class inherits from a child class, creating a chain.

```java
class Animal {
}

class Dog extends Animal {
}

class Puppy extends Dog {
}
```

Here:

```text
Animal -> Dog -> Puppy
```

---

### 3. Hierarchical Inheritance

Multiple child classes inherit from the same parent class.

```java
class Animal {
}

class Dog extends Animal {
}

class Cat extends Animal {
}
```

Here, both `Dog` and `Cat` inherit from `Animal`.

---

## 5. Important Point

Java does not support multiple inheritance with classes.

This is not allowed:

```java
class A {
}

class B {
}

class C extends A, B {
}
```

This gives a compile-time error.

Java avoids multiple inheritance with classes to prevent ambiguity problems.

However, Java supports multiple inheritance using interfaces.

Example:

```java
interface A {
    void methodA();
}

interface B {
    void methodB();
}

class C implements A, B {
    public void methodA() {
        System.out.println("Method A");
    }

    public void methodB() {
        System.out.println("Method B");
    }
}
```

---

## 6. Common Mistakes

### Mistake 1: Thinking private members are directly accessible in child class

Private members are inherited but cannot be accessed directly in child class.

Wrong:

```java
class Parent {
    private String name;
}

class Child extends Parent {
    void printName() {
        System.out.println(name); // Error
    }
}
```

Correct:

```java
class Parent {
    private String name;

    public String getName() {
        return name;
    }
}

class Child extends Parent {
    void printName() {
        System.out.println(getName());
    }
}
```

Use getter/setter methods to access private fields.

---

### Mistake 2: Thinking constructor is inherited

Constructors are not inherited in Java.

Example:

```java
class Parent {
    Parent() {
        System.out.println("Parent constructor");
    }
}

class Child extends Parent {
    Child() {
        System.out.println("Child constructor");
    }
}
```

When child object is created, parent constructor is called first, but constructor is not inherited.

---

### Mistake 3: Not understanding `super`

The `super` keyword is used to access parent class members or constructor.

Example:

```java
class Parent {
    String name = "Parent";
}

class Child extends Parent {
    String name = "Child";

    void printNames() {
        System.out.println(name);
        System.out.println(super.name);
    }
}
```

Output:

```text
Child
Parent
```

---

### Mistake 4: Using inheritance when composition is better

Inheritance should be used only when there is an **is-a** relationship.

Correct inheritance example:

```text
Dog is an Animal
Car is a Vehicle
Developer is an Employee
```

Wrong inheritance example:

```text
Car is an Engine
```

A car is not an engine. A car has an engine.

In this case, composition is better.

```java
class Engine {
}

class Car {
    private Engine engine;
}
```

---

### Mistake 5: Thinking Java supports multiple inheritance with classes

Java does not allow a class to extend more than one class.

Wrong:

```java
class C extends A, B {
}
```

Correct using interfaces:

```java
class C implements A, B {
}
```

---

## 7. Interview Questions and Answers

### Q1. What is inheritance in Java?

Inheritance is an OOP concept where one class acquires the properties and methods of another class using the `extends` keyword.

Example:

```java
class Dog extends Animal {
}
```

Here, `Dog` inherits from `Animal`.

---

### Q2. Why do we use inheritance?

We use inheritance for:

- Code reusability
- Reducing duplicate code
- Creating parent-child relationships
- Method overriding
- Runtime polymorphism

---

### Q3. What is the difference between parent class and child class?

| Parent Class | Child Class |
|---|---|
| Class whose properties are inherited | Class that inherits properties |
| Also called superclass | Also called subclass |
| Contains common behavior | Contains specific behavior |

---

### Q4. Which keyword is used for inheritance in Java?

The `extends` keyword is used for inheritance between classes.

Example:

```java
class Car extends Vehicle {
}
```

---

### Q5. Does Java support multiple inheritance?

Java does not support multiple inheritance with classes.

But Java supports multiple inheritance using interfaces.

---

### Q6. Are constructors inherited in Java?

No, constructors are not inherited.

However, when a child object is created, the parent class constructor is called first.

---

### Q7. Can private members be inherited?

Private members are part of the parent class, but they cannot be accessed directly in child class.

They can be accessed using public or protected getter/setter methods.

---

### Q8. What is method overriding?

Method overriding happens when a child class provides its own implementation of a method already defined in the parent class.

Example:

```java
class Animal {
    void sound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {
    @Override
    void sound() {
        System.out.println("Dog barks");
    }
}
```

---

### Q9. What is the difference between inheritance and composition?

| Inheritance | Composition |
|---|---|
| Represents is-a relationship | Represents has-a relationship |
| Uses `extends` | Uses object reference |
| Strong relationship | Flexible relationship |

Example inheritance:

```text
Dog is an Animal
```

Example composition:

```text
Car has an Engine
```

---

### Q10. What is the best interview answer for inheritance?

Inheritance is an OOP concept in which a child class acquires properties and methods of a parent class using the `extends` keyword. It is mainly used for code reusability and method overriding. Java supports single, multilevel, and hierarchical inheritance with classes, but it does not support multiple inheritance with classes to avoid ambiguity. Multiple inheritance can be achieved using interfaces.

---

## 8. Quick Revision

```text
Inheritance = Parent-child relationship

Keyword:
extends

Parent class:
Superclass / Base class

Child class:
Subclass / Derived class

Use when:
There is an is-a relationship

Example:
Dog is an Animal
Car is a Vehicle
Developer is an Employee
```

---

## 9. Summary

- Inheritance allows one class to reuse fields and methods of another class.
- It is implemented using the `extends` keyword.
- Parent class contains common behavior.
- Child class contains specific behavior.
- Java does not support multiple inheritance with classes.
- Constructors are not inherited.
- Private members cannot be accessed directly in child class.
- Use inheritance only when there is an is-a relationship.
