
# Java Tutorial: Interfaces

## 1. Introduction to Interfaces
An **interface** in Java is a reference type, similar to a class, that can contain only abstract methods, default methods, static methods, and constant declarations. Interfaces are used to achieve abstraction and multiple inheritance in Java.

## 2. Vocabulary
- **Interface**: A contract that a class can implement, which mandates that the class must provide concrete implementations for the methods declared in the interface.
- **Abstract Method**: A method without a body that must be implemented by any class that implements the interface.
- **Implements Keyword**: The keyword used by a class to indicate that it is implementing an interface.
- **Default Method**: A method within an interface that has a default implementation.
- **Static Method**: A method within an interface that belongs to the interface itself and not to an instance of a class.

## 3. Basic Structure and Syntax of an Interface
```java
public interface Animal {
    void makeSound(); // abstract method

    default void eat() {
        System.out.println("This animal is eating.");
    }

    static void description() {
        System.out.println("This is an animal interface.");
    }
}
```

## 4. Implementing an Interface
When a class implements an interface, it must provide implementations for all of its abstract methods.
```java
public class Dog implements Animal {
    @Override
    public void makeSound() {
        System.out.println("Woof! Woof!");
    }

    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.makeSound(); // Outputs: Woof! Woof!
        dog.eat();       // Outputs: This animal is eating.
        Animal.description(); // Outputs: This is an animal interface.
    }
}
```

## 5. When to Use Interfaces
- **Multiple Inheritance**: Interfaces are used to allow a class to inherit behaviors from multiple sources since Java does not support multiple inheritance with classes.
- **Defining Contracts**: Interfaces are ideal for creating a contract that classes must follow. For example, a `Flyable` interface can ensure that all classes implementing it will have a `fly()` method.
- **Decoupling Code**: Using interfaces helps achieve loose coupling in code, making it more flexible and easier to maintain.

## 6. Big Assignment: Building a Payment Processing System

**Objective**: Create a payment processing system where different types of payment methods (Credit Card, PayPal, Bank Transfer) implement a common interface.

### Step 1: Define the `Payment` interface
```java
public interface Payment {
    void processPayment(double amount);
}
```

### Step 2: Implement the `CreditCardPayment` class
```java
public class CreditCardPayment implements Payment {
    @Override
    public void processPayment(double amount) {
        System.out.println("Processing credit card payment of $" + amount);
    }
}
```

### Step 3: Implement the `PayPalPayment` class
```java
public class PayPalPayment implements Payment {
    @Override
    public void processPayment(double amount) {
        System.out.println("Processing PayPal payment of $" + amount);
    }
}
```

### Step 4: Implement the `BankTransferPayment` class
```java
public class BankTransferPayment implements Payment {
    @Override
    public void processPayment(double amount) {
        System.out.println("Processing bank transfer payment of $" + amount);
    }
}
```

### Step 5: Create a `PaymentProcessor` class
```java
public class PaymentProcessor {
    public void processPayment(Payment paymentMethod, double amount) {
        paymentMethod.processPayment(amount);
    }

    public static void main(String[] args) {
        Payment creditCard = new CreditCardPayment();
        Payment payPal = new PayPalPayment();
        Payment bankTransfer = new BankTransferPayment();

        PaymentProcessor processor = new PaymentProcessor();
        processor.processPayment(creditCard, 150.00);
        processor.processPayment(payPal, 200.50);
        processor.processPayment(bankTransfer, 1000.00);
    }
}
```

### Expected Output
```
Processing credit card payment of $150.0
Processing PayPal payment of $200.5
Processing bank transfer payment of $1000.0
```

## 7. Solution Explanation
- The `Payment` interface is used to define a contract that ensures all payment methods have a `processPayment` method.
- Each class (`CreditCardPayment`, `PayPalPayment`, `BankTransferPayment`) implements the `Payment` interface and provides its own implementation of the `processPayment` method.
- The `PaymentProcessor` class takes any implementation of `Payment` and processes it, showcasing the use of polymorphism with interfaces.

By following this structure, you have created a modular and scalable payment processing system that adheres to the principles of interface-driven design.
