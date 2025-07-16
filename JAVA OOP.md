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

## More about OOP


Object-Oriented Programming (OOP) is a programming paradigm based on the concept of "objects", which can contain data and code. Java is a strongly object-oriented language, and OOP principles are fundamental to its design.

The four main pillars of OOP are:

### 1. Encapsulation
* **Definition:** The bundling of data (attributes) and the methods (functions) that operate on the data into a single unit (class). It also involves restricting direct access to some of an object's components, which is achieved through access specifiers (`private`, `protected`, `public`, default).
* **Purpose:**
    * **Data Hiding:** Protects the internal state of an object from unauthorized external access.
    * **Maintainability:** Changes to the internal implementation of a class do not affect external code as long as the public interface remains consistent.
    * **Control:** Allows controlled access to data through public getter and setter methods.
* **Example:** A `BankAccount` class with a `private` `balance` attribute, accessible only through `public` `deposit()` and `withdraw()` methods. (See "Encapsulation" section for more details).

### 2. Inheritance
* **Definition:** A mechanism where one class (subclass/child class) acquires the properties (attributes and methods) of another class (superclass/parent class). It promotes code reusability.
* **Keyword:** `extends`
* **Purpose:**
    * **Code Reusability:** Avoids duplicating code by allowing subclasses to reuse methods and fields from their superclass.
    * **IS-A Relationship:** Represents a hierarchical relationship where a subclass "is a" type of its superclass (e.g., a `Car` IS-A `Vehicle`).
* **Example:** A `Car` class inheriting from a `Vehicle` class, reusing `start()` and `stop()` methods. (See "Inheritance" section for more details).

### 3. Polymorphism
* **Definition:** The ability of an object to take on many forms. In Java, it typically refers to the ability of an object to pass different types of objects to a method or function, or to have a single interface for different underlying data types.
* **Types:**
    * **Compile-time Polymorphism (Method Overloading):** Achieved by having multiple methods with the same name but different parameters within the same class. (See "Method Overloading / Overriding" section for more details).
    * **Runtime Polymorphism (Method Overriding):** Achieved when a subclass provides a specific implementation for a method that is already defined in its superclass. This is resolved at runtime by the JVM. (See "Method Overloading / Overriding" section for more details).
* **Purpose:**
    * **Flexibility:** Allows a single interface to represent different underlying implementations.
    * **Extensibility:** New types can be added without modifying existing code.
* **Example:** An `Animal` class with an `eat()` method, and `Dog` and `Cat` subclasses overriding `eat()` to provide their specific eating behavior.

### 4. Abstraction
* **Definition:** The process of hiding the implementation details and showing only the essential features of an object to the user. It focuses on "what" an object does rather than "how" it does it.
* **Achieved By:**
    * **Abstract Classes:** Classes that cannot be instantiated directly and may contain abstract methods (methods without an implementation).
    * **Interfaces:** Blueprints of a class that contain only abstract methods (before Java 8) or default/static methods (from Java 8 onwards).
* **Purpose:**
    * **Simplicity:** Reduces complexity by hiding unnecessary details.
    * **Security:** Prevents users from accessing or modifying internal implementation.
    * **Framework Design:** Provides a common interface for different implementations.
* **Example:** An `abstract Shape` class with an `abstract calculateArea()` method, implemented by concrete `Circle` and `Rectangle` classes. (See "Abstraction" and "Interfaces" sections for more details).

These four pillars work together to create robust, flexible, and maintainable software systems in Java.


---

## Object Lifecycle


The lifecycle of an object in Java refers to the stages an object goes through from its creation to its destruction. This process is managed by the Java Virtual Machine (JVM), particularly its garbage collector.

### 1. Creation (Instantiation)
* **Action:** An object is created in memory.
* **Steps:**
    1.  **Declaration:** A reference variable is declared.
        ```java
        ClassName objectName;
        ```
    2.  **Instantiation:** Memory is allocated for the object on the heap using the `new` keyword.
        ```java
        objectName = new ClassName();
        ```
    3.  **Initialization:** The constructor of the class is called to initialize the object's instance variables.
        ```java
        ClassName objectName = new ClassName(arguments);
        ```
    * **Memory:** Objects reside in the **Heap** memory area.

### 2. In Use (Reachable)
* **Action:** The object is actively being used by the program.
* **State:** The object is considered "reachable" if there is at least one active reference pointing to it.
* **Operations:** Methods are called on the object, and its attributes are accessed or modified.

### 3. Unreachable (Eligible for Garbage Collection)
* **Action:** An object becomes unreachable when there are no longer any active references pointing to it.
* **Conditions for Unreachability:**
    * **Nulling the reference:** `objectName = null;`
    * **Reassigning the reference:** `objectName = anotherObject;`
    * **Object created inside a method:** When the method completes execution, local references to the object are removed.
    * **Island of Isolation:** Two or more objects refer to each other, but none of them are referenced by any active part of the program.
* **Eligibility:** Once an object is unreachable, it becomes eligible for garbage collection. It does *not* mean it is immediately destroyed.

### 4. Garbage Collection
* **Action:** The JVM's Garbage Collector (GC) identifies unreachable objects and reclaims the memory they occupy.
* **Automatic Process:** Garbage collection is an automatic background process in Java. Developers do not explicitly destroy objects.
* **`finalize()` method:** Before an object is garbage collected, the JVM calls its `finalize()` method (if overridden). This method is intended for performing cleanup operations, but its execution is not guaranteed and it should generally be avoided in modern Java development in favor of `try-with-resources` or explicit resource management.
* **Memory:** The memory reclaimed is returned to the Heap, making it available for new object creation.

### 5. De-allocation (Destruction)
* **Action:** The memory occupied by the object is de-allocated.
* **Timing:** The exact timing of garbage collection is determined by the JVM's garbage collector algorithm and cannot be precisely controlled by the programmer.

**Simplified Object Lifecycle Flow:**
Declaration -> Instantiation (`new`) -> Initialization (Constructor) -> In Use (Reachable) -> Unreachable -> Eligible for GC -> Garbage Collection -> De-allocation


