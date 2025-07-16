# Java Concepts: A Detailed Guide

This document provides a detailed overview of fundamental Java programming concepts.

## Basic Syntax


Java's basic syntax is highly structured and object-oriented, requiring all code to reside within classes.

### Class Structure
Every Java program must have at least one class.
* A class is defined using the `class` keyword, followed by the class name.
* The class body is enclosed in curly braces `{}`.
* The file name must match the public class name.

```java
// Example of a basic class structure
public class MyFirstJavaProgram {
    // Class members (fields, methods) go here
}
```

### The `main` Method
The `main` method is the entry point for any Java application. When you run a Java program, the Java Virtual Machine (JVM) looks for this method to start execution.
* It must be `public static void main(String[] args)`.
    * `public`: Accessible from anywhere.
    * `static`: Can be called without creating an object of the class.
    * `void`: Does not return any value.
    * `main`: The name of the method.
    * `String[] args`: An array of `String` objects to hold command-line arguments.

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, Java!"); // Prints to the console
    }
}
```

### Statements and Semicolons
* Each statement in Java must end with a semicolon `;`. This indicates the end of an instruction.
* Blocks of code (e.g., method bodies, loop bodies, conditional statements) are defined by curly braces `{}`.

```java
int x = 10; // Assignment statement
System.out.println(x); // Method call statement

if (x > 5) {
    System.out.println("x is greater than 5.");
}
```

### Comments
Comments are used to explain code and are ignored by the Java compiler.
* **Single-line comments:** Start with `//`.
* **Multi-line comments:** Start with `/*` and end with `*/`.
* **Documentation comments (Javadoc):** Start with `/**` and end with `*/`. Used to generate API documentation.

```java
// This is a single-line comment

/*
 * This is a multi-line comment.
 * It can span across several lines.
 */

/**
 * This is a documentation comment.
 * It can be used to describe classes, methods, or fields.
 */
```

### Keywords
Java has a set of reserved words (keywords) that have special meanings and cannot be used as identifiers (variable names, class names, etc.). Examples include `public`, `static`, `void`, `class`, `if`, `else`, `for`, `while`, `new`, `this`, `super`, `try`, `catch`, `finally`.

### Case Sensitivity
Java is a **case-sensitive** language. This means `myVariable` and `myvariable` are treated as two different identifiers.

### Naming Conventions (Commonly Followed)
* **Classes:** `PascalCase` (e.g., `MyClass`, `HelloWorld`).
* **Methods and Variables:** `camelCase` (e.g., `myMethod`, `firstName`).
* **Constants:** `UPPER_SNAKE_CASE` (e.g., `MAX_VALUE`, `PI`).
* **Packages:** `lowercase` (e.g., `com.example.myapp`).


---

## Lifecycle of a Java Program


The lifecycle of a Java program involves several distinct stages, from source code to execution, leveraging the Java Virtual Machine (JVM) for platform independence.

### 1. Writing the Source Code
This is the initial stage where a developer writes Java instructions in a text editor or an Integrated Development Environment (IDE). The code is saved in files with a `.java` extension (e.g., `MyProgram.java`).

### 2. Compilation
The Java source code (`.java` files) is compiled into **bytecode** by the **Java Compiler (Javac)**.
* The compiler translates human-readable Java code into a platform-independent intermediate format called bytecode.
* Bytecode files have a `.class` extension (e.g., `MyProgram.class`).
* If there are any syntax errors, the compiler will report them, and the `.class` file will not be generated.

### 3. Loading
When you run a Java program, the **Class Loader** component of the JVM loads the `.class` files into memory.
* It performs three main tasks:
    * **Loading:** Finds and loads the `.class` files from the file system or network.
    * **Linking:**
        * **Verification:** Checks the bytecode for security and correctness.
        * **Preparation:** Allocates memory for static variables and initializes them to default values.
        * **Resolution:** Replaces symbolic references in the bytecode with direct references.
    * **Initialization:** Executes static initializers and static blocks of the class, and assigns actual values to static variables.

### 4. Execution
The loaded bytecode is then executed by the **Java Virtual Machine (JVM)**.
* The JVM interprets the bytecode instruction by instruction.
* **Just-In-Time (JIT) Compiler:** For frequently executed code segments, the JVM's JIT compiler translates bytecode into native machine code at runtime. This machine code is then cached and reused for subsequent executions, significantly improving performance. This is why Java is often considered both interpreted and compiled.

### 5. Runtime Data Areas
During execution, the JVM allocates various runtime data areas (memory regions) to manage program execution:
* **Method Area:** Stores class structures (metadata, constant pool, field and method data, bytecode for methods).
* **Heap:** Used for dynamic memory allocation for objects and arrays. All objects created with `new` reside here.
* **JVM Stacks:** Each thread has its own private JVM stack, used to store local variables, partial results, and to participate in method invocation and return.
* **PC Registers:** Each thread has its own PC (Program Counter) register, which stores the address of the currently executing JVM instruction.
* **Native Method Stacks:** Used to support native methods (methods written in languages other than Java, like C/C++).

