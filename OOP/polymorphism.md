# Polymorphism in Java

## 1. Definition

Polymorphism is an Object-Oriented Programming concept where one thing can have many forms.

In Java, polymorphism allows the same method name or same object reference to behave differently based on the situation.

The word polymorphism means:

```text
Poly = many
Morphism = forms
```

So polymorphism means **many forms**.

---

## 2. Types of Polymorphism in Java

Java mainly supports two types of polymorphism:

1. Compile-time polymorphism
2. Runtime polymorphism

---

## 3. Compile-Time Polymorphism

Compile-time polymorphism is achieved by **method overloading**.

Method overloading means multiple methods have the same name but different parameters.

It is called compile-time polymorphism because the method call is decided at compile time.

Example:

```java
class Calculator {
    int add(int a, int b) {
        return a + b;
    }

    int add(int a, int b, int c) {
        return a + b + c;
    }

    double add(double a, double b) {
        return a + b;
    }
}
```

Here, the method name is same:

```java
add()
```

But parameters are different.

---

## 4. Runtime Polymorphism

Runtime polymorphism is achieved by **method overriding**.

Method overriding means a child class provides its own implementation of a method already defined in the parent class.

It is called runtime polymorphism because the method call is decided at runtime based on the actual object.

Example:

```java
class Animal {
    void sound() {
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {
    @Override
    void sound() {
        System.out.println("Dog barks");
    }
}

class Cat extends Animal {
    @Override
    void sound() {
        System.out.println("Cat meows");
    }
}
```

---

## 5. Use Case

Polymorphism is used when we want the same method or same reference type to behave differently for different objects.

It is useful for:

- Code flexibility
- Code reusability
- Loose coupling
- Runtime decision making
- Cleaner and scalable design

---

## 6. Real-Life Use Case

Suppose we are building a payment system.

Different payment methods can have different processing logic:

- Card payment
- Wallet payment
- Bank transfer
- Raast payment

We can create a common parent interface:

```java
interface Payment {
    void pay(double amount);
}
```

Then each payment type can provide its own implementation:

```java
class CardPayment implements Payment {
    public void pay(double amount) {
        System.out.println("Paid by card: " + amount);
    }
}

class WalletPayment implements Payment {
    public void pay(double amount) {
        System.out.println("Paid by wallet: " + amount);
    }
}

class RaastPayment implements Payment {
    public void pay(double amount) {
        System.out.println("Paid by Raast: " + amount);
    }
}
```

Now we can use one reference type:

```java
Payment payment = new CardPayment();
payment.pay(1000);
```

Later, we can change implementation:

```java
Payment payment = new WalletPayment();
payment.pay(1000);
```

Same method call:

```java
pay()
```

But behavior is different depending on the actual object.

---

## 7. Example

```java
class Animal {
    void sound() {
        System.out.println("Animal makes sound");
    }
}

class Dog extends Animal {
    @Override
    void sound() {
        System.out.println("Dog barks");
    }
}

class Cat extends Animal {
    @Override
    void sound() {
        System.out.println("Cat meows");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal animal;

        animal = new Dog();
        animal.sound();

        animal = new Cat();
        animal.sound();
    }
}
```

### Output

```text
Dog barks
Cat meows
```

### Explanation

In this example:

- `Animal` is the parent class.
- `Dog` and `Cat` are child classes.
- Both child classes override the `sound()` method.
- The reference type is `Animal`.
- The actual object is `Dog` or `Cat`.
- At runtime, Java decides which `sound()` method to call.

---

## 8. Method Overloading Example

```java
class Printer {
    void print(String text) {
        System.out.println(text);
    }

    void print(int number) {
        System.out.println(number);
    }

    void print(String text, int count) {
        System.out.println(text + " " + count);
    }
}

public class Main {
    public static void main(String[] args) {
        Printer printer = new Printer();

        printer.print("Hello");
        printer.print(100);
        printer.print("Java", 5);
    }
}
```

### Output

```text
Hello
100
Java 5
```

### Explanation

The same method name `print()` is used with different parameters.

This is compile-time polymorphism.

---

## 9. Method Overriding Example

```java
class Bank {
    double getInterestRate() {
        return 0.0;
    }
}

class HBL extends Bank {
    @Override
    double getInterestRate() {
        return 10.5;
    }
}

class Meezan extends Bank {
    @Override
    double getInterestRate() {
        return 12.0;
    }
}

public class Main {
    public static void main(String[] args) {
        Bank bank;

        bank = new HBL();
        System.out.println(bank.getInterestRate());

        bank = new Meezan();
        System.out.println(bank.getInterestRate());
    }
}
```

### Output

```text
10.5
12.0
```

### Explanation

The same method `getInterestRate()` gives different results based on the actual object.

This is runtime polymorphism.

---

## 10. Common Mistakes

### Mistake 1: Confusing overloading with overriding

Overloading:

```text
Same method name, different parameters, same class or child class.
```

Overriding:

```text
Same method name, same parameters, parent-child relationship.
```

Example overloading:

```java
void add(int a, int b) {
}

void add(int a, int b, int c) {
}
```

Example overriding:

```java
class Parent {
    void show() {
    }
}

class Child extends Parent {
    @Override
    void show() {
    }
}
```

---

### Mistake 2: Thinking return type alone can overload a method

Wrong:

```java
int add(int a, int b) {
    return a + b;
}

double add(int a, int b) {
    return a + b;
}
```

This is not allowed because parameters are same.

Correct:

```java
int add(int a, int b) {
    return a + b;
}

double add(double a, double b) {
    return a + b;
}
```