---

## Inheritance


**Inheritance** is one of the fundamental pillars of Object-Oriented Programming (OOP) in Java. It is a mechanism where one class acquires the properties (attributes/fields and methods) of another class.

### Key Concepts
* **Parent Class / Superclass / Base Class:** The class whose properties are inherited.
* **Child Class / Subclass / Derived Class:** The class that inherits properties from the parent class.
* **`extends` Keyword:** Used to establish an inheritance relationship. A subclass `extends` a superclass.
    ```java
    class Subclass extends Superclass {
        // ...
    }
    ```
* **IS-A Relationship:** Inheritance represents an "IS-A" relationship. For example, a `Car` IS-A `Vehicle`, a `Dog` IS-A `Animal`.

### Benefits of Inheritance
1.  **Code Reusability:** The most significant benefit. Common code (fields and methods) can be defined in a superclass and reused by multiple subclasses, avoiding duplication.
2.  **Method Overriding (Runtime Polymorphism):** Subclasses can provide their specific implementation for a method already defined in the superclass.
3.  **Extensibility:** New functionalities can be added to existing classes by extending them.
4.  **Maintainability:** Changes in the superclass automatically propagate to subclasses (unless overridden), simplifying maintenance.

### Types of Inheritance (in Java)
Java primarily supports **single inheritance** (a class can extend only one direct superclass). However, it achieves the benefits of multiple inheritance through **interfaces**.

* **Single Inheritance:** A class inherits from only one direct superclass.
    ```java
    class A { /* ... */ }
    class B extends A { /* ... */ } // B inherits from A
    ```
* **Multilevel Inheritance:** A class inherits from another class, which in turn inherits from another class.
    ```java
    class A { /* ... */ }
    class B extends A { /* ... */ }
    class C extends B { /* ... */ } // C inherits from B, which inherits from A
    ```
* **Hierarchical Inheritance:** Multiple subclasses inherit from a single superclass.
    ```java
    class A { /* ... */ }
    class B extends A { /* ... */ }
    class C extends A { /* ... */ } // B and C both inherit from A
    ```
* **Multiple Inheritance (via Interfaces):** Java does not support multiple inheritance of classes (a class cannot extend more than one class) to avoid the "diamond problem." However, a class can implement multiple interfaces.
    ```java
    interface Interface1 { /* ... */ }
    interface Interface2 { /* ... */ }
    class MyClass implements Interface1, Interface2 { /* ... */ }
    ```
* **Hybrid Inheritance:** A combination of two or more types of inheritance. Since Java doesn't support multiple inheritance of classes, hybrid inheritance involving multiple class inheritance is not directly possible.

### What is Inherited?
* **Fields (Attributes):** All non-private fields are inherited. Private fields are not directly accessible but can be accessed through public/protected getter/setter methods in the superclass.
* **Methods:** All non-private methods are inherited. Private methods are not inherited.
* **Constructors:** Constructors are *not* inherited. However, a subclass constructor implicitly or explicitly calls a superclass constructor using `super()`.

### `super` Keyword
The `super` keyword is used to refer to the immediate parent class object.
* `super.variable`: Refers to the superclass's instance variable.
* `super.method()`: Calls the superclass's method.
* `super(arguments)`: Calls the superclass's constructor.

```java
// Example: Inheritance
class Vehicle {
    String brand = "Generic Brand"; // Superclass attribute

    public void honk() { // Superclass method
        System.out.println("Honk, Honk!");
    }
}

class Car extends Vehicle { // Car is a subclass of Vehicle
    String model = "Sedan"; // Subclass attribute

    public void displayInfo() {
        System.out.println("Brand: " + brand); // Accessing inherited attribute
        System.out.println("Model: " + model);
    }

    @Override // Annotation indicating method overriding
    public void honk() {
        super.honk(); // Calls the honk() method of the superclass
        System.out.println("Car specific honk!");
    }

    public static void main(String[] args) {
        Car myCar = new Car();
        myCar.displayInfo();
        myCar.honk(); // Calls the overridden honk() method in Car
    }
}
/*
Output:
Brand: Generic Brand
Model: Sedan
Honk, Honk!
Car specific honk!
*/
```


---

## Abstraction


**Abstraction** is one of the four fundamental pillars of Object-Oriented Programming (OOP). It is the process of hiding the implementation details and showing only the essential features or functionalities to the user. The focus is on "what" an object does rather than "how" it does it.

### Key Concepts
* **Hiding Complexity:** Abstraction simplifies complex systems by presenting a higher-level view, allowing users to interact with objects without needing to understand their intricate internal workings.
* **Focus on Interface:** It emphasizes the interface (what is exposed to the user) over the implementation (how it works internally).
* **Achieved By:**
    * **Abstract Classes**
    * **Interfaces**

### 1. Abstract Classes
* **Definition:** A class declared with the `abstract` keyword.
* **Instantiation:** Cannot be instantiated directly (i.e., you cannot create an object of an abstract class using `new`).
* **Abstract Methods:** Can have abstract methods (methods declared with `abstract` keyword and no body) and concrete methods (methods with implementation).
* **Inheritance:** If a class contains an abstract method, it must be declared abstract. If a subclass extends an abstract class, it must either implement all its abstract methods or also be declared abstract.
* **Purpose:** To provide a common base for related subclasses, defining a common interface while allowing specific implementations to vary.

