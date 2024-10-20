
## **Assignments**

### **Assignment 1: Dog and Cat Class Implementation**

In this assignment, you will implement two classes: `Dog` and `Cat`. These classes will demonstrate your understanding of fields, constructors, methods, and access modifiers.

#### **Task:**

1. Create a class called `Dog` with the following fields:
   - `name` (String) – public access modifier
   - `breed` (String) – private access modifier
   - `age` (int) – protected access modifier
   - `species` (String) – static field with a value of `"Canine"`

2. Create a class called `Cat` with the following fields:
   - `name` (String) – public access modifier
   - `color` (String) – private access modifier
   - `age` (int) – protected access modifier
   - `species` (String) – static field with a value of `"Feline"`

3. Create the following constructors for both `Dog` and `Cat` classes:
   - A parameterized constructor that takes all fields as parameters (`name`, `breed`/`color`, `age`).
   - A default constructor that initializes the fields to default values (`name = "Unknown"`, `breed/color = "Unknown"`, `age = 0`).

4. Implement the following methods for both `Dog` and `Cat`:
   - A **public method** `getBreed`/`getColor` to return the `breed` (for `Dog`) or `color` (for `Cat`) value.
   - A **protected method** `displayAnimalInfo` that prints the animal’s `name`, `breed`/`color`, and `age`.
   - A **static method** `displaySpecies` that prints the species of the animal.

5. Create a `main` method to:
   - Create two `Dog` objects and two `Cat` objects, one using the parameterized constructor and the other using the default constructor.
   - Call the `displayAnimalInfo` method on each object.
   - Call the static method `displaySpecies` to show the species of the animals.

#### **Sample Output**:

```
Dog 1: Name: Max, Breed: Labrador, Age: 5
Dog 2: Name: Unknown, Breed: Unknown, Age: 0
All dogs are of species: Canine

Cat 1: Name: Whiskers, Color: Black, Age: 3
Cat 2: Name: Unknown, Color: Unknown, Age: 0
All cats are of species: Feline
```