### 6. Garbage Collection
Java features automatic memory management through **Garbage Collection**.
* The garbage collector automatically reclaims memory occupied by objects that are no longer referenced by the running program.
* This frees developers from manual memory deallocation, reducing memory leaks and improving program stability.

### 7. Program Termination
The program terminates when:
* The `main` method finishes execution.
* `System.exit()` is called.
* An unhandled exception occurs.

**Simplified Flow:**
Source Code (`.java`) -> (Java Compiler - Javac) -> Bytecode (`.class`) -> (Class Loader) -> (JVM: Bytecode Verifier, JIT Compiler, Runtime Environment) -> Execution


---

## Data Types


Java is a statically typed language, meaning you must declare the data type of a variable before using it. Data types determine the kind of values a variable can hold and the operations that can be performed on it.

### 1. Primitive Data Types
These are the fundamental building blocks and directly hold values. They are predefined by Java and have a fixed size.

* **`byte`:** 8-bit signed integer. Range: -128 to 127. Default value: 0.
    ```java
    byte b = 100;
    ```
* **`short`:** 16-bit signed integer. Range: -32,768 to 32,767. Default value: 0.
    ```java
    short s = 10000;
    ```
* **`int`:** 32-bit signed integer. Range: -2^31 to 2^31-1. Default value: 0. This is the most commonly used integer type.
    ```java
    int i = 50000;
    ```
* **`long`:** 64-bit signed integer. Range: -2^63 to 2^63-1. Used for very large integer values. Default value: 0L.
    ```java
    long l = 15000000000L; // 'L' suffix indicates a long literal
    ```
* **`float`:** 32-bit single-precision floating-point number. Used for decimal numbers with less precision. Default value: 0.0f.
    ```java
    float f = 23.5f; // 'f' suffix indicates a float literal
    ```
* **`double`:** 64-bit double-precision floating-point number. Used for decimal numbers requiring higher precision. This is the default floating-point type. Default value: 0.0d.
    ```java
    double d = 123.456;
    ```
* **`boolean`:** Represents one bit of information. Has only two possible values: `true` and `false`. Default value: `false`.
    ```java
    boolean isJavaFun = true;
    ```
* **`char`:** 16-bit Unicode character. Used to store single characters. Default value: ` ` (null character).
    ```java
    char grade = 'A';
    ```

### 2. Non-Primitive (Reference) Data Types
These are not predefined by Java and are created by the programmer (except for `String`). They do not store the actual values directly but rather references (addresses) to objects in memory.

* **`String`:** A sequence of characters. Although it looks like a primitive type, `String` is a class in Java.
    ```java
    String name = "Alice";
    String message = new String("Hello");
    ```
* **Arrays:** Used to store multiple values of the same data type in a single variable.
    ```java
    int[] numbers = {1, 2, 3, 4, 5};
    String[] names = new String[3];
    ```
* **Classes:** User-defined types that serve as blueprints for creating objects.
    ```java
    // Example: A Car class
    class Car {
        String make;
        String model;
    }
    Car myCar = new Car(); // Creating an object of Car class
    ```
* **Interfaces:** Blueprints of a class. They specify what a class must do, but not how.
* **Enums:** Special "classes" that represent a group of constants (unchangeable variables, like final variables).

**Key Difference:**
* **Primitive types** store values directly in the memory location allocated for the variable.
* **Reference types** store the memory address (reference) where the actual object is stored in the heap.


---

## Variables and Scopes


Variables are named memory locations used to store data. In Java, variables must be declared with a specific data type. Scope defines the region of a program where a variable is accessible.

### Variables
* **Declaration:** Specifying the data type and name of the variable.
    ```java
    int age; // Declares an integer variable named 'age'
    String name; // Declares a String variable named 'name'
    ```
* **Initialization:** Assigning an initial value to a variable.
    ```java
    age = 30; // Initializes 'age'
    name = "Bob"; // Initializes 'name'
    ```
* **Declaration and Initialization:** Can be done in a single statement.
    ```java
    double price = 19.99;
    boolean isActive = true;
    ```
* **Naming Conventions (CamelCase for variables):**
    * Must start with a letter, `_`, or `$`.
    * Cannot start with a number.
    * Are case-sensitive.
    * Should be descriptive.
    * Commonly `camelCase` (e.g., `firstName`, `totalAmount`).

### Scopes in Java
Java defines three main types of variable scopes:

1.  **Local Variables:**
    * **Definition:** Declared inside a method, constructor, or block (e.g., `if` block, `for` loop, `while` loop).
    * **Accessibility:** Only accessible within the method, constructor, or block where they are declared.
    * **Lifecycle:** Created when the method/block is entered and destroyed when the method/block exits.
    * **Initialization:** Must be explicitly initialized before use; Java does not provide default values for local variables.
    ```java
    public class ScopeExample {
        public void myMethod() {
            int localVariable = 10; // Local variable
            System.out.println(localVariable);
        } // localVariable is destroyed here

        public static void main(String[] args) {
            // System.out.println(localVariable); // Compile-time error: localVariable cannot be resolved
        }
    }
    ```

