# Generics

Excellent. **Generics** is one of the most important Core Java topics for **4+ years Java Backend interviews**. It is frequently asked in banking and product-based companies because it demonstrates type safety and good API design.

We'll cover it in the same interview-oriented format.

* ✅ Concept
* ✅ Why Generics were introduced
* ✅ Interview Answers
* ✅ Syntax
* ✅ Bounded Generics
* ✅ Wildcards
* ✅ Type Erasure
* ✅ Generic Methods
* ✅ Real-time Usage
* ✅ Interview Questions
* ✅ Coding Problems

---

# Generics ⭐⭐⭐⭐⭐

## 1. What are Generics?

### Interview Answer

> Generics are a feature introduced in Java 5 that allow classes, interfaces, and methods to operate on different data types while providing compile-time type safety and eliminating the need for explicit type casting.

---

# 2. Why were Generics introduced?

Before Java 5

Collections stored objects.

```java
ArrayList list = new ArrayList();

list.add("Sai");

list.add(100);
```

Everything is stored as an Object.

When retrieving

```java
String name = (String) list.get(0);
```

Need explicit casting.

If

```java
String name = (String) list.get(1);
```

Runtime

```
ClassCastException
```

---

With Generics

```java
ArrayList<String> list = new ArrayList<>();

list.add("Sai");
```

Now

```java
list.add(100);
```

Compile-time error.

---

## Advantages

* Compile-time type checking
* Eliminates explicit casting
* Prevents ClassCastException
* Improves code readability
* Enables reusable code

---

# 3. Basic Syntax

```java
ClassName<Type>
```

Example

```java
ArrayList<String> list = new ArrayList<>();
```

Here

```
String
```

is the generic type.

---

# 4. Generic Class

Example

```java
class Box<T>{

    private T value;

    public void set(T value){
        this.value=value;
    }

    public T get(){
        return value;
    }

}

public class Main{

    public static void main(String args[]){

        Box<String> box=new Box<>();

        box.set("Java");

        System.out.println(box.get());

    }

}
```

Output

```
Java
```

---

## Interview Question

### What does T mean?

### Answer

T is called a **Type Parameter**.

It represents any data type.

Common names

```
T -> Type

E -> Element

K -> Key

V -> Value

N -> Number
```

---

# 5. Generic Method

Example

```java
public class Main{

    public static <T> void print(T value){

        System.out.println(value);

    }

    public static void main(String args[]){

        print("Java");

        print(100);

        print(10.5);

    }

}
```

Output

```
Java

100

10.5
```

---

## Interview Question

Difference between Generic Class and Generic Method?

### Answer

A Generic Class uses type parameters for the entire class, whereas a Generic Method introduces its own type parameter that applies only to that method.

---

# 6. Bounded Generics ⭐⭐⭐⭐

Suppose only numbers are allowed.

```java
class Calculator<T extends Number>{

}
```

Allowed

```java
Calculator<Integer>

Calculator<Double>

Calculator<Float>
```

Not allowed

```java
Calculator<String>
```

Compile-time error.

---

## Interview Question

Why use bounded generics?

### Answer

To restrict the types that can be passed, ensuring only compatible types are accepted.

---

# 7. Multiple Bounds

```java
<T extends Number & Comparable<T>>
```

Interview Question

Can Java support multiple inheritance using Generics?

Answer

No.

Generics support one class and multiple interfaces.

Example

```java
<T extends Number & Comparable<T>>
```

---

# 8. Wildcards ⭐⭐⭐⭐⭐

Most asked.

There are three types.

---

## Unbounded Wildcard

```java
List<?>
```

Can hold any type.

```java
List<String>

List<Integer>

List<Double>
```

---

## Upper Bounded Wildcard

```java
List<? extends Number>
```

Accepts

```
Integer

Double

Float
```

Not

```
String
```

---

## Lower Bounded Wildcard

```java
List<? super Integer>
```

Accepts

```
Integer

Number

Object
```

---

# Interview Question

Difference between extends and super?

### Answer

| extends     | super       |
| ----------- | ----------- |
| Read data   | Write data  |
| Upper bound | Lower bound |
| Producer    | Consumer    |

**Memory Tip:** **PECS**