```java
// Example: Abstract Class
abstract class Shape { // Abstract class
    String color;

    // Abstract method (no body)
    public abstract double calculateArea();

    // Concrete method
    public void displayColor() {
        System.out.println("Shape color: " + color);
    }

    // Constructor
    public Shape(String color) {
        this.color = color;
    }
}

class Circle extends Shape {
    double radius;

    public Circle(String color, double radius) {
        super(color);
        this.radius = radius;
    }

    @Override
    public double calculateArea() { // Implementation of abstract method
        return Math.PI * radius * radius;
    }
}

class Rectangle extends Shape {
    double length;
    double width;

    public Rectangle(String color, double length, double width) {
        super(color);
        this.length = length;
        this.width = width;
    }

    @Override
    public double calculateArea() { // Implementation of abstract method
        return length * width;
    }
}

public class AbstractionExample {
    public static void main(String[] args) {
        // Shape s = new Shape("Red"); // Compile-time error: Cannot instantiate abstract class

        Shape circle = new Circle("Blue", 5.0);
        Shape rectangle = new Rectangle("Green", 4.0, 6.0);

        circle.displayColor(); // Output: Shape color: Blue
        System.out.println("Circle Area: " + circle.calculateArea()); // Output: Circle Area: 78.53...

        rectangle.displayColor(); // Output: Shape color: Green
        System.out.println("Rectangle Area: " + rectangle.calculateArea()); // Output: Rectangle Area: 24.0
    }
}
```

### 2. Interfaces
* **Definition:** A blueprint of a class. It contains abstract methods (implicitly `public abstract` before Java 8), and from Java 8 onwards, it can also contain `default` and `static` methods. From Java 9, `private` methods are also allowed.
* **Implementation:** Classes `implement` interfaces using the `implements` keyword. A class can implement multiple interfaces.
* **Purpose:** To achieve full abstraction and multiple inheritance of type. It defines a contract that implementing classes must adhere to.

(See "Interfaces" section for more details).

### Benefits of Abstraction
* **Reduces Complexity:** Hides internal implementation details, making the system easier to understand and use.
* **Enhances Security:** Prevents unauthorized access to sensitive data and methods.
* **Facilitates Maintenance and Evolution:** Changes to implementation details don't affect the public interface, allowing for easier updates.
* **Promotes Reusability:** Abstract classes and interfaces define common behavior that can be reused across different concrete implementations.
* **Supports Polymorphism:** Enables runtime polymorphism, allowing a single interface to represent different implementations.


---

## Method Chaining


**Method chaining** (also known as fluent interface) is a programming technique that allows multiple method calls to be linked together in a single statement. This is achieved by having each method return the object itself (`this`), allowing the next method to be called on the result of the previous call.

### How it Works
For method chaining to work, each method in the chain (except possibly the last one) must return a reference to the current object (`this`).

```java
public class StringBuilderExample {
    public static void main(String[] args) {
        // Example of method chaining with StringBuilder
        StringBuilder sb = new StringBuilder();
        sb.append("Hello")
          .append(" ")
          .append("World")
          .insert(6, "Java "); // Each method returns StringBuilder itself

        System.out.println(sb.toString()); // Output: Hello Java World
    }
}
```
In the `StringBuilder` example above, `append()` and `insert()` methods return `this` (the `StringBuilder` object), allowing you to call another method directly on the returned object.

### Benefits
* **Readability:** Makes code more concise and easier to read, especially when performing a sequence of operations on the same object.
* **Conciseness:** Reduces the need for intermediate variables.
* **Fluent API Design:** Enables the creation of APIs that read like natural language.

### Implementing Method Chaining
To implement method chaining in your own classes, simply ensure that the methods you want to chain return `this` (the current object).

```java
public class Calculator {
    private double result;

    public Calculator() {
        this.result = 0.0;
    }

    public Calculator add(double value) {
        this.result += value;
        return this; // Return 'this' for chaining
    }

    public Calculator subtract(double value) {
        this.result -= value;
        return this; // Return 'this' for chaining
    }

    public Calculator multiply(double value) {
        this.result *= value;
        return this; // Return 'this' for chaining
    }

    public double getResult() {
        return this.result; // The last method can return the final result
    }

    public static void main(String[] args) {
        Calculator calc = new Calculator();
        double finalResult = calc.add(10)
                                 .subtract(2)
                                 .multiply(3)
                                 .getResult(); // Chaining methods

        System.out.println("Final Result: " + finalResult); // Output: Final Result: 24.0
    }
}
```

### Considerations
* **Return Type:** Ensure that the methods intended for chaining have the correct return type (the class itself).
* **Side Effects:** Be mindful of the order of operations, as each method call modifies the state of the object.
* **Debugging:** Chained calls can sometimes be slightly harder to debug if an error occurs in the middle of a long chain, as the stack trace might point to the entire line rather than a specific method in the chain. However, most modern IDEs provide good debugging support for this.


---

## Encapsulation


**Encapsulation** is one of the four fundamental pillars of Object-Oriented Programming (OOP) in Java. It is the mechanism of bundling data (attributes/fields) and the methods (functions) that operate on that data into a single unit, which is the class. It also involves restricting direct access to some of an object's components.

### Key Concepts
* **Bundling:** Combining data and methods that work on that data into a single unit (a class).
* **Data Hiding:** Protecting the internal state of an object from direct external access. This is achieved by declaring attributes as `private`.
* **Controlled Access:** Providing public methods (often called **getters** and **setters**) to access and modify the private data in a controlled manner.

### How Encapsulation is Achieved in Java
1.  **Declare instance variables as `private`:** This makes them inaccessible directly from outside the class.
2.  **Provide `public` getter methods:** These methods allow external code to read the value of a private variable.
3.  **Provide `public` setter methods:** These methods allow external code to modify the value of a private variable, often with validation logic.

### Benefits of Encapsulation
1.  **Data Hiding / Security:** Prevents direct, unauthorized access or modification of an object's internal state, protecting data integrity.
2.  **Flexibility and Maintainability:** The internal implementation of a class can be changed without affecting the external code that uses the class, as long as the public getter/setter interface remains the same.
3.  **Control over Data:** Setters can include validation logic to ensure that data is set to valid values. Getters can format or transform data before returning it.
4.  **Modularity:** Encapsulated classes are self-contained and easier to reuse in different parts of an application or in other projects.

