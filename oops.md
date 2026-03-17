# Java If Condition Examples

This document contains simple examples of **if conditions in Java** for beginners.

---





```python
public class SimpleIfElseIf {
    public static void main(String[] args) {

        int marks = 65;

        if (marks >= 90) {
            System.out.println("Grade A");
        } 
        else if (marks >= 75) {
            System.out.println("Grade B");
        } 
        else if (marks >= 50) {
            System.out.println("Grade C");
        } 
        else {
            System.out.println("Fail");
        }

    }
}
```

## 🔹 1. Simple for Loop
```python
public class ForLoopExample {
    public static void main(String[] args) {

        for (int i = 1; i <= 5; i++) {
            System.out.println(i);
        }

    }
}
```
```python
🔹 Output
1
2
3
4
5
```
## 🔹 2. Simple while Loop
```python
public class WhileLoopExample {
    public static void main(String[] args) {

        int i = 1;

        while (i <= 5) {
            System.out.println(i);
            i++;
        }

    }
}
```
## 🔹 Output
```python
1
2
3
4
5
```
## 🔹 3. Simple do-while Loop
```python
public class DoWhileExample {
    public static void main(String[] args) {

        int i = 1;

        do {
            System.out.println(i);
            i++;
        } while (i <= 5);

    }
}
```
```python
🔹 Output
1
2
3
4
5
```



```
## 🔹 1. Simple `if` Statement

Checks a condition and executes code only if it is true.

```java
public class SimpleIf {
    public static void main(String[] args) {
        int age = 20;

        if (age >= 18) {
            System.out.println("You are eligible to vote");
        }
    }
}
```

🔹 2. if-else Statement

Executes one block if condition is true, otherwise another block.

public class IfElseExample {
    public static void main(String[] args) {
        int number = 5;

        if (number % 2 == 0) {
            System.out.println("Even number");
        } else {
            System.out.println("Odd number");
        }
    }
}
🔹 3. if-else if Ladder

Used when multiple conditions need to be checked.

public class GradeExample {
    public static void main(String[] args) {
        int marks = 85;

        if (marks >= 90) {
            System.out.println("Grade A");
        } else if (marks >= 75) {
            System.out.println("Grade B");
        } else if (marks >= 50) {
            System.out.println("Grade C");
        } else {
            System.out.println("Fail");
        }
    }
}
## 🔹 4. Nested if Statement

An if inside another if.

public class NestedIf {
    public static void main(String[] args) {
        int age = 22;
        boolean hasID = true;

        if (age >= 18) {
            if (hasID) {
                System.out.println("Entry allowed");
            } else {
                System.out.println("ID required");
            }
        } else {
            System.out.println("Underage");
        }
    }
}
```
## 🔹 5. Real-World Example (Login Check)
```python
public class LoginExample {
    public static void main(String[] args) {
        String username = "admin";
        String password = "1234";

        if (username.equals("admin") && password.equals("1234")) {
            System.out.println("Login successful");
        } else {
            System.out.println("Invalid credentials");
        }
    }
}
```









# Java Control Statements and Operators

## 🔹 1. Control Statements

Control statements determine the flow of execution in a Java program.

---

### ✅ A. Decision-Making Statements

#### 1. if Statement
```java
if (condition) {
    // code runs if condition is true
}
```

## 2. if-else
```python
if (condition) {
    // true block
} else {
    // false block
}
```
## 3. if-else if ladder
```python
if (condition1) {
    // block 1
} else if (condition2) {
    // block 2
} else {
    // default block
}
```
## 4. switch
```python
switch (value) {
    case 1:
        // code
        break;
    case 2:
        // code
        break;
    default:
        // default code
}
```
## 🔁 B. Looping Statements
```python
### 1. for loop
for (int i = 0; i < 5; i++) {
    System.out.println(i);
}
```
### 2. while loop
```python
int i = 0;
while (i < 5) {
    System.out.println(i);
    i++;
}
```

### 3. do-while loop
```python
int i = 0;
do {
    System.out.println(i);
    i++;
} while (i < 5);
```
### 🔄 C. Jump Statements

## 1. break
```python
for (int i = 0; i < 5; i++) {
    if (i == 3) break;
}
```
## 2. continue
```python
for (int i = 0; i < 5; i++) {
    if (i == 3) continue;
    System.out.println(i);
}
```
## 3. return
```pyhton
return value;
```

# Object-Oriented Programming (OOP) in Java

## 🔹 What is OOP?

OOP is a programming paradigm based on the concept of **objects**, which contain:
- Data (variables)
- Behavior (methods/functions)

It helps in writing **modular, reusable, and scalable code**.

---

## 🔹 4 Pillars of OOP

### 1. Encapsulation 🔒

**Definition:** Wrapping data and methods into a single unit (class) and restricting direct access.

```java
class Student {
    private int marks;

    public void setMarks(int marks) {
        this.marks = marks;
    }

    public int getMarks() {
        return marks;
    }
}
```

## 2. Inheritance 🧬

Definition: One class acquires properties of another class.
```python
class Animal {
    void eat() {
        System.out.println("Eating...");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("Barking...");
    }
}
```

## 3. Polymorphism 🔁

Definition: One action, many forms.
```python
Method Overloading (Compile-time)
class MathUtil {
    int add(int a, int b) {
        return a + b;
    }

    int add(int a, int b, int c) {
        return a + b + c;
    }
}
```

Method Overriding (Runtime)
class Animal {
    void sound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {
    void sound() {
        System.out.println("Bark");
    }
}
### 4. Abstraction 🎭

Definition: Hiding implementation details and showing only functionality.

Using Abstract Class
```python
abstract class Vehicle {
    abstract void start();
}

class Car extends Vehicle {
    void start() {
        System.out.println("Car starts with key");
    }
}
Using Interface
interface Animal {
    void sound();
}

class Dog implements Animal {
    public void sound() {
        System.out.println("Bark");
    }
}
```