2.  **Instance Variables (Non-Static Fields):**
    * **Definition:** Declared inside a class but outside any method, constructor, or block.
    * **Accessibility:** Accessible by all methods, constructors, and blocks within the same class. They can be accessed from outside the class using an object of that class.
    * **Lifecycle:** Created when an object of the class is instantiated (`new` keyword) and destroyed when the object is garbage-collected.
    * **Initialization:** Java provides default values if not explicitly initialized (e.g., `0` for numeric types, `false` for boolean, `null` for reference types).
    ```java
    public class Car {
        String make; // Instance variable
        int year;    // Instance variable

        public Car(String make, int year) {
            this.make = make; // 'this' refers to the current object's instance variable
            this.year = year;
        }

        public void displayCarInfo() {
            System.out.println("Make: " + make + ", Year: " + year);
        }

        public static void main(String[] args) {
            Car myCar = new Car("Toyota", 2020);
            myCar.displayCarInfo(); // Accessing instance variables via object
        }
    }
    ```

3.  **Static Variables (Class Variables):**
    * **Definition:** Declared inside a class, outside any method, constructor, or block, and marked with the `static` keyword.
    * **Accessibility:** Accessible by all methods, constructors, and blocks within the same class. Can be accessed directly using the class name (e.g., `ClassName.staticVariable`) without creating an object.
    * **Lifecycle:** Created when the class is loaded into memory by the JVM and destroyed when the program terminates. There is only one copy of a static variable per class, regardless of how many objects are created.
    * **Initialization:** Java provides default values if not explicitly initialized.
    ```java
    public class Counter {
        static int count = 0; // Static variable

        public Counter() {
            count++; // Increments the same 'count' for all objects
        }

        public static void main(String[] args) {
            Counter c1 = new Counter();
            Counter c2 = new Counter();
            Counter c3 = new Counter();
            System.out.println("Total objects created: " + Counter.count); // Access via class name
        }
    }
    ```


---

## Type Casting


Type casting in Java is the process of converting a value from one data type to another. This is crucial when you need to perform operations that require specific data types or when handling different types of data.

### Why Type Cast?
* **Compatibility:** To make different data types compatible for operations (e.g., assigning a `long` to an `int`).
* **Data Manipulation:** To perform specific operations that are only available for certain types.
* **API Requirements:** Many methods in Java APIs expect arguments of a particular type.

### Types of Type Casting

Java supports two main types of type casting:

1.  **Widening (Implicit) Type Casting / Automatic Type Conversion:**
    * **Definition:** Converting a smaller data type to a larger data type.
    * **Safety:** This conversion is done automatically by the compiler because there is no loss of data.
    * **Order:** `byte -> short -> char -> int -> long -> float -> double`
    ```java
    public class WideningCasting {
        public static void main(String[] args) {
            int myInt = 9;
            double myDouble = myInt; // Automatic casting: int to double

            System.out.println(myInt);    // Output: 9
            System.out.println(myDouble); // Output: 9.0

            char myChar = 'A';
            int charToInt = myChar; // Automatic casting: char to int (ASCII value)
            System.out.println(charToInt); // Output: 65
        }
    }
    ```

2.  **Narrowing (Explicit) Type Casting / Manual Type Conversion:**
    * **Definition:** Converting a larger data type to a smaller data type.
    * **Safety:** This conversion must be done manually by the programmer because there is a potential loss of data (e.g., converting a `double` to an `int` will truncate the decimal part).
    * **Syntax:** `(targetDataType) valueToConvert`
    ```java
    public class NarrowingCasting {
        public static void main(String[] args) {
            double myDouble = 9.78;
            int myInt = (int) myDouble; // Manual casting: double to int

            System.out.println(myDouble); // Output: 9.78
            System.out.println(myInt);    // Output: 9 (decimal part truncated)

            long myLong = 1234567890123L;
            int longToInt = (int) myLong; // Manual casting: long to int (potential data loss)
            System.out.println(longToInt); // Output: 1215752195 (due to overflow)

            int largeInt = 200;
            byte intToByte = (byte) largeInt; // Manual casting: int to byte (potential data loss)
            System.out.println(intToByte); // Output: -56 (due to overflow)
        }
    }
    ```

### Type Casting with Objects (Polymorphism)
Type casting also applies to objects, especially in the context of inheritance and polymorphism.

* **Upcasting (Implicit):** Converting a subclass object to a superclass type. This is always safe and implicit.
    ```java
    class Animal { void eat() {} }
    class Dog extends Animal { void bark() {} }

    public class ObjectCasting {
        public static void main(String[] args) {
            Dog myDog = new Dog();
            Animal animal = myDog; // Upcasting: Dog to Animal (implicit)
            animal.eat(); // Can call Animal methods
            // animal.bark(); // Compile-time error: Animal type doesn't have bark()
        }
    }
    ```
