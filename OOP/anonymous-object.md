# Anonymous Object in Java

## 1. Definition

An anonymous object in Java is an object that is created without assigning it to a reference variable.

Normally, we create an object like this:

```java
Student s = new Student();
s.study();
```

Here, `s` is a reference variable.

But an anonymous object is created like this:

```java
new Student().study();
```

Here, the object is created and the method is called directly, but the object reference is not stored in any variable.

---

## 2. Use Case

Anonymous objects are used when we need an object only once.

They are useful when:

- We want to call a method one time only.
- We do not need to reuse the object.
- We want to reduce unnecessary reference variables.
- We are passing an object directly to a method or constructor.

Example use cases:

```java
new Calculator().add(10, 20);
```

Here, the `Calculator` object is used only once.

Another example:

```java
printStudent(new Student());
```

Here, the `Student` object is created and passed directly to the method.

---

## 3. Example

```java
class Student {
    void study() {
        System.out.println("Student is studying");
    }
}

public class Main {
    public static void main(String[] args) {
        new Student().study();
    }
}
```

### Output

```text
Student is studying
```

### Explanation

In this example:

- `new Student()` creates an object.
- `.study()` calls the method directly.
- No reference variable is used.
- After this line, the same object cannot be accessed again.

---

## 4. Another Example

```java
class Calculator {
    void add(int a, int b) {
        System.out.println("Sum: " + (a + b));
    }
}

public class Main {
    public static void main(String[] args) {
        new Calculator().add(10, 20);
    }
}
```

### Output

```text
Sum: 30
```

### Explanation

The `Calculator` object is created only to call the `add()` method once.

---

## 5. Common Mistakes

### Mistake 1: Thinking anonymous object can be reused

Wrong understanding:

```text
Anonymous object can be reused later.
```

Correct understanding:

```text
Anonymous object cannot be reused because it has no reference variable.
```

Example:

```java
new Student().study();
```

After this line, we cannot call another method on the same object.

---

### Mistake 2: Creating multiple anonymous objects unintentionally

Example:

```java
new Student().study();
new Student().play();
```

This creates two different objects.

It does not call both methods on the same object.

Correct approach:

```java
Student s = new Student();
s.study();
s.play();
```

Use a reference variable when you need to call multiple methods on the same object.

---

### Mistake 3: Setting value in one anonymous object and reading from another

Example:

```java
new Student().name = "Ali";
System.out.println(new Student().name);
```

If the class is:

```java
class Student {
    String name;
}
```

Output:

```text
null
```

Explanation:

- First `new Student()` creates one object and sets name as `Ali`.
- Second `new Student()` creates another new object.
- The second object has default value `null`.

---

### Mistake 4: Using anonymous object when object is needed multiple times

Wrong:

```java
new Account().deposit(1000);
new Account().withdraw(500);
```

This creates two different `Account` objects.

Correct:

```java
Account account = new Account();
account.deposit(1000);
account.withdraw(500);
```

---

## 6. Interview Questions and Answers

### Q1. What is an anonymous object in Java?

An anonymous object is an object created without assigning it to a reference variable.

Example:

```java
new Student().study();
```

---

### Q2. Can we reuse an anonymous object?

No, we cannot reuse an anonymous object directly because it does not have a reference variable.

---

### Q3. When should we use anonymous objects?

We should use anonymous objects when we need to use an object only once.

Example:

```java
new Calculator().add(10, 20);
```

---

### Q4. How many objects are created here?

```java
new Student().study();
new Student().study();
```

Two objects are created because `new Student()` is called two times.

---

### Q5. Is an anonymous object eligible for garbage collection?

Yes, after the statement is executed, if no reference points to the object, it becomes eligible for garbage collection.

---

## 7. Quick Revision

```text
Anonymous Object = Object without reference variable

Normal object:
Student s = new Student();

Anonymous object:
new Student().study();

Use anonymous object when:
- Object is needed only once
- No need to reuse object
- Direct method call is required
```

---

## 8. Summary

- Anonymous object has no reference variable.
- It is used for one-time operations.
- It cannot be reused directly.
- Every `new ClassName()` creates a new object.
- If multiple methods need to be called on the same object, use a reference variable.
