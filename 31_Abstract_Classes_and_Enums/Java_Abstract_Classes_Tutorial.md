
# Java Tutorial: Abstract Classes

## 1. Definitions and Key Concepts

**Abstract Class**: A class that cannot be instantiated and is used as a blueprint for other classes. It may contain abstract methods (methods without a body) and non-abstract methods (methods with a body).

**Abstract Method**: A method that is declared without an implementation. Subclasses that inherit an abstract class must implement all its abstract methods unless the subclass is also abstract.

**Concrete Class**: A class that can be instantiated and must provide implementations for all inherited abstract methods.

**Inheritance**: The process by which one class acquires the properties (methods and fields) of another class.

**Polymorphism**: The ability of a single function, class, or method to work in different ways based on the context.

## 2. Vocabulary Words
- **Abstract**: A keyword used to declare an abstract class or method.
- **Extends**: A keyword indicating that a class is inheriting properties and methods from another class.
- **Override**: A feature that allows a subclass to provide a specific implementation for an inherited method.
- **Concrete Method**: A regular method that has an implementation in an abstract class or subclass.

## 3. Examples

**Basic Abstract Class and Method Example**:
```java
abstract class Animal {
    // Abstract method (no body)
    public abstract void makeSound();
    
    // Concrete method (has a body)
    public void eat() {
        System.out.println("This animal is eating.");
    }
}

class Dog extends Animal {
    // Providing implementation for the abstract method
    @Override
    public void makeSound() {
        System.out.println("The dog barks");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog myDog = new Dog();
        myDog.makeSound(); // Output: The dog barks
        myDog.eat();       // Output: This animal is eating.
    }
}
```

**Explanation**: In the example above, `Animal` is an abstract class with an abstract method `makeSound()` and a concrete method `eat()`. The `Dog` class extends `Animal` and provides an implementation for `makeSound()`.

## 4. Assignment: Animal Simulation

**Task**: Create an abstract class called `Vehicle` with the following:
- An abstract method `move()` that will be implemented differently by subclasses.
- A concrete method `startEngine()` that prints "The engine starts."

Create three subclasses:
- `Car` that prints "The car drives on the road."
- `Boat` that prints "The boat sails on water."
- `Plane` that prints "The plane flies in the sky."

In your `Main` class, create an array of `Vehicle` objects containing one instance of each subclass and call `move()` and `startEngine()` for each object.

**Code Template**:
```java
abstract class Vehicle {
    public abstract void move();
    
    public void startEngine() {
        System.out.println("The engine starts.");
    }
}

class Car extends Vehicle {
    @Override
    public void move() {
        System.out.println("The car drives on the road.");
    }
}

class Boat extends Vehicle {
    @Override
    public void move() {
        System.out.println("The boat sails on water.");
    }
}

class Plane extends Vehicle {
    @Override
    public void move() {
        System.out.println("The plane flies in the sky.");
    }
}

public class Main {
    public static void main(String[] args) {
        Vehicle[] vehicles = {new Car(), new Boat(), new Plane()};
        
        for (Vehicle v : vehicles) {
            v.startEngine();
            v.move();
        }
    }
}
```

**Expected Output**:
```
The engine starts.
The car drives on the road.
The engine starts.
The boat sails on water.
The engine starts.
The plane flies in the sky.
```

## 5. Assignment Solution Explanation
In the assignment:
- The `Vehicle` class is an abstract class with an abstract method `move()` and a concrete method `startEngine()`.
- The `Car`, `Boat`, and `Plane` classes extend `Vehicle` and provide their own implementations for `move()`.
- In the `Main` class, an array of `Vehicle` objects is created, and both methods are called for each object, showcasing polymorphism.

This example helps understand how abstract classes can provide a foundation for multiple subclasses with shared and unique behaviors.

## 6. When to Use Abstract Classes

Abstract classes are ideal when:

- **You Need a Common Base Class**: Use abstract classes when you want to create a blueprint for other classes that share common properties and methods but may have different implementations for some of those methods. This allows you to define a template with shared behavior while enforcing implementation of certain behaviors in subclasses.

- **Partial Implementation**: If you want to provide a base implementation for some methods while leaving other methods abstract for subclasses to define, abstract classes are perfect. This enables code reuse while ensuring subclasses implement specific behavior.

- **Shared State or Behavior**: Abstract classes can have fields (variables) that are shared across all subclasses, making it a suitable choice when common state or behavior should be inherited.

- **When Using Inheritance Over Interfaces**: Abstract classes are preferred when there is a clear "is-a" relationship, and you need to share code between classes. For example, `Animal` as an abstract class makes sense if `Dog`, `Cat`, and `Bird` will inherit common methods like `eat()` or `sleep()`.

- **Extending Functionality**: Abstract classes allow you to extend the functionality of the base class. They can have constructors, fields, and concrete methods, which interfaces do not support (prior to Java 8).

**When Not to Use Abstract Classes**:
- If you only need to enforce a contract without any shared code or state, interfaces are more appropriate.
- When a class needs to inherit from multiple sources, using interfaces is better since Java supports single inheritance for classes but allows multiple interfaces.

Abstract classes strike a balance between concrete classes and interfaces, providing both structure and partial functionality.