* **Downcasting (Explicit):** Converting a superclass object to a subclass type. This must be done explicitly and can lead to a `ClassCastException` if the object being cast is not actually an instance of the target subclass.
    ```java
    class Animal { void eat() {} }
    class Dog extends Animal { void bark() {} }
    class Cat extends Animal { void meow() {} }

    public class ObjectCasting {
        public static void main(String[] args) {
            Animal animal = new Dog(); // Upcast initially
            Dog myDog = (Dog) animal; // Downcasting: Animal to Dog (explicit, safe here)
            myDog.bark(); // Can now call Dog methods

            Animal anotherAnimal = new Cat();
            // Dog anotherDog = (Dog) anotherAnimal; // This would compile but throw ClassCastException at runtime
        }
    }
    ```
    To prevent `ClassCastException` during downcasting, it's good practice to use the `instanceof` operator:
    ```java
    if (anotherAnimal instanceof Dog) {
        Dog anotherDog = (Dog) anotherAnimal;
        anotherDog.bark();
    } else {
        System.out.println("anotherAnimal is not a Dog.");
    }
    ```


---

## Classes and Objects


Java is an object-oriented programming (OOP) language, and **classes** and **objects** are its core concepts.

### Classes
* **Blueprint:** A class is a blueprint or a template for creating objects. It defines the structure (attributes/fields) and behavior (methods) that objects of that class will have.
* **Logical Entity:** A class is a logical entity; it does not occupy memory when defined.
* **Syntax:**
    ```java
    public class ClassName {
        // Attributes (variables)
        dataType attributeName;

        // Methods (functions)
        returnType methodName(parameters) {
            // method body
        }
    }
    ```
* **Example:** A `Car` class might define attributes like `make`, `model`, `year` and methods like `start()`, `stop()`.

### Objects
* **Instance:** An object is an instance of a class. It's a real-world entity that has state (values of attributes) and behavior (actions performed by methods).
* **Physical Entity:** An object is a physical entity; it occupies memory when created.
* **Creation:** Objects are created using the `new` keyword, which allocates memory for the object on the heap.
* **Syntax:**
    ```java
    ClassName objectName = new ClassName(); // Using default constructor
    ClassName objectName = new ClassName(arguments); // Using parameterized constructor
    ```
* **Example:** `Car myCar = new Car();` creates an object `myCar` based on the `Car` class. This `myCar` object will have its own `make`, `model`, and `year` values.

### Relationship between Classes and Objects
* A class is like a cookie cutter, and objects are the cookies. You can make many cookies from one cookie cutter.
* Objects are concrete realizations of the abstract definition provided by the class.
* All objects of a class share the same methods but have their own unique values for instance variables (attributes).

```java
// Example: Class and Object
class Dog {
    // Attributes
    String name;
    String breed;

    // Constructor to initialize attributes
    public Dog(String name, String breed) {
        this.name = name;
        this.breed = breed;
    }

    // Method
    public void bark() {
        System.out.println(name + " says Woof!");
    }

    public static void main(String[] args) {
        // Creating objects (instances) of the Dog class
        Dog dog1 = new Dog("Buddy", "Golden Retriever");
        Dog dog2 = new Dog("Lucy", "Labrador");

        // Accessing attributes
        System.out.println(dog1.name + " is a " + dog1.breed); // Output: Buddy is a Golden Retriever
        System.out.println(dog2.name + " is a " + dog2.breed); // Output: Lucy is a Labrador

        // Calling methods
        dog1.bark(); // Output: Buddy says Woof!
        dog2.bark(); // Output: Lucy says Woof!
    }
}
```


---

## Attributes and Methods


Within a Java class, **attributes** (also known as fields or member variables) define the state of an object, while **methods** define its behavior.

### Attributes (Fields/Member Variables)
* **Definition:** Variables declared inside a class but outside any method, constructor, or block. They represent the characteristics or properties of an object.
* **State:** Attributes hold the data that defines the current state of an object. Each object will have its own set of instance attribute values.
* **Types:**
    * **Instance Variables:** Unique to each object. Declared without the `static` keyword.
    * **Static Variables (Class Variables):** Shared by all objects of the class. Declared with the `static` keyword. (See "Static Keyword" section for more details).
* **Declaration Syntax:**
    ```java
    class MyClass {
        dataType instanceVariable; // Instance variable
        static dataType staticVariable; // Static variable
    }
    ```
* **Access:**
    * Instance variables are accessed using an object: `objectName.instanceVariable`.
    * Static variables are accessed using the class name: `ClassName.staticVariable`.

### Methods
* **Definition:** Blocks of code that perform a specific task. They define the actions or behaviors that an object can perform.
* **Behavior:** Methods operate on the object's attributes or interact with other objects.
* **Syntax:**
    ```java
    accessModifier returnType methodName(parameterList) {
        // method body
        // statements
        return value; // if returnType is not void
    }
    ```
    * `accessModifier`: (e.g., `public`, `private`, `protected`, default) controls visibility.
    * `returnType`: The data type of the value the method returns (e.g., `int`, `String`, `void` if nothing is returned).
    * `methodName`: The name of the method (camelCase convention).
    * `parameterList`: A comma-separated list of input values the method accepts (optional).
