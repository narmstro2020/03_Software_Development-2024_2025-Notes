
# Java POJO Assignments

## Assignment 1: POJO without `record` (Regular Class)

**Title**: **Student Enrollment System**

### Objective:
Create a simple POJO representing a `Student` in a student enrollment system.

### Instructions:
1. Create a `Student` class with the following private fields:
    - `String studentId`
    - `String firstName`
    - `String lastName`
    - `int age`
    - `String major`

2. Add a default constructor that initializes all fields to default values.

3. Add a parameterized constructor to initialize all the fields.

4. Implement getter and setter methods for each field.

5. Implement a `toString` method that returns a string representation of the student in the format:
   ```
   Student ID: 12345, Name: John Doe, Age: 20, Major: Computer Science
   ```

6. Create a `StudentEnrollment` class with a `main` method to:
    - Create a list of at least 3 `Student` objects.
    - Print out the details of each student using the `toString` method.
    - Update the major of one student and print the updated information.

### Sample Output:
```java
Student ID: 12345, Name: John Doe, Age: 20, Major: Computer Science
Student ID: 23456, Name: Jane Smith, Age: 21, Major: Mathematics
Student ID: 34567, Name: Bob Johnson, Age: 19, Major: Physics

Updated Major for Student ID: 12345, Name: John Doe, Age: 20, Major: Data Science
```