```java
// Example: Encapsulation
public class Student {
    // Private attributes (data hiding)
    private String name;
    private int age;

    // Constructor
    public Student(String name, int age) {
        this.name = name;
        // Use setter for initial age validation
        setAge(age);
    }

    // Public getter method for name
    public String getName() {
        return name;
    }

    // Public setter method for name (optional, if name is immutable after creation)
    public void setName(String name) {
        this.name = name;
    }

    // Public getter method for age
    public int getAge() {
        return age;
    }

    // Public setter method for age (with validation)
    public void setAge(int age) {
        if (age > 0 && age < 120) { // Validation logic
            this.age = age;
        } else {
            System.out.println("Invalid age. Age must be between 1 and 119.");
        }
    }

    public static void main(String[] args) {
        Student student1 = new Student("Alice", 20);

        // Accessing data using getter
        System.out.println("Student Name: " + student1.getName()); // Output: Student Name: Alice
        System.out.println("Student Age: " + student1.getAge());   // Output: Student Age: 20

        // Modifying data using setter with validation
        student1.setAge(22); // Valid change
        System.out.println("New Age: " + student1.getAge()); // Output: New Age: 22

        student1.setAge(-5); // Invalid change
        // Output: Invalid age. Age must be between 1 and 119.
        System.out.println("Age after invalid attempt: " + student1.getAge()); // Output: Age after invalid attempt: 22 (age remains unchanged)
    }
}
```
In this example, the `name` and `age` attributes are `private`, preventing direct access. Instead, `public` `getName()`, `setName()`, `getAge()`, and `setAge()` methods are provided. The `setAge()` method includes validation to ensure the age is within a reasonable range, demonstrating controlled access.


---

## Interfaces


An **interface** in Java is a blueprint of a class. It defines a set of methods that a class must implement. Interfaces are used to achieve full abstraction and to support multiple inheritance of type (not implementation).

### Key Characteristics of Interfaces
* **Abstraction:** Before Java 8, interfaces could only contain abstract methods (methods without a body) and `public static final` variables (constants). All methods were implicitly `public abstract`.
* **From Java 8:** Interfaces can have `default` and `static` methods with implementations.
* **From Java 9:** Interfaces can have `private` methods.
* **No Instantiation:** You cannot create an object of an interface directly using `new`.
* **Implementation:** Classes `implement` interfaces using the `implements` keyword. A class can implement multiple interfaces.
* **No Constructors:** Interfaces cannot have constructors.
* **Fields:** All fields declared in an interface are implicitly `public static final`.

### Why Use Interfaces?
1.  **Achieve Full Abstraction:** By defining only abstract methods, interfaces enforce that implementing classes provide their own concrete implementations.
2.  **Support Multiple Inheritance of Type:** A class can implement multiple interfaces, allowing it to inherit behavior contracts from multiple sources. This solves the "diamond problem" associated with multiple inheritance of implementation in languages like C++.
3.  **Define Contracts/APIs:** Interfaces define a contract for what a class *must* do, without dictating *how* it does it. This is crucial for designing flexible and extensible systems.
4.  **Loose Coupling:** Promotes loose coupling between components, as classes interact through interfaces rather than concrete implementations.
5.  **Polymorphism:** Enables runtime polymorphism, allowing a single interface type to refer to objects of different implementing classes.

### Syntax
```java
public interface InterfaceName {
    // Constant (implicitly public static final)
    int MAX_VALUE = 100;

    // Abstract method (implicitly public abstract before Java 8)
    void doSomething();

    // Default method (from Java 8)
    default void log(String message) {
        System.out.println("Log: " + message);
    }

    // Static method (from Java 8)
    static void helperMethod() {
        System.out.println("This is a static helper method in the interface.");
    }

    // Private method (from Java 9)
    private void privateHelper() {
        System.out.println("This is a private helper method.");
    }
}
```

### Implementing an Interface
A class that implements an interface must provide an implementation for all its abstract methods (unless the implementing class is itself abstract).

```java
// Example: Interface
interface Drivable {
    void start(); // Abstract method
    void stop();  // Abstract method
    void accelerate(int speed); // Abstract method

    default void turn(String direction) { // Default method
        System.out.println("Turning " + direction);
    }

    static void displayDrivingTips() { // Static method
        System.out.println("Always drive safely!");
    }
}

class Car implements Drivable { // Implements the Drivable interface
    @Override
    public void start() {
        System.out.println("Car started.");
    }

    @Override
    public void stop() {
        System.out.println("Car stopped.");
    }

    @Override
    public void accelerate(int speed) {
        System.out.println("Car accelerating to " + speed + " mph.");
    }
}

class Bicycle implements Drivable { // Implements the Drivable interface
    @Override
    public void start() {
        System.out.println("Bicycle started pedaling.");
    }

    @Override
    public void stop() {
        System.out.println("Bicycle stopped.");
    }

    @Override
    public void accelerate(int speed) {
        System.out.println("Bicycle pedaling faster to reach " + speed + " mph.");
    }

    // Bicycle can also override the default method
    @Override
    public void turn(String direction) {
        System.out.println("Bicycle leaning to turn " + direction);
    }
}

public class InterfaceExample {
    public static void main(String[] args) {
        Car myCar = new Car();
        myCar.start();
        myCar.accelerate(60);
        myCar.turn("left"); // Calls default method
        myCar.stop();

        System.out.println("
--- Bicycle ---");
        Bicycle myBicycle = new Bicycle();
        myBicycle.start();
        myBicycle.accelerate(15);
        myBicycle.turn("right"); // Calls overridden default method
        myBicycle.stop();

        Drivable.displayDrivingTips(); // Calling static method on interface
    }
}
```


---

## Enums


An **Enum** (short for "enumeration") in Java is a special data type that represents a fixed set of named constants. It's used when you have a collection of predefined values that do not change.

### Why Use Enums?
* **Type Safety:** Prevents invalid values from being assigned. Instead of using arbitrary integers or strings, you use specific enum constants.
* **Readability:** Makes code more readable and self-documenting.
* **Maintainability:** If you need to add or remove constants, you only modify the enum definition.
* **Preventing Errors:** Reduces the chance of errors that can occur with magic numbers or string literals.

### Declaring an Enum
Enums are declared using the `enum` keyword. The constants are typically written in `UPPER_SNAKE_CASE`.