* **Producer → Extends**
* **Consumer → Super**

---

# Example

```java
public static void print(List<? extends Number> list){

    for(Number n:list){

        System.out.println(n);

    }

}
```

---

# 9. Type Erasure ⭐⭐⭐⭐⭐

Most asked.

Interview Question

What is Type Erasure?

### Interview Answer

Type Erasure is the process by which the Java compiler removes generic type information during compilation and replaces it with Object or the bounded type. Generics exist only at compile time and are not available at runtime.

---

Example

Compile-time

```java
ArrayList<String>
```

Runtime

```
ArrayList
```

---

## Why Type Erasure?

Backward compatibility.

Old Java code still works.

---

# 10. Generic Interface

Example

```java
interface Printer<T>{

    void print(T value);

}
```

Implementation

```java
class StringPrinter implements Printer<String>{

    public void print(String value){

        System.out.println(value);

    }

}
```

---

# 11. Real-Time Usage

Collections

```java
List<String>

Map<Integer,String>

Set<Employee>
```

Spring

```java
ResponseEntity<Employee>
```

Optional

```java
Optional<Employee>
```

Comparable

```java
Comparable<Employee>
```

---

# Interview Questions

---

## What are Generics?

**Answer**

Generics allow classes, interfaces, and methods to work with different data types while ensuring compile-time type safety.

---

## Why were Generics introduced?

**Answer**

To provide compile-time type checking, eliminate explicit casting, and reduce runtime ClassCastException.

---

## What is Type Erasure?

**Answer**

The compiler removes generic type information during compilation, so generic types are not available at runtime.

---

## What is a Generic Class?

**Answer**

A class defined using a type parameter.

Example

```java
class Box<T>{

}
```

---

## What is a Generic Method?

**Answer**

A method that declares its own type parameter.

```java
public static <T> void print(T value)
```

---

## Difference between Generic Class and Generic Method?

| Generic Class        | Generic Method       |
| -------------------- | -------------------- |
| Type for whole class | Type only for method |

---

## What are Wildcards?

**Answer**

Wildcards (`?`) represent an unknown type and make generic code more flexible.

---

## Types of Wildcards?

* `<?>`
* `<? extends T>`
* `<? super T>`

---

## Difference between extends and super?

**Answer**

* `extends` is used for reading (Producer).
* `super` is used for writing (Consumer).

Remember **PECS**:

**Producer Extends, Consumer Super.**

---

## What is PECS?

**Answer**

PECS stands for **Producer Extends, Consumer Super**, a guideline for choosing between `extends` and `super` wildcards.

---

## Can Generics work with primitive types?

**Answer**

No.

Use wrapper classes.

```
Integer

Double

Long

Character
```

---

## Can we create Generic Arrays?

**Answer**

No.

```java
T[] arr = new T[10];
```

Not allowed.

---

## Why?

Because of Type Erasure.

---

# Coding Problems

### 1. Create Generic Class

```java
class Box<T>{

    T value;

}
```

---

### 2. Create Generic Method

```java
public static <T> void display(T value){

    System.out.println(value);

}
```

---

### 3. Create Generic Interface

```java
interface Printer<T>{

    void print(T value);

}
```

---

### 4. Use Upper Bounded Wildcard

```java
List<? extends Number>
```

---

### 5. Use Lower Bounded Wildcard

```java
List<? super Integer>
```

---

## ⭐ Frequently Asked in 4+ Years Interviews

Focus especially on:

1. What are Generics?
2. Why were Generics introduced?
3. Generic Class vs Generic Method
4. Wildcards (`?`, `extends`, `super`)
5. PECS (Producer Extends, Consumer Super)
6. Type Erasure
7. Why Generics don't work with primitive types
8. Real-world use of Generics in Collections and Spring Boot

These are the questions most commonly asked in Java backend interviews. After mastering Generics, the next major topic in your plan is **Design Patterns**, starting with the **Singleton Pattern**.

--
in Generics this i see  extends producer consumer super is it different compared to inheritance concept we have in oops  tell in single sentence

**Yes, they are different—`extends` in Generics is used to restrict the allowed types (type bounds), whereas `extends` in OOP inheritance is used for a class to inherit properties and behavior from another class.**
