
# Java Tutorial: Basics of Classes and Objects

## 1. **Introduction to Classes and Objects**

In Java, **classes** and **objects** are fundamental concepts of Object-Oriented Programming (OOP). A class is like a blueprint, and an object is an instance of that blueprint.

- **Class**: A blueprint that defines fields (data) and methods (functions) that an object can have.
- **Object**: An instance of a class. It is created from the class and represents a real-world entity.

---

## 2. **Fields (Instance and Static Variables)**

Fields (also known as variables) are used to store data. There are two main types of fields:

### 2.1 **Instance Variables**
- Belong to objects (instances) of a class.
- Each object has its own copy of the instance variables.
- They are declared outside methods but inside the class.

```java
public class Car {
    String brand;  // Instance variable
    String model;  // Instance variable
    int year;      // Instance variable
}
```

### 2.2 **Static Variables**
- Belong to the class itself, not to objects of the class.
- All instances of the class share the same static variable.
- Declared using the `static` keyword.

```java
public class Car {
    static int numberOfWheels = 4; // Static variable
}
```

---

## 3. **Access Modifiers**

In Java, **access modifiers** control the visibility and accessibility of classes, fields, methods, and constructors. There are four access levels: **public**, **private**, **protected**, and the default (no modifier).

### 3.1 **Public**
- The member is accessible from any other class.
- No restrictions on access.

```java
public class Car {
    public String brand; // Public field
}
```

### 3.2 **Private**
- The member is only accessible within the class in which it is declared.
- It is not visible to any other class, including subclasses.

```java
public class Car {
    private String model; // Private field

    public String getModel() {
        return model; // You can access the private field within the class using methods.
    }
}
```

### 3.3 **Protected**
- The member is accessible within the same package and by subclasses, even if they are in different packages.
- Commonly used in inheritance.

```java
public class Car {
    protected int year; // Protected field
}
```

### 3.4 **Default (Package-Private)**
- If no access modifier is specified, the member is accessible only within the same package (package-private).
- It is not accessible from classes in different packages.

```java
public class Car {
    String color; // Default (Package-private) field
}
```

### Summary of Access Modifiers:

| Modifier     | Class | Package | Subclass | World  |
|--------------|-------|---------|----------|--------|
| **public**   | Yes   | Yes     | Yes      | Yes    |
| **protected**| Yes   | Yes     | Yes      | No     |
| **default**  | Yes   | Yes     | No       | No     |
| **private**  | Yes   | No      | No       | No     |

---

## 4. **Methods**

Methods define behaviors for objects. Like fields, methods can be either **instance** methods or **static** methods.

### 4.1 **Instance Methods**
- Operate on instance variables.
- Require an object to be invoked.

```java
public class Car {
    String brand;
    
    // Instance method
    void displayBrand() {
        System.out.println("The car brand is " + brand);
    }
}
```

### 4.2 **Static Methods**
- Belong to the class, not objects.
- Cannot access instance variables directly (unless an object is provided).
- Invoked without creating an object of the class.

```java
public class Car {
    static void displayWheels() {
        System.out.println("All cars have " + numberOfWheels + " wheels.");
    }
}
```

---

## 5. **Constructors**

A **constructor** is a special method used to create and initialize objects. It has the same name as the class and no return type.

- **Default Constructor**: If you do not define any constructor, Java provides a default one.
- **Parameterized Constructor**: You can define constructors with parameters to initialize objects with specific values.

```java
public class Car {
    String brand;
    String model;
    int year;
    
    // Constructor with parameters
    public Car(String brand, String model, int year) {
        this.brand = brand;
        this.model = model;
        this.year = year;
    }
}
```

To create an object:
```java
Car myCar = new Car("Toyota", "Corolla", 2021);
```

---

## 6. **Initializer Blocks**

Java provides **initializer blocks** to execute code before a constructor. These can be used to set up instance variables when the object is created.

### 6.1 **Instance Initializer Block**
- Runs every time an instance of the class is created, before the constructor.

```java
public class Car {
    String brand;
    
    // Instance initializer block
    {
        System.out.println("An instance is being created.");
    }
    
    public Car(String brand) {
        this.brand = brand;
    }
}
```

### 6.2 **Static Initializer Block**
- Runs once when the class is first loaded.

```java
public class Car {
    static {
        System.out.println("Class Car is loaded.");
    }
    
    public Car() {
        System.out.println("Car instance created.");
    }
}
```

---

## 7. **Static vs Instance (Key Differences)**

| Feature              | Static                                  | Instance                                |
|----------------------|-----------------------------------------|-----------------------------------------|
| **Belongs to**        | Class                                   | Object                                  |
| **Accessed by**       | Class name                              | Object reference                        |
| **Memory allocation** | Allocated once (at class loading time)  | Allocated per object (at object creation)|
| **Modification**      | Shared by all instances                 | Unique to each instance                 |
| **Example**           | `Car.numberOfWheels`                    | `myCar.brand`                           |

---

## 8. **Execution Order in a Class**

When an object is created, the sequence in which different parts of the class are executed is important. The full execution order includes field creation, static and instance initializer blocks, and the constructor.

Here’s the execution order:

1. **Static Field Creation**: Static fields are created and initialized when the class is first loaded.
2. **Static Initializer Block**: Runs only once when the class is loaded.
3. **Instance Field Creation**: Instance fields are created and initialized when an object is created.
4. **Instance Initializer Block**: Runs every time an object is created, before the constructor.
5. **Constructor**: Runs after the instance initializer block, finalizing the object creation.

### Example

```java
public class Car {
    // Static field
    static int count;
    
    // Instance fields
    String brand;
    String model;

    // Static initializer block
    static {
        System.out.println("Static block executed.");
        count = 0;
    }
    
    // Instance initializer block
    {
        System.out.println("Instance initializer block executed.");
        brand = "Default Brand"; // Initializing instance field
    }
    
    // Constructor
    public Car(String brand, String model) {
        this.brand = brand;
        this.model = model;
        System.out.println("Constructor executed.");
    }
    
    public static void main(String[] args) {
        Car car1 = new Car("Toyota", "Corolla");  // First object creation
        Car car2 = new Car("Honda", "Civic");     // Second object creation
    }
}
```

### Output:
```
Static block executed.
Instance initializer block executed.
Constructor executed.
Instance initializer block executed.
Constructor executed.
```

---

This updated tutorial now includes information on **Access Modifiers** alongside the previously covered topics. It helps you understand how to control the visibility of fields, methods, and constructors in Java classes.