```java
// Example: Declaring an Enum
public enum Day {
    SUNDAY,
    MONDAY,
    TUESDAY,
    WEDNESDAY,
    THURSDAY,
    FRIDAY,
    SATURDAY
}
```

### Using Enums
You access enum constants using the enum type name followed by a dot and the constant name.

```java
public class EnumExample {
    public static void main(String[] args) {
        Day today = Day.WEDNESDAY;

        if (today == Day.WEDNESDAY) {
            System.out.println("It's hump day!");
        }

        switch (today) {
            case SATURDAY:
            case SUNDAY:
                System.out.println("It's the weekend!");
                break;
            default:
                System.out.println("It's a weekday.");
        }
    }
}
```

### Enums with Fields, Constructors, and Methods
Enums can be much more powerful than simple lists of constants. They can have:
* **Fields (attributes):** To store data associated with each constant.
* **Constructors:** To initialize these fields. Enum constructors are implicitly `private`.
* **Methods:** To define behavior for each constant.

```java
// Enum with fields, constructor, and method
public enum CoffeeSize {
    SMALL(8, "S"),
    MEDIUM(12, "M"),
    LARGE(16, "L");

    private final int ounces;
    private final String code;

    // Constructor (implicitly private)
    CoffeeSize(int ounces, String code) {
        this.ounces = ounces;
        this.code = code;
    }

    // Getter methods
    public int getOunces() {
        return ounces;
    }

    public String getCode() {
        return code;
    }

    // Method to display description
    public void displayDescription() {
        System.out.println(name() + " size: " + ounces + " oz (" + code + ")");
    }

    public static void main(String[] args) {
        CoffeeSize myCoffee = CoffeeSize.MEDIUM;
        System.out.println("My coffee is " + myCoffee); // Output: My coffee is MEDIUM
        System.out.println("Ounces: " + myCoffee.getOunces()); // Output: Ounces: 12
        myCoffee.displayDescription(); // Output: MEDIUM size: 12 oz (M)

        // Iterating through enum constants
        for (CoffeeSize size : CoffeeSize.values()) {
            size.displayDescription();
        }
    }
}
```

### Enum Methods
All enums implicitly extend `java.lang.Enum` and inherit several useful methods:
* `name()`: Returns the name of the enum constant as a `String`.
* `ordinal()`: Returns the ordinal (position) of the enum constant (0-indexed).
* `valueOf(String name)`: Returns the enum constant with the specified name.
* `values()`: Returns an array containing all the constants of the enum type.

```java
Day day = Day.MONDAY;
System.out.println(day.name());    // Output: MONDAY
System.out.println(day.ordinal()); // Output: 1 (SUNDAY is 0)

Day parsedDay = Day.valueOf("FRIDAY");
System.out.println(parsedDay);     // Output: FRIDAY
```


---

## Record


**Records** are a new type declaration in Java (introduced in Java 16 as a standard feature) designed to reduce boilerplate code for classes that are primarily used to store data. They provide a concise way to declare immutable data classes.

### Why Use Records?
Traditional data classes often require a lot of boilerplate code:
* Fields (attributes)
* Constructor(s)
* `equals()` method
* `hashCode()` method
* `toString()` method
* Getter methods

Records automatically generate these common methods, significantly simplifying the code for data carriers.

