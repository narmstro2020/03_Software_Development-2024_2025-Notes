
# Inheritance in Java

**Inheritance** is a fundamental concept in Object-Oriented Programming (OOP) that enables one class to acquire properties and methods from another. It helps to reduce code redundancy and promotes reusability.

## 1. Basics of Inheritance

In Java, inheritance allows a new class, called the **subclass** (or derived/child class), to inherit fields and methods from an existing class, known as the **superclass** (or base/parent class).

### Syntax:
```java
class SuperClass {
    // Fields and methods
}

class SubClass extends SuperClass {
    // Additional fields and methods
}
```

The `extends` keyword is used to indicate that a class is inheriting from another class.

### Example:
```java
class Animal {
    void eat() {
        System.out.println("This animal eats food.");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("The dog barks.");
    }
}
```

In this example, the `Dog` class inherits the `eat()` method from the `Animal` class and adds its own `bark()` method.

## 2. Types of Inheritance in Java

Java supports **single inheritance** and **multilevel inheritance** but **does not support multiple inheritance** (a class cannot inherit from more than one class directly).

1. **Single Inheritance**: A class inherits from one superclass.
   ```java
   class Cat extends Animal {
       void meow() {
           System.out.println("The cat meows.");
       }
   }
   ```

2. **Multilevel Inheritance**: A class inherits from a superclass, and another class inherits from that subclass.
   ```java
   class Mammal extends Animal {
       void giveBirth() {
           System.out.println("Mammals give birth to young ones.");
       }
   }

   class Whale extends Mammal {
       void swim() {
           System.out.println("The whale swims.");
       }
   }
   ```

## 3. The `super` Keyword

The `super` keyword is used to refer to the superclass. It can be used to:
- Call the superclass's constructor
- Access a superclass’s method or field that is overridden in the subclass

### Example:
```java
class Animal {
    Animal() {
        System.out.println("Animal constructor called");
    }
    
    void sound() {
        System.out.println("Some sound...");
    }
}

class Dog extends Animal {
    Dog() {
        super();  // Calls Animal's constructor
        System.out.println("Dog constructor called");
    }
    
    @Override
    void sound() {
        super.sound();  // Calls the superclass sound method
        System.out.println("Woof woof");
    }
}
```

## 4. Method Overriding

When a subclass has a specific implementation of a method already defined in its superclass, it is called **method overriding**. The `@Override` annotation is used for better readability and to ensure the method is correctly overridden.

### Example:
```java
class Vehicle {
    void start() {
        System.out.println("Vehicle is starting");
    }
}

class Car extends Vehicle {
    @Override
    void start() {
        System.out.println("Car is starting with ignition");
    }
}
```

In this example, the `start()` method in the `Car` class overrides the `start()` method in the `Vehicle` class.

## 5. Access Modifiers and Inheritance

Java provides different access levels to control member accessibility, especially within inheritance. The key access modifiers are `public`, `protected`, package-private (no modifier), and `private`.

### Differences between `protected` and Package-Private

- **`protected`**: Accessible within the same package and in subclasses, even if the subclass is in a different package.
- **Package-Private**: Accessible only within the same package and not available to subclasses outside the package.

Here’s an example to illustrate the difference:

```java
package com.example.animals;

public class Animal {
    protected String name = "Generic Animal";
    String species = "Unknown"; // package-private

    protected void makeSound() {
        System.out.println(name + " makes a sound");
    }

    void habitat() {  // package-private
        System.out.println("This animal lives somewhere.");
    }
}

package com.example.animals;

public class Dog extends Animal {
    void bark() {
        makeSound();         // Accessible due to protected
        System.out.println(name + " barks");
        System.out.println(species);  // Accessible within the same package
    }
}

package com.example.zoo;

import com.example.animals.Animal;

public class ZooKeeper extends Animal {
    void manage() {
        System.out.println(name);    // Accessible due to protected
        makeSound();                 // Accessible due to protected
        // habitat();  // Not accessible, package-private in a different package
    }
}
```

In this example:
- The `name` and `makeSound()` members are `protected`, so they’re accessible within `Dog` and `ZooKeeper` even if `ZooKeeper` is in a different package.
- The `species` and `habitat()` members are package-private (no modifier), so they’re only accessible within the same package (`com.example.animals`) and not accessible in `ZooKeeper`.

## 6. Real-World Example

Let's create an example using `Person`, `Employee`, and `Manager` classes:

```java
class Person {
    String name;
    int age;
    
    Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
    
    void displayInfo() {
        System.out.println("Name: " + name + ", Age: " + age);
    }
}

class Employee extends Person {
    String employeeId;
    
    Employee(String name, int age, String employeeId) {
        super(name, age);
        this.employeeId = employeeId;
    }
    
    void work() {
        System.out.println(name + " is working.");
    }
}

class Manager extends Employee {
    String department;
    
    Manager(String name, int age, String employeeId, String department) {
        super(name, age, employeeId);
        this.department = department;
    }
    
    void manage() {
        System.out.println(name + " manages the " + department + " department.");
    }
}
```

In this example:
- `Employee` inherits from `Person`.
- `Manager` inherits from `Employee`.

## 7. Benefits of Inheritance

1. **Code Reusability**: Common functionalities are written in the superclass and inherited by subclasses.
2. **Code Maintenance**: Changes in the superclass reflect in subclasses, making updates easier.
3. **Polymorphism**: Inheritance facilitates polymorphism, allowing a superclass reference to hold subclass objects.

## 8. Limitations of Inheritance

- **Tight Coupling**: Subclasses are tightly coupled with the superclass, making changes more complex.
- **Multiple Inheritance**: Java doesn’t support multiple inheritance directly; however, it can be achieved with interfaces.

## Conclusion

Inheritance in Java is essential for structuring and organizing code efficiently in an object-oriented approach. Through single and multilevel inheritance, Java enables a flexible way to share attributes and methods across classes, ensuring reusability, maintainability, and extensibility.
