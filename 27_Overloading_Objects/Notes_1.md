
# Java Tutorial: Overloaded Constructors and Overloaded Methods

In Java, **overloading** allows a class to have more than one method or constructor with the same name but different parameter lists. This is a form of **polymorphism** known as **compile-time polymorphism** or **static polymorphism**.

## 1. Overloaded Constructors
A **constructor** in Java is a special method used to initialize objects. By **overloading constructors**, you can create multiple ways to instantiate objects of a class with different sets of initial values or behaviors.

### Key Features of Overloaded Constructors:
- Same constructor name (class name) but with different parameters.
- Each overloaded constructor must have a unique parameter list (different types, number, or order of parameters).
- Provides flexibility in how objects of the class can be created.

### Example: Overloaded Constructors
```java
public class Person {
    private String name;
    private int age;
    
    // Default constructor
    public Person() {
        this.name = "Unknown";
        this.age = 0;
    }

    // Constructor with one parameter (name)
    public Person(String name) {
        this.name = name;
        this.age = 0;
    }

    // Constructor with two parameters (name and age)
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    // Display method
    public void displayPersonInfo() {
        System.out.println("Name: " + name + ", Age: " + age);
    }
    
    public static void main(String[] args) {
        // Using default constructor
        Person p1 = new Person();
        p1.displayPersonInfo();  // Output: Name: Unknown, Age: 0

        // Using constructor with one parameter
        Person p2 = new Person("Alice");
        p2.displayPersonInfo();  // Output: Name: Alice, Age: 0

        // Using constructor with two parameters
        Person p3 = new Person("Bob", 25);
        p3.displayPersonInfo();  // Output: Name: Bob, Age: 25
    }
}
```

### Explanation:
- The class `Person` has three constructors:
  1. The default constructor initializes `name` as `"Unknown"` and `age` as `0`.
  2. The second constructor accepts a `String` parameter to initialize the `name`.
  3. The third constructor accepts both a `String` for the `name` and an `int` for the `age`.

This allows creating `Person` objects with varying levels of information.

## 2. Overloaded Methods
**Method overloading** is when multiple methods in a class share the same name but differ in parameters (either in number, type, or both).

### Key Features of Overloaded Methods:
- Same method name but different parameter lists.
- Return type can be the same or different, but it doesn't differentiate methods.
- Helps increase code readability by logically grouping similar operations under a single method name.

### Example: Overloaded Methods
```java
public class Calculator {
    
    // Method to add two integers
    public int add(int a, int b) {
        return a + b;
    }

    // Overloaded method to add three integers
    public int add(int a, int b, int c) {
        return a + b + c;
    }

    // Overloaded method to add two double values
    public double add(double a, double b) {
        return a + b;
    }

    public static void main(String[] args) {
        Calculator calc = new Calculator();

        // Calling add method with two integers
        System.out.println("Sum of two integers: " + calc.add(5, 10)); // Output: 15

        // Calling overloaded add method with three integers
        System.out.println("Sum of three integers: " + calc.add(5, 10, 15)); // Output: 30

        // Calling overloaded add method with two double values
        System.out.println("Sum of two doubles: " + calc.add(5.5, 10.5)); // Output: 16.0
    }
}
```

### Explanation:
- The class `Calculator` has three overloaded `add` methods:
  1. The first method accepts two `int` parameters.
  2. The second method accepts three `int` parameters.
  3. The third method accepts two `double` parameters.

All three methods have the same name (`add`), but the number or type of their parameters is different, which makes them unique.

## Rules for Overloading:
1. **Method name or constructor name must be the same**.
2. **Parameter list must be different**. This could mean:
   - Different number of parameters.
   - Different types of parameters.
   - Different order of parameters.
3. **Return type alone cannot be used to differentiate overloaded methods**.

### Practical Use of Overloading
Overloading can help create flexible and more intuitive APIs, allowing users to call methods or constructors with a variety of argument combinations without needing to remember multiple method names.

## Conclusion
Overloaded constructors and methods provide a way to define multiple versions of a constructor or method, each designed to handle different input types or numbers of arguments. This feature helps improve code readability and usability by offering different ways to instantiate objects or perform operations with a single method or constructor name.