### Key Characteristics of Records
* **Immutability:** All fields in a record are implicitly `final`. Once an object is created, its state cannot be changed.
* **Concise Declaration:** You declare the components (fields) directly in the record header.
* **Automatic Generation:** The compiler automatically generates:
    * A **canonical constructor** (a public constructor with all components as parameters).
    * **Accessor methods** (implicitly named after the component, e.g., `name()` instead of `getName()`).
    * `equals()` and `hashCode()` methods (based on all components).
    * `toString()` method (that prints the record's type and the values of all components).
* **No `extends`:** Records implicitly extend `java.lang.Record` and cannot extend any other class.
* **Can `implement` interfaces:** Records can implement interfaces.
* **Can have static fields and methods:** Records can have static members.
* **Can have instance methods:** Records can have additional custom instance methods.

### Syntax
```java
public record RecordName(Type component1, Type component2, ...) {
    // Optional: Compact constructor for validation/normalization
    // Optional: Custom instance methods
    // Optional: Static fields and methods
}
```

### Example
```java
// Traditional Java class for a Point
class TraditionalPoint {
    private final int x;
    private final int y;

    public TraditionalPoint(int x, int y) {
        this.x = x;
        this.y = y;
    }

    public int getX() { return x; }
    public int getY() { return y; }

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        TraditionalPoint that = (TraditionalPoint) o;
        return x == that.x && y == that.y;
    }

    @Override
    public int hashCode() {
        return Objects.hash(x, y);
    }

    @Override
    public String toString() {
        return "TraditionalPoint{" +
               "x=" + x +
               ", y=" + y +
               '}';
    }
}

// Equivalent Java Record
public record Point(int x, int y) {
    // Optional: You can add custom instance methods
    public double distanceFromOrigin() {
        return Math.sqrt(x * x + y * y);
    }

    // Optional: You can add a compact constructor for validation/normalization
    public Point {
        if (x < 0 || y < 0) {
            // This is a "compact constructor" - no parameters, refers to the components
            // Parameters are implicitly available and assigned after this block.
            // You can add validation here.
            System.out.println("Warning: Point coordinates should ideally be non-negative.");
        }
    }
}

public class RecordExample {
    public static void main(String[] args) {
        // Creating instances of the Record
        Point p1 = new Point(10, 20);
        Point p2 = new Point(10, 20);
        Point p3 = new Point(30, 40);

        // Accessing components (implicitly generated accessors)
        System.out.println("P1 x: " + p1.x() + ", P1 y: " + p1.y()); // Output: P1 x: 10, P1 y: 20

        // Automatically generated toString()
        System.out.println("P1: " + p1); // Output: Point[x=10, y=20]

        // Automatically generated equals()
        System.out.println("P1 equals P2: " + p1.equals(p2)); // Output: P1 equals P2: true
        System.out.println("P1 equals P3: " + p1.equals(p3)); // Output: P1 equals P3: false

        // Using custom instance method
        System.out.println("Distance from origin for P1: " + p1.distanceFromOrigin()); // Output: Distance from origin for P1: 22.36...

        // Using compact constructor with validation
        Point pNeg = new Point(-1, 5); // Output: Warning: Point coordinates should ideally be non-negative.
    }
}
```
Records are ideal for DTOs (Data Transfer Objects) and other simple data-holding classes, making code cleaner and less error-prone.


---

## Method Overloading / Overriding


**Method Overloading** and **Method Overriding** are two distinct concepts in Java that enable polymorphism. While both involve methods with the same name, they differ in their purpose, how they are resolved, and the rules that govern them.

### 1. Method Overloading (Compile-time Polymorphism)
* **Definition:** Occurs when a class has multiple methods with the same name but different **method signatures** (different number of parameters, different types of parameters, or different order of parameters). The return type can be the same or different.
* **Resolution:** The correct overloaded method to call is determined at **compile time** based on the arguments passed to the method. This is why it's also known as Compile-time Polymorphism or Static Polymorphism.
* **Scope:** Happens within the same class.

### Rules for Method Overloading:
1.  Methods must have the same name.
2.  Methods must have different parameter lists (number, type, or order of parameters).
3.  Return type *can* be different, but it's not sufficient to overload a method. Only changing the return type (without changing parameters) will result in a compile-time error.
4.  Access modifiers *can* be different.

```java
// Example: Method Overloading
public class Calculator {
    // Method 1: Adds two integers
    public int add(int a, int b) {
        System.out.println("Adding two integers:");
        return a + b;
    }

    // Method 2: Adds three integers (different number of parameters)
    public int add(int a, int b, int c) {
        System.out.println("Adding three integers:");
        return a + b + c;
    }

    // Method 3: Adds two doubles (different types of parameters)
    public double add(double a, double b) {
        System.out.println("Adding two doubles:");
        return a + b;
    }

    // Method 4: Adds two strings (different types of parameters)
    public String add(String s1, String s2) {
        System.out.println("Concatenating two strings:");
        return s1 + s2;
    }

    public static void main(String[] args) {
        Calculator calc = new Calculator();
        System.out.println(calc.add(10, 20));        // Calls Method 1
        System.out.println(calc.add(10, 20, 30));    // Calls Method 2
        System.out.println(calc.add(10.5, 20.5));    // Calls Method 3
        System.out.println(calc.add("Hello", "World")); // Calls Method 4
    }
}
```

### 2. Method Overriding (Runtime Polymorphism)
* **Definition:** Occurs when a subclass provides a specific implementation for a method that is already defined in its superclass. The method signature (name, number, and type of parameters) must be exactly the same as in the superclass.
* **Resolution:** The correct overridden method to call is determined at **runtime** by the JVM based on the actual object type. This is why it's also known as Runtime Polymorphism or Dynamic Polymorphism.
* **Scope:** Happens across classes in an inheritance hierarchy.
* **`@Override` Annotation:** It's good practice to use the `@Override` annotation to indicate that a method is intended to override a superclass method. This helps the compiler detect errors if the method signature doesn't match.

### Rules for Method Overriding:
1.  Methods must have the same name.
2.  Methods must have the same parameter list.
3.  Return type must be the same or a covariant return type (a subclass of the superclass's return type).
4.  Access modifier of the overriding method cannot be more restrictive than the overridden method (e.g., a `public` method in superclass cannot be `private` in subclass).
5.  `final` methods cannot be overridden.
6.  `static` methods cannot be overridden (they are hidden, not overridden).
7.  Constructors cannot be overridden.

```java
// Example: Method Overriding
class Animal {
    public void makeSound() { // Superclass method
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {
    @Override // Indicates this method overrides a superclass method
    public void makeSound() { // Overriding the makeSound method
        System.out.println("Dog barks: Woof! Woof!");
    }

    public void fetch() {
        System.out.println("Dog fetches the ball.");
    }
}

class Cat extends Animal {
    @Override
    public void makeSound() { // Overriding the makeSound method
        System.out.println("Cat meows: Meow!");
    }
}

public class OverridingExample {
    public static void main(String[] args) {
        Animal myAnimal = new Animal();
        myAnimal.makeSound(); // Output: Animal makes a sound

        Dog myDog = new Dog();
        myDog.makeSound(); // Output: Dog barks: Woof! Woof! (Overridden method)

        Cat myCat = new Cat();
        myCat.makeSound(); // Output: Cat meows: Meow! (Overridden method)

        // Runtime Polymorphism: A superclass reference variable can hold a subclass object
        Animal polyAnimal1 = new Dog();
        polyAnimal1.makeSound(); // Output: Dog barks: Woof! Woof! (Dog's method is called at runtime)

        Animal polyAnimal2 = new Cat();
        polyAnimal2.makeSound(); // Output: Cat meows: Meow! (Cat's method is called at runtime)

        // polyAnimal1.fetch(); // Compile-time error: 'fetch' is not defined in Animal
    }
}
```

### Key Differences Summary:

| Feature           | Method Overloading                               | Method Overriding                                  |
| :---------------- | :----------------------------------------------- | :------------------------------------------------- |
| **Concept** | Multiple methods with same name, different signatures | Subclass provides specific implementation for superclass method |
| **Scope** | Within the same class                            | Across classes (inheritance hierarchy)             |
| **Signature** | Must be different                                | Must be same                                       |
| **Return Type** | Can be same or different                         | Must be same or covariant                          |
| **Access Modifier**| Can be different                                 | Cannot be more restrictive                         |
| **`final` methods**| Can be overloaded                                | Cannot be overridden                               |
| **`static` methods**| Can be overloaded (but not overridden)           | Cannot be overridden (hidden instead)              |
| **Polymorphism** | Compile-time (Static) Polymorphism               | Runtime (Dynamic) Polymorphism                     |


---

## Initializer Block


In Java, an **initializer block** is a block of code that is executed when an object is created or when a class is loaded. There are two types of initializer blocks:

### 1. Instance Initializer Block (Non-Static Initializer Block)
* **Definition:** A block of code inside a class, without any `static` keyword, method name, or constructor.
* **Execution:** Executed every time an object of the class is created, *before* the constructor.
* **Order of Execution (when creating an object):**
    1.  Static blocks (if any) are executed when the class is loaded.
    2.  Instance variables are initialized (either explicitly or to default values).
    3.  Instance initializer blocks are executed in the order they appear in the class.
    4.  The constructor is executed.
* **Purpose:**
    * To perform initialization that is common to all constructors of the class.
    * To initialize instance variables that require more complex logic than a simple assignment.

```java
public class InstanceInitializerExample {
    private int value;

    // Instance initializer block
    {
        System.out.println("Instance Initializer Block 1 executed.");
        this.value = 10; // Initialize instance variable
    }

    // Another instance initializer block
    {
        System.out.println("Instance Initializer Block 2 executed.");
        this.value += 5;
    }

    public InstanceInitializerExample() {
        System.out.println("Constructor executed. Value: " + value);
    }

    public InstanceInitializerExample(int initialValue) {
        // Instance initializer blocks run before this constructor body
        System.out.println("Parameterized Constructor executed. Initial Value: " + initialValue + ", Current Value: " + value);
        this.value = initialValue; // Overwrites value set by initializer blocks
        System.out.println("Value after constructor assignment: " + value);
    }

    public static void main(String[] args) {
        System.out.println("Creating obj1:");
        InstanceInitializerExample obj1 = new InstanceInitializerExample();
        // Output:
        // Instance Initializer Block 1 executed.
        // Instance Initializer Block 2 executed.
        // Constructor executed. Value: 15

        System.out.println("
Creating obj2:");
        InstanceInitializerExample obj2 = new InstanceInitializerExample(100);
        // Output:
        // Instance Initializer Block 1 executed.
        // Instance Initializer Block 2 executed.
        // Parameterized Constructor executed. Initial Value: 100, Current Value: 15
        // Value after constructor assignment: 100
    }
}
```

### 2. Static Initializer Block (Static Block)
* **Definition:** A block of code inside a class, preceded by the `static` keyword.
* **Execution:** Executed only once, when the class is loaded into the JVM. This happens even before the `main` method is executed or any objects of the class are created.
* **Purpose:**
    * To initialize static variables that require complex logic (e.g., reading from a file, database connection).
    * To perform one-time setup tasks for the class.

```java
public class StaticInitializerExample {
    static int staticValue;

    // Static initializer block
    static {
        System.out.println("Static Initializer Block executed.");
        staticValue = 20; // Initialize static variable
        System.out.println("Static value initialized to: " + staticValue);
    }

    public StaticInitializerExample() {
        System.out.println("Constructor executed.");
    }

    public static void main(String[] args) {
        System.out.println("Main method started.");
        StaticInitializerExample obj1 = new StaticInitializerExample();
        StaticInitializerExample obj2 = new StaticInitializerExample(); // Static block does not run again
        System.out.println("Static value in main: " + staticValue);
        System.out.println("Main method finished.");
    }
}
/*
Output:
Static Initializer Block executed.
Static value initialized to: 20
Main method started.
Constructor executed.
Constructor executed.
Static value in main: 20
Main method finished.
*/
```
**Key Differences:**

| Feature            | Instance Initializer Block         | Static Initializer Block            |
| :----------------- | :--------------------------------- | :---------------------------------- |
| **Keyword** | None                               | `static`                            |
| **Execution** | Every time an object is created    | Once, when the class is loaded      |
| **Access** | Can access instance and static members | Can access only static members      |
| **`this`/`super`** | Can use `this` and `super`         | Cannot use `this` or `super`        |
| **Purpose** | Common initialization for objects  | One-time class setup/static init    |


---

## Static vs Dynamic Binding


In Java, **binding** refers to the process of linking a method call to its actual implementation. This linking can occur at two different stages: compile time or runtime.

### 1. Static Binding (Early Binding / Compile-time Binding)
* **Definition:** The method call is resolved at **compile time**. The compiler determines which method to call based on the type of the reference variable (the declared type).
* **Mechanism:** Achieved through method overloading, `final` methods, `static` methods, and `private` methods.
* **Characteristics:**
    * **Faster Execution:** Since the method call is resolved early, there's no overhead at runtime.
    * **Less Flexible:** The decision is fixed at compile time.
* **Examples:**
    * **Method Overloading:** The compiler knows which overloaded method to call based on the number/types of arguments.
    * **`private` methods:** Can only be accessed within the same class, so the compiler knows the exact method.
    * **`final` methods:** Cannot be overridden, so the compiler knows the exact method.
    * **`static` methods:** Belong to the class, not an object, so the call is resolved based on the class name at compile time.

```java
public class StaticBindingExample {
    public void display(int num) { // Overloaded method
        System.out.println("Displaying int: " + num);
    }

    public void display(String text) { // Overloaded method
        System.out.println("Displaying String: " + text);
    }

    private void privateMethod() { // Private method
        System.out.println("This is a private method.");
    }

    static void staticMethod() { // Static method
        System.out.println("This is a static method.");
    }

    final void finalMethod() { // Final method
        System.out.println("This is a final method.");
    }

    public static void main(String[] args) {
        StaticBindingExample obj = new StaticBindingExample();

        // Method overloading - resolved at compile time
        obj.display(10);      // Calls display(int)
        obj.display("Hello"); // Calls display(String)

        // Private, static, final methods - resolved at compile time
        obj.privateMethod(); // Compiler knows it's this class's privateMethod
        StaticBindingExample.staticMethod(); // Compiler knows it's this class's staticMethod
        obj.finalMethod(); // Compiler knows it's this class's finalMethod
    }
}
```

### 2. Dynamic Binding (Late Binding / Runtime Binding)
* **Definition:** The method call is resolved at **runtime**. The JVM determines which method to call based on the actual object type (the object pointed to by the reference variable), not just the declared type of the reference variable.
* **Mechanism:** Achieved through **Method Overriding**. This is a core concept of runtime polymorphism.
* **Characteristics:**
    * **More Flexible:** Allows for different implementations to be called based on the actual object at runtime.
    * **Slightly Slower:** Involves a small overhead at runtime to determine the correct method.
* **Example:** When a superclass reference variable holds a subclass object, the overridden method of the subclass is executed.

```java
class Animal {
    public void eat() { // Overridden method
        System.out.println("Animal eats food.");
    }
}

class Dog extends Animal {
    @Override
    public void eat() { // Overriding method
        System.out.println("Dog eats kibble.");
    }

    public void bark() {
        System.out.println("Woof!");
    }
}

class Cat extends Animal {
    @Override
    public void eat() { // Overriding method
        System.out.println("Cat eats fish.");
    }
}

public class DynamicBindingExample {
    public static void main(String[] args) {
        Animal animal1 = new Animal(); // Reference type is Animal, Object type is Animal
        animal1.eat(); // Output: Animal eats food. (Static binding, but also dynamic if it were overridden)

        Animal animal2 = new Dog(); // Reference type is Animal, Object type is Dog
        animal2.eat(); // Output: Dog eats kibble. (Dynamic binding - Dog's eat() is called)

        Animal animal3 = new Cat(); // Reference type is Animal, Object type is Cat
        animal3.eat(); // Output: Cat eats fish. (Dynamic binding - Cat's eat() is called)

        // Dog dog = new Animal(); // Compile-time error: Cannot convert Animal to Dog
        // Dog dog = (Dog) animal2; // Downcasting
        // dog.bark(); // Now bark() can be called
    }
}
```
In the `DynamicBindingExample`, even though `animal2` and `animal3` are declared as `Animal` type, the `eat()` method called is determined by the actual object type (`Dog` or `Cat`) at runtime. This is the essence of dynamic binding and runtime polymorphism.

**Summary:**
* **Static Binding:** Compiler decides which method to call. Based on reference type. Used for overloaded, private, static, and final methods.
* **Dynamic Binding:** JVM decides which method to call at runtime. Based on actual object type. Used for overridden methods (runtime polymorphism).


---

## Pass by Value / Pass by Reference


In Java, arguments are always passed by **value**. This is a crucial concept to understand, as it affects how variables behave when passed to methods.

### 1. Pass by Value (for Primitive Data Types)
* **Mechanism:** When a primitive data type (like `int`, `char`, `boolean`, `float`, `double`, `byte`, `short`, `long`) is passed to a method, a **copy of its value** is made and passed to the method's parameter.
* **Effect:** Any changes made to the parameter inside the method will *not* affect the original variable outside the method.

```java
public class PassByValuePrimitive {
    public static void increment(int num) {
        System.out.println("Inside method (before increment): " + num); // Shows the copied value
        num = num + 1; // Modifies the copy
        System.out.println("Inside method (after increment): " + num);
    }

    public static void main(String[] args) {
        int originalNum = 10;
        System.out.println("Before method call: " + originalNum); // Output: 10
        increment(originalNum); // Pass a copy of 10
        System.out.println("After method call: " + originalNum);  // Output: 10 (original remains unchanged)
    }
}
```
In this example, `increment(originalNum)` receives a copy of `10`. When `num` is incremented to `11` inside the method, it only affects the copy, not `originalNum`.

### 2. Pass by Value (for Reference Data Types)
* **Mechanism:** When an object (a reference data type like `String`, `Array`, `Class` objects, `Interface` objects) is passed to a method, a **copy of the reference (memory address)** to that object is made and passed to the method's parameter. The object itself is *not* copied.
* **Effect:**
    * If you modify the *state* of the object using the copied reference inside the method, these changes *will* be reflected in the original object outside the method, because both the original and copied references point to the *same* object in memory.
    * If you reassign the *parameter* to point to a *new* object inside the method, this change will *not* affect the original reference outside the method. The original reference will still point to the original object.

```java
class MyObject {
    int value;
    MyObject(int value) { this.value = value; }
    @Override
    public String toString() { return "MyObject [value=" + value + "]"; }
}

public class PassByValueReference {
    public static void modifyObject(MyObject obj) {
        System.out.println("Inside method (before modify): " + obj); // Shows reference to original object
        obj.value = 200; // Modifies the state of the original object
        System.out.println("Inside method (after modify): " + obj);
    }

    public static void reassignObject(MyObject obj) {
        System.out.println("Inside reassign method (before reassign): " + obj);
        obj = new MyObject(999); // Reassigns the LOCAL parameter 'obj' to a NEW object
        System.out.println("Inside reassign method (after reassign): " + obj);
    }

    public static void main(String[] args) {
        MyObject originalObj = new MyObject(100);
        System.out.println("Before modify method call: " + originalObj); // Output: MyObject [value=100]
        modifyObject(originalObj); // Pass a copy of the reference
        System.out.println("After modify method call: " + originalObj);  // Output: MyObject [value=200] (Original object's state changed)

        System.out.println("
--- Reassign Example ---");
        MyObject anotherObj = new MyObject(500);
        System.out.println("Before reassign method call: " + anotherObj); // Output: MyObject [value=500]
        reassignObject(anotherObj); // Pass a copy of the reference
        System.out.println("After reassign method call: " + anotherObj);  // Output: MyObject [value=500] (Original reference still points to original object)
    }
}
```
In `modifyObject`, `obj.value = 200;` changes the `value` field of the object that *both* `originalObj` and the method's `obj` parameter refer to.
In `reassignObject`, `obj = new MyObject(999);` makes the *local* parameter `obj` point to a *new* object. The `anotherObj` outside the method still points to the *original* object.

### Conclusion on Java's Parameter Passing
Java is strictly **pass-by-value**.
* For primitives, it passes a copy of the value.
* For objects, it passes a copy of the reference (the memory address).
This means you can change the contents of an object passed to a method, but you cannot make the original reference outside the method point to a different object.


---

