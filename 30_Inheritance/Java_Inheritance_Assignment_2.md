
# Assignment 2: Employee Management System

**Objective:** Practice building a multilevel inheritance structure, using constructors with `super`, and accessing protected and package-private members.

### Instructions:

1. **Create the following classes:**
   - `Person`: This is the superclass with:
     - Fields for `name` (String) and `age` (int).
     - A constructor to initialize these fields.
     - A `displayInfo()` method that prints "Name: [name], Age: [age]".
   - `Employee`: A subclass of `Person` with:
     - A field for `employeeId` (String).
     - A constructor that initializes `name`, `age`, and `employeeId` using the `super` keyword to call `Person`’s constructor.
     - A `work()` method that prints "[name] is working."

2. **Create a subclass `Manager` that inherits from `Employee`:**
   - Add a `protected` field `department` (String).
   - Create a constructor that sets `name`, `age`, `employeeId`, and `department`.
   - Add a `manage()` method that prints "[name] manages the [department] department."

3. **Write a `Company` class to test the hierarchy:**
   - Create instances of `Employee` and `Manager`.
   - Call `displayInfo()`, `work()`, and `manage()` on the `Manager` instance, noting any `protected` or package-private access limitations you encounter.

### Expected Output Example:
```plaintext
Name: John Doe, Age: 35
John Doe is working.
John Doe manages the IT department.
```