* **Types:**
    * **Instance Methods:** Operate on instance variables and can be called only on an object.
    * **Static Methods (Class Methods):** Operate on static variables and can be called directly on the class. They cannot access instance variables directly. (See "Static Keyword" section for more details).
    * **Constructors:** Special methods used to initialize objects when they are created. They have the same name as the class and no return type.

```java
// Example: Attributes and Methods
public class BankAccount {
    // Attributes (Instance Variables)
    String accountNumber;
    double balance;

    // Constructor
    public BankAccount(String accNum, double initialBalance) {
        this.accountNumber = accNum;
        this.balance = initialBalance;
        System.out.println("Account " + accountNumber + " created with balance: " + balance);
    }

    // Method to deposit money (Instance Method)
    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
            System.out.println("Deposited: " + amount + ", New balance: " + balance);
        } else {
            System.out.println("Deposit amount must be positive.");
        }
    }

    // Method to withdraw money (Instance Method)
    public void withdraw(double amount) {
        if (amount > 0 && balance >= amount) {
            balance -= amount;
            System.out.println("Withdrew: " + amount + ", New balance: " + balance);
        } else if (amount <= 0) {
            System.out.println("Withdrawal amount must be positive.");
        } else {
            System.out.println("Insufficient balance. Current balance: " + balance);
        }
    }

    // Method to get balance (Instance Method)
    public double getBalance() {
        return balance;
    }

    public static void main(String[] args) {
        BankAccount myAccount = new BankAccount("12345", 1000.0);
        myAccount.deposit(500.0);
        myAccount.withdraw(200.0);
        System.out.println("Final balance for " + myAccount.accountNumber + ": " + myAccount.getBalance());
    }
}
```


---

## Access Specifiers


Access specifiers (or access modifiers) in Java control the visibility and accessibility of classes, fields (attributes), constructors, and methods. They are crucial for implementing encapsulation, a core OOP principle.

Java has four access specifiers:

1.  **`public`:**
    * **Visibility:** Accessible from anywhere (within the same class, same package, subclasses, and different packages).
    * **Usage:** Typically used for methods and fields that need to be accessible from outside the class or package, especially for public APIs.
    ```java
    // Example: public class, method, and field
    package com.example.app;

    public class PublicExample {
        public int publicField = 10;

        public void publicMethod() {
            System.out.println("This is a public method.");
        }
    }
    ```java
    // In another package:
    // import com.example.app.PublicExample;
    // PublicExample obj = new PublicExample();
    // System.out.println(obj.publicField);
    // obj.publicMethod();
    ```

2.  **`private`:**
    * **Visibility:** Accessible only within the class where it is declared.
    * **Usage:** Primarily used for fields to enforce encapsulation. This means the internal state of an object can only be accessed or modified through public methods (getters and setters), preventing direct external manipulation.
    ```java
    // Example: private field and method
    public class PrivateExample {
        private String privateData = "Secret"; // private field

        private void privateMethod() { // private method
            System.out.println("This is a private method.");
        }

        // Public method to access private data (getter)
        public String getPrivateData() {
            privateMethod(); // Can call private method from within the class
            return privateData;
        }
    }
    ```java
    // In main method or another class:
    // PrivateExample obj = new PrivateExample();
    // System.out.println(obj.getPrivateData()); // OK
    // System.out.println(obj.privateData); // Compile-time error
    // obj.privateMethod(); // Compile-time error
    ```

3.  **`protected`:**
    * **Visibility:** Accessible within the same package and by subclasses (even if the subclasses are in different packages).
    * **Usage:** Used when you want to allow subclasses to access certain members while restricting access from unrelated classes in different packages.
    ```java
    // Example: protected field and method
    package com.example.base;

    public class ProtectedExample {
        protected String protectedData = "Protected Info";

        protected void protectedMethod() {
            System.out.println("This is a protected method.");
        }
    }
    ```java
    // In a subclass in a different package:
    package com.example.derived;
    import com.example.base.ProtectedExample;

    public class SubclassExample extends ProtectedExample {
        public void accessProtected() {
            System.out.println(protectedData); // Accessible
            protectedMethod(); // Accessible
        }

        public static void main(String[] args) {
            SubclassExample obj = new SubclassExample();
            obj.accessProtected();
        }
    }
    ```java
    // In a non-subclass in a different package:
    // import com.example.base.ProtectedExample;
    // ProtectedExample obj = new ProtectedExample();
    // System.out.println(obj.protectedData); // Compile-time error
    ```

