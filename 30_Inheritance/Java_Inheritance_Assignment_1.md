
# Assignment 1: Creating an Animal Hierarchy

**Objective:** Practice creating a class hierarchy with inheritance, applying the `protected` access modifier, and understanding method overriding.

### Instructions:

1. **Create the following classes:**
   - `Animal`: This is the superclass with:
     - A protected field `species` (String) to hold the type of animal (e.g., "Mammal," "Bird").
     - A method `makeSound()` that prints "Some generic animal sound."
   - `Bird`: A subclass of `Animal` with:
     - A constructor that sets `species` to "Bird."
     - An overridden `makeSound()` method that prints "Chirp chirp."
   - `Mammal`: Another subclass of `Animal` with:
     - A constructor that sets `species` to "Mammal."
     - An overridden `makeSound()` method that prints "Some mammal sound."

2. **Create another class `Dog` that inherits from `Mammal`:**
   - Implement an overridden `makeSound()` method that prints "Woof woof."

3. **Write a `Zoo` class to test the hierarchy:**
   - Create an array of `Animal` objects and add instances of `Bird`, `Mammal`, and `Dog` to it.
   - Use a loop to call `makeSound()` on each object in the array, observing polymorphism in action.

### Expected Output Example:
```plaintext
Chirp chirp
Some mammal sound
Woof woof
```