Method overloading depends on parameter list, not only return type.

---

### Mistake 3: Reducing visibility while overriding

Wrong:

```java
class Parent {
    public void show() {
    }
}

class Child extends Parent {
    @Override
    private void show() {
    }
}
```

This is not allowed.

Correct:

```java
class Parent {
    public void show() {
    }
}

class Child extends Parent {
    @Override
    public void show() {
    }
}
```

In overriding, child class cannot reduce method visibility.

---

### Mistake 4: Thinking static methods are overridden

Static methods are not overridden. They are hidden.

Example:

```java
class Parent {
    static void show() {
        System.out.println("Parent static method");
    }
}

class Child extends Parent {
    static void show() {
        System.out.println("Child static method");
    }
}
```

This is method hiding, not method overriding.

Runtime polymorphism does not apply to static methods.

---

### Mistake 5: Thinking fields are overridden

Fields are not overridden in Java. Only methods are overridden.

Example:

```java
class Parent {
    String name = "Parent";
}

class Child extends Parent {
    String name = "Child";
}
```

This is field hiding, not overriding.

---

### Mistake 6: Calling child-specific method using parent reference

Example:

```java
class Animal {
    void sound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("Dog barks");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal animal = new Dog();

        animal.sound();
        animal.bark(); // Error
    }
}
```

Even though actual object is `Dog`, reference type is `Animal`.

So we can only call methods available in `Animal`.

Correct:

```java
Dog dog = new Dog();
dog.bark();
```

Or use casting carefully:

```java
Animal animal = new Dog();

if (animal instanceof Dog) {
    Dog dog = (Dog) animal;
    dog.bark();
}
```

---

## 11. Interview Questions and Answers

### Q1. What is polymorphism in Java?

Polymorphism is an OOP concept where the same method or reference can behave differently in different situations.

It means many forms.

---

### Q2. What are the types of polymorphism in Java?

Java has two main types of polymorphism:

1. Compile-time polymorphism
2. Runtime polymorphism

Compile-time polymorphism is achieved by method overloading.

Runtime polymorphism is achieved by method overriding.

---

### Q3. What is compile-time polymorphism?

Compile-time polymorphism means the method call is decided at compile time.

It is achieved using method overloading.

Example:

```java
void add(int a, int b) {
}

void add(int a, int b, int c) {
}
```

---

### Q4. What is runtime polymorphism?

Runtime polymorphism means the method call is decided at runtime based on the actual object.

It is achieved using method overriding.

Example:

```java
Animal animal = new Dog();
animal.sound();
```

If `Dog` overrides `sound()`, then Dog's method will be called.

---

### Q5. What is method overloading?

Method overloading means multiple methods with the same name but different parameters.

Example:

```java
void print(String text) {
}

void print(int number) {
}
```

---

### Q6. What is method overriding?

Method overriding means a child class provides its own implementation of a method already defined in the parent class.

Example:

```java
class Parent {
    void show() {
    }
}

class Child extends Parent {
    @Override
    void show() {
    }
}
```

---

### Q7. Difference between overloading and overriding?

| Overloading | Overriding |
|---|---|
| Same method name, different parameters | Same method name, same parameters |
| Can happen in same class | Requires inheritance |
| Compile-time polymorphism | Runtime polymorphism |
| Return type alone does not matter | Return type can be same or covariant |
| Static methods can be overloaded | Static methods cannot be overridden |

---

### Q8. Can we override static methods?

No, static methods cannot be overridden.

They can be hidden, but runtime polymorphism does not apply to static methods.

---

### Q9. Can we overload static methods?

Yes, static methods can be overloaded.

Example:

```java
static void test(int a) {
}

static void test(String a) {
}
```

---

### Q10. Can we overload the main method?

Yes, we can overload the main method.

Example:

```java
public static void main(String[] args) {
}

public static void main(int args) {
}
```

But JVM calls only this method as program entry point:

```java
public static void main(String[] args)
```

---

### Q11. Can private methods be overridden?

No, private methods cannot be overridden because they are not visible in child class.

---

### Q12. Can final methods be overridden?

No, final methods cannot be overridden.

Example:

```java
final void show() {
}
```

---

### Q13. What is dynamic method dispatch?

Dynamic method dispatch is the mechanism by which Java decides at runtime which overridden method to call.

Example:

```java
Animal animal = new Dog();
animal.sound();
```

Here, Java calls Dog's `sound()` method at runtime.

---

### Q14. What is the best interview answer for polymorphism?

Polymorphism is an OOP concept where the same method or reference can have different behaviors. In Java, compile-time polymorphism is achieved using method overloading, and runtime polymorphism is achieved using method overriding. Runtime polymorphism allows parent class references to point to child class objects, and the actual method implementation is selected at runtime.

---

## 12. Quick Revision

```text
Polymorphism = Many forms

Types:
1. Compile-time polymorphism
   - Method overloading

2. Runtime polymorphism
   - Method overriding

Overloading:
Same method name, different parameters

Overriding:
Same method name, same parameters, parent-child relationship

Example:
Animal animal = new Dog();
animal.sound();
```

---

## 13. Summary

- Polymorphism means many forms.
- It allows the same method or reference to behave differently.
- Compile-time polymorphism is achieved by method overloading.
- Runtime polymorphism is achieved by method overriding.
- Overloading depends on method parameters.
- Overriding depends on inheritance.
- Static methods are not overridden.
- Private and final methods cannot be overridden.
- Runtime polymorphism improves flexibility and loose coupling.
