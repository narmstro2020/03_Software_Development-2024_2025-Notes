### **Assignment 2: Static vs Instance Fields and Methods**

In this assignment, you will create a class called `Library` and explore the difference between static and instance fields and methods.

#### **Task:**

1. Create a class called `Library` with the following fields:
   - `name` (String) – public access modifier, instance field for the name of the library.
   - `totalBooks` (static int) – public access modifier, static field that tracks the total number of books across all libraries.

2. Implement the following methods:
   - A **public method** `addBooks(int numBooks)` that adds books to the library and increases the `totalBooks` static field.
   - A **public static method** `getTotalBooks` that returns the total number of books across all libraries.

3. Create a `main` method to:
   - Create two `Library` objects (`Library A` and `Library B`).
   - Add 100 books to `Library A` and 150 books to `Library B`.
   - Display the total number of books across both libraries using the `getTotalBooks` method.

#### **Sample Output**:

```
Library A added 100 books.
Library B added 150 books.
Total books in all libraries: 250
```