4.  **Default (No Modifier) / Package-Private:**
    * **Visibility:** Accessible only within the same package. If you don't specify any access modifier, it's considered default.
    * **Usage:** Useful for classes or members that are part of an internal implementation of a package and should not be exposed to other packages.
    ```java
    // Example: Default access
    package com.example.util;

    class DefaultExample { // Class with default access
        String defaultField = "Default Info"; // Field with default access

        void defaultMethod() { // Method with default access
            System.out.println("This is a default method.");
        }
    }
    ```java
    // In the same package (com.example.util):
    // public class AnotherClassInSamePackage {
    //     public static void main(String[] args) {
    //         DefaultExample obj = new DefaultExample();
    //         System.out.println(obj.defaultField); // Accessible
    //         obj.defaultMethod(); // Accessible
    //     }
    // }
    ```java
    // In a different package:
    // import com.example.util.DefaultExample; // Compile-time error: DefaultExample is not public
    ```

**Summary Table:**

| Modifier  | Same Class | Same Package | Subclass (different package) | Other Package |
| :-------- | :--------- | :----------- | :--------------------------- | :------------ |
| `private` | Yes        | No           | No                           | No            |
| Default   | Yes        | Yes          | No                           | No            |
| `protected`| Yes        | Yes          | Yes                          | No            |
| `public`  | Yes        | Yes          | Yes                          | Yes           |


---

## Static Keyword


The `static` keyword in Java is a non-access modifier used for members that belong to the class itself, rather than to any specific object of the class. A single copy of static members is created and shared among all instances of the class.

### 1. Static Variables (Class Variables)
* **Definition:** A variable declared with the `static` keyword inside a class but outside any method, constructor, or block.
* **Memory:** Static variables are stored in the Method Area (part of the Heap in modern JVMs) and are created only once when the class is loaded.
* **Shared:** All objects of the class share the same copy of the static variable. Changes made by one object are visible to all others.
* **Access:** Accessed using the class name, not an object reference (e.g., `ClassName.staticVariable`).
* **Use Case:** Common for constants or properties that are common to all instances (e.g., `Math.PI`, a counter for the number of objects created).

```java
public class Employee {
    String name;
    int id;
    static String companyName = "ABC Corp"; // Static variable

    public Employee(String name, int id) {
        this.name = name;
        this.id = id;
    }

    public void displayInfo() {
        System.out.println("Name: " + name + ", ID: " + id + ", Company: " + companyName);
    }

    public static void main(String[] args) {
        Employee emp1 = new Employee("Alice", 101);
        Employee emp2 = new Employee("Bob", 102);

        emp1.displayInfo(); // Output: Name: Alice, ID: 101, Company: ABC Corp
        emp2.displayInfo(); // Output: Name: Bob, ID: 102, Company: ABC Corp

        // Changing static variable affects all instances
        Employee.companyName = "XYZ Inc.";
        emp1.displayInfo(); // Output: Name: Alice, ID: 101, Company: XYZ Inc.
    }
}
```

