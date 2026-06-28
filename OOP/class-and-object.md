# Class and Object in Java

## 1. Definition

### Class

A class in Java is a blueprint or template used to create objects.

It defines the state and behavior of an object.

- State means variables or fields.
- Behavior means methods or functions.

Example:

```java
class Student {
    String name;
    int age;

    void study() {
        System.out.println(name + " is studying");
    }
}
```

In this example, `Student` is a class.

---

### Object

An object is a real instance of a class.

When we create an object, memory is allocated in the heap, and we can use the variables and methods defined inside the class.

Example:

```java
Student s = new Student();
```

Here, `s` is a reference variable pointing to a `Student` object.

---

## 2. Use Case

Classes and objects are used to represent real-world entities in code.

For example, in a real application, we can create classes like:

- `Student`
- `Employee`
- `Account`
- `Product`
- `Order`
- `Customer`

Each class defines common properties and behaviors.

Example:

```java
class Employee {
    String name;
    double salary;

    void work() {
        System.out.println(name + " is working");
    }
}
```

Now we can create multiple employee objects:

```java
Employee emp1 = new Employee();
emp1.name = "Ali";
emp1.salary = 50000;

Employee emp2 = new Employee();
emp2.name = "Ahmed";
emp2.salary = 70000;
```

Here, `emp1` and `emp2` are two different objects created from the same `Employee` class.

---

## 3. Example

```java
class Car {
    String brand;
    String color;

    void drive() {
        System.out.println(brand + " car is driving");
    }
}

public class Main {
    public static void main(String[] args) {
        Car car1 = new Car();
        car1.brand = "Toyota";
        car1.color = "Black";

        Car car2 = new Car();
        car2.brand = "Honda";
        car2.color = "White";

        car1.drive();
        car2.drive();
    }
}
```

### Output

```text
Toyota car is driving
Honda car is driving
```

### Explanation

- `Car` is a class.
- `car1` and `car2` are objects.
- Both objects have their own values for `brand` and `color`.
- The same `drive()` method behaves according to each object's data.

---

## 4. Memory Concept

When we write:

```java
Car car = new Car();
```

Java performs these steps:

1. `new Car()` creates an object in heap memory.
2. The constructor of `Car` is called.
3. The reference of the object is returned.
4. The reference is stored in the variable `car`.

Important point:

```java
Car car = new Car();
```

- `car` is a reference variable.
- The actual object is created in heap memory.
- If `car` is a local variable, it is stored in stack memory.

---

## 5. Common Mistakes

### Mistake 1: Thinking class and object are the same

Wrong understanding:

```text
Class and object are same.
```

Correct understanding:

```text
Class is a blueprint.
Object is a real instance of the class.
```

---

### Mistake 2: Declaring reference but not creating object

Wrong:

```java
Student s;
s.study(); // Error
```

Correct:

```java
Student s = new Student();
s.study();
```

Explanation:

Only declaring `Student s;` does not create an object.

---

### Mistake 3: Calling instance method without object

Wrong:

```java
Student.study(); // Error if study() is not static
```

Correct:

```java
Student s = new Student();
s.study();
```

Explanation:

Instance methods belong to objects, so we need an object to call them.

---

### Mistake 4: Confusing reference variable with actual object

Example:

```java
Student s = new Student();
```

Here:

- `s` is not the actual object.
- `s` is a reference variable.
- The actual object is created in heap memory.

---

### Mistake 5: Multiple references can point to the same object

Example:

```java
Student s1 = new Student();
s1.name = "Ali";

Student s2 = s1;
s2.name = "Ahmed";

System.out.println(s1.name);
```

Output:

```text
Ahmed
```

Explanation:

`s1` and `s2` are pointing to the same object.

---

## 6. Interview Questions and Answers

### Q1. What is a class in Java?

A class is a blueprint or template that defines variables and methods. Objects are created from a class.

Example:

```java
class Student {
    String name;
    void study() {
        System.out.println("Studying");
    }
}
```

---

### Q2. What is an object in Java?

An object is an instance of a class. It has state and behavior.

Example:

```java
Student s = new Student();
```

Here, `s` refers to an object of the `Student` class.

---

### Q3. What is the difference between class and object?

| Class | Object |
|---|---|
| Blueprint or template | Real instance of class |
| Logical entity | Runtime entity |
| Does not directly store object data | Stores actual object data |
| Created using `class` keyword | Created using `new` keyword |

---

### Q4. Where is an object stored in Java?

The actual object is stored in heap memory.

If the reference variable is local, then the reference variable is stored in stack memory.

Example:

```java
Student s = new Student();
```

- `new Student()` object is in heap.
- `s` reference is in stack if it is a local variable.

---

### Q5. Can we create multiple objects from one class?

Yes, we can create multiple objects from one class.

Example:

```java
Student s1 = new Student();
Student s2 = new Student();
Student s3 = new Student();
```

Here, three different objects are created from the same `Student` class.

---

### Q6. Can a class exist without an object?

Yes, a class can exist without an object.

Example:

```java
class Student {
}
```

This class exists even if no object is created.

---

### Q7. Can an object exist without a class?

No, in Java every object must belong to a class.

Example:

```java
Student s = new Student();
```

Here, the object belongs to the `Student` class.

---

### Q8. What happens when we use the `new` keyword?

When we use `new`, Java creates an object in heap memory and calls the constructor.

Example:

```java
Student s = new Student();
```

Steps:

1. Memory is allocated in heap.
2. Object is created.
3. Constructor is called.
4. Reference is returned.
5. Reference is stored in variable `s`.

---

### Q9. What is the state and behavior of an object?

State means the data of an object.

Behavior means the actions of an object.

Example:

```java
class Account {
    double balance;

    void deposit(double amount) {
        balance = balance + amount;
    }
}
```

Here:

- `balance` is state.
- `deposit()` is behavior.

---

### Q10. What is the best interview answer for class and object?

A class is a blueprint or template that defines the state and behavior of an entity. An object is a runtime instance of a class. When an object is created using the `new` keyword, memory is allocated in heap, the constructor is called, and a reference to that object is returned.

Example:

```java
class Employee {
    String name;
    double salary;

    void work() {
        System.out.println(name + " is working");
    }
}

Employee emp = new Employee();
```

Here, `Employee` is the class and `emp` is a reference variable pointing to an `Employee` object.

---

## 7. Quick Revision

```text
Class  = Blueprint
Object = Real instance of class

Class contains:
- Variables
- Methods
- Constructors
- Blocks
- Nested classes

Object contains:
- Actual values of instance variables
- Access to instance methods
```

---

## 8. Summary

- A class is a blueprint.
- An object is an instance of a class.
- Objects are created using the `new` keyword.
- Objects are stored in heap memory.
- Reference variables point to objects.
- One class can create multiple objects.
- Instance variables and methods are accessed through objects.