### 2. Static Methods (Class Methods)
* **Definition:** A method declared with the `static` keyword.
* **Access:** Can be called directly on the class name without creating an object (e.g., `ClassName.staticMethod()`).
* **Restrictions:**
    * A static method can access only static data members (variables) and can call only other static methods.
    * It cannot use `this` or `super` keywords (as `this` refers to the current object, and static methods don't operate on specific objects).
    * It cannot access instance (non-static) variables or methods directly.
* **Use Case:** Utility methods that don't depend on the state of an object (e.g., `Math.max()`, `Integer.parseInt()`).

```java
public class Calculator {
    static int add(int a, int b) { // Static method
        return a + b;
    }

    public static void main(String[] args) {
        int sum = Calculator.add(5, 3); // Calling static method using class name
        System.out.println("Sum: " + sum); // Output: Sum: 8
    }
}
```

### 3. Static Blocks
* **Definition:** A block of code inside a class, preceded by the `static` keyword.
* **Execution:** Executed exactly once, when the class is loaded into the JVM, even before the `main` method or any object creation.
* **Use Case:** Used to initialize static variables or perform any one-time setup that is required for the class.

```java
public class StaticBlockExample {
    static {
        System.out.println("Static block executed: This runs once when the class is loaded.");
    }

    public StaticBlockExample() {
        System.out.println("Constructor executed: An object is created.");
    }

    public static void main(String[] args) {
        System.out.println("Main method started.");
        StaticBlockExample obj1 = new StaticBlockExample();
        StaticBlockExample obj2 = new StaticBlockExample();
        System.out.println("Main method finished.");
    }
}
/*
Output:
Static block executed: This runs once when the class is loaded.
Main method started.
Constructor executed: An object is created.
Constructor executed: An object is created.
Main method finished.
*/
```

### 4. Static Nested Classes
* **Definition:** A nested class declared with the `static` keyword.
* **Access:** Can be accessed directly using the outer class name without needing an instance of the outer class.
* **Restrictions:** Can only access static members of the outer class. (See "Nested Classes" section for more details).


---

## Final Keyword


The `final` keyword in Java is a non-access modifier used to restrict the user. It can be applied to variables, methods, and classes.

### 1. `final` Variable
* **Definition:** A variable declared with the `final` keyword.
* **Immutability:** Once a `final` variable is initialized, its value cannot be changed. It becomes a constant.
* **Initialization:** A `final` variable must be initialized either at the time of declaration or within a constructor (for instance `final` variables) or a static block (for static `final` variables).
* **Naming Convention:** For static `final` variables (constants), the convention is `UPPER_SNAKE_CASE`.

```java
public class FinalVariableExample {
    final int SPEED_LIMIT = 90; // final instance variable, initialized at declaration
    final String MY_NAME; // final instance variable, not initialized here

    static final double PI = 3.14159; // static final variable (constant)

    public FinalVariableExample() {
        MY_NAME = "John Doe"; // Initializing final variable in constructor
        // SPEED_LIMIT = 100; // Compile-time error: cannot assign a value to final variable
    }

    public void display() {
        System.out.println("Speed Limit: " + SPEED_LIMIT);
        System.out.println("My Name: " + MY_NAME);
        System.out.println("PI: " + PI);
    }

    public static void main(String[] args) {
        FinalVariableExample obj = new FinalVariableExample();
        obj.display();
        // PI = 3.14; // Compile-time error: cannot assign a value to final variable
    }
}
```

### 2. `final` Method
* **Definition:** A method declared with the `final` keyword.
* **No Overriding:** A `final` method cannot be overridden by any subclass. This is used to prevent unwanted modifications to the behavior defined in the superclass.
* **Use Case:** Ensures that a particular implementation of a method remains consistent across the inheritance hierarchy.

```java
class Vehicle {
    final void run() { // final method
        System.out.println("Vehicle is running.");
    }
}

class Car extends Vehicle {
    // void run() { // Compile-time error: cannot override final method from Vehicle
    //     System.out.println("Car is running.");
    // }

    public static void main(String[] args) {
        Car myCar = new Car();
        myCar.run(); // Output: Vehicle is running.
    }
}
```

### 3. `final` Class
* **Definition:** A class declared with the `final` keyword.
* **No Inheritance:** A `final` class cannot be inherited by any other class. This means no other class can extend it.
* **Use Case:** Used to create immutable classes (like `String`, `Integer`, etc., in Java's standard library) or to prevent security vulnerabilities by ensuring that the implementation cannot be altered by subclasses.

```java
final class ImmutableClass { // final class
    private final int value;

    public ImmutableClass(int value) {
        this.value = value;
    }

    public int getValue() {
        return value;
    }
}

// class SubClass extends ImmutableClass { // Compile-time error: cannot inherit from final class
// }

public class FinalClassExample {
    public static void main(String[] args) {
        ImmutableClass obj = new ImmutableClass(100);
        System.out.println("Value: " + obj.getValue()); // Output: Value: 100
    }
}
```


---

## Nested Classes


In Java, a **nested class** is a class defined within another class. Nested classes help in logically grouping classes that are only used in one place, increasing encapsulation, and making the code more readable and maintainable.

There are two main types of nested classes:

### 1. Static Nested Class
* **Definition:** A nested class declared with the `static` modifier.
* **Behavior:**
    * Behaves like a static member of the outer class.
    * Can be accessed directly using the outer class name without creating an instance of the outer class.
    * Can only access static members (fields and methods) of the outer class directly. To access non-static members of the outer class, it needs an instance of the outer class.
* **Use Case:** When the nested class is logically grouped with the outer class but does not need to access the outer class's instance members. Often used for utility classes or helper classes.

```java
public class OuterClass {
    private static String outerStaticField = "Outer Static Data";
    private String outerInstanceField = "Outer Instance Data";

    public static class StaticNestedClass { // Static nested class
        public void display() {
            System.out.println("Accessing outer static field: " + outerStaticField);
            // System.out.println(outerInstanceField); // Compile-time error: cannot access non-static field
        }

        public void displayWithOuterInstance(OuterClass outer) {
            System.out.println("Accessing outer instance field via outer object: " + outer.outerInstanceField);
        }
    }

    public static void main(String[] args) {
        // Creating an object of Static Nested Class
        OuterClass.StaticNestedClass staticNestedObj = new OuterClass.StaticNestedClass();
        staticNestedObj.display(); // Output: Accessing outer static field: Outer Static Data

        OuterClass outerObj = new OuterClass();
        staticNestedObj.displayWithOuterInstance(outerObj); // Output: Accessing outer instance field via outer object: Outer Instance Data
    }
}
```

### 2. Inner Classes (Non-Static Nested Classes)
Inner classes are non-static members of the outer class. They are further categorized into:

* **a. Member Inner Class:**
    * **Definition:** A non-static class defined inside another class.
    * **Behavior:**
        * Requires an instance of the outer class to be instantiated.
        * Can access all members (static and non-static) of the outer class directly, including private members.
        * Each instance of the inner class is implicitly associated with an instance of the outer class.
    * **Use Case:** When the inner class needs to directly interact with the instance members of the outer class.

    ```java
    public class OuterClassMember {
        private String msg = "Hello from OuterClassMember";

        class InnerClass { // Member Inner Class
            public void display() {
                System.out.println(msg); // Can access outer class's instance field directly
            }
        }

        public static void main(String[] args) {
            OuterClassMember outer = new OuterClassMember();
            OuterClassMember.InnerClass inner = outer.new InnerClass(); // Creating inner class object
            inner.display(); // Output: Hello from OuterClassMember
        }
    }
    ```

* **b. Local Inner Class:**
    * **Definition:** A class defined inside a method, constructor, or block.
    * **Behavior:**
        * Its scope is restricted to the block where it is defined.
        * Cannot be declared with access modifiers (`public`, `private`, etc.) or `static`.
        * Can access final or effectively final local variables of the enclosing block.
    * **Use Case:** When a class is needed only within a single method or block.

    ```java
    public class LocalInnerClassExample {
        public void displayMessage() {
            final String message = "Hello from Local Inner Class"; // Effectively final

            class LocalInner { // Local Inner Class
                public void printMessage() {
                    System.out.println(message); // Accessing effectively final local variable
                }
            }

            LocalInner local = new LocalInner();
            local.printMessage(); // Output: Hello from Local Inner Class
        }

        public static void main(String[] args) {
            LocalInnerClassExample obj = new LocalInnerClassExample();
            obj.displayMessage();
        }
    }
    ```

* **c. Anonymous Inner Class:**
    * **Definition:** An inner class without a name. It is declared and instantiated in a single expression.
    * **Behavior:**
        * Used to override a method of a class or an interface.
        * Can implement an interface or extend a class.
        * Cannot have constructors.
    * **Use Case:** For implementing an interface or abstract class with a single method, or for creating a one-time use object.

    ```java
    interface Greeting {
        void greet();
    }

    public class AnonymousInnerClassExample {
        public static void main(String[] args) {
            // Anonymous inner class implementing the Greeting interface
            Greeting englishGreeting = new Greeting() {
                @Override
                public void greet() {
                    System.out.println("Hello!");
                }
            };
            englishGreeting.greet(); // Output: Hello!

            // Anonymous inner class extending a class
            Thread myThread = new Thread(new Runnable() {
                @Override
                public void run() {
                    System.out.println("Thread running from anonymous class.");
                }
            });
            myThread.start(); // Output: Thread running from anonymous class.
        }
    }
    ```


---

## Packages


**Packages** in Java are a mechanism to organize classes, interfaces, and sub-packages into logical groups. They provide a way to modularize code, prevent naming conflicts, and control access.

### Why Use Packages?
1.  **Organization:** Helps in organizing related classes and interfaces into a single unit.
2.  **Naming Conflict Resolution:** Allows classes with the same name to exist in different packages without conflict (e.g., `java.util.List` and `java.awt.List`).
3.  **Access Control:** Packages provide a level of access protection (default/package-private access).
4.  **Modularity:** Makes it easier to manage large projects by breaking them down into smaller, manageable modules.

### Creating a Package
* A package is declared using the `package` keyword as the first statement in a Java source file (before any `import` statements or class definitions).
* The package name usually follows a reverse domain name convention (e.g., `com.example.myapp`).
* The directory structure on your file system must match the package structure.

```java
// File: com/example/myapp/MyClass.java
package com.example.myapp; // Package declaration

public class MyClass {
    public void display() {
        System.out.println("Hello from MyClass in com.example.myapp package!");
    }
}
```

### Importing Packages
To use classes from another package, you need to import them using the `import` keyword.

1.  **Importing a specific class:**
    ```java
    import java.util.ArrayList; // Imports only the ArrayList class

    public class MyProgram {
        public static void main(String[] args) {
            ArrayList<String> list = new ArrayList<>();
            list.add("Item 1");
            System.out.println(list);
        }
    }
    ```
2.  **Importing all classes from a package (wildcard import):**
    ```java
    import java.util.*; // Imports all classes within the java.util package

    public class MyProgram {
        public static void main(String[] args) {
            ArrayList<String> list = new ArrayList<>();
            HashMap<String, Integer> map = new HashMap<>();
            // ... other classes from java.util
        }
    }
    ```
    * **Note:** While convenient, wildcard imports can sometimes lead to ambiguity if two packages have classes with the same name.
3.  **Fully Qualified Name:** If you don't import, you can use the fully qualified name of the class.
    ```java
    public class MyProgram {
        public static void main(String[] args) {
            java.util.ArrayList<String> list = new java.util.ArrayList<>();
            list.add("Item 1");
            System.out.println(list);
        }
    }
    ```

### Subpackages
Packages can contain other packages, forming a hierarchy.
* `java.util` contains `java.util.concurrent`, `java.util.function`, etc.
* Importing `java.util.*` does *not* import classes from `java.util.concurrent`. You need to import subpackages explicitly.

### Default Package
If you don't specify a `package` statement in your Java source file, the classes are considered to be in the "default package" (also known as the unnamed package). This is generally discouraged for larger projects.

### `CLASSPATH`
The Java Virtual Machine (JVM) and Java compiler (Javac) use the `CLASSPATH` environment variable to locate classes and packages. It's a path that tells the JVM where to look for `.class` files. Modern build tools (like Maven, Gradle) and IDEs (like IntelliJ, Eclipse) manage the classpath automatically, so manual configuration is less common.


---

