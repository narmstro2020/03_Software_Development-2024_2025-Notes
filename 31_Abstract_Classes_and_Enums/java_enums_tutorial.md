
# Java Enums Tutorial

## Introduction to Enums in Java
Enums (short for "enumerations") are a special Java type used to define collections of constants. Enums are particularly useful when a variable can only take one out of a small set of possible values. They make the code more readable and less error-prone.

## Vocabulary Words
- **Enum**: A special type in Java that represents a group of constants.
- **Constant**: A fixed value that doesn’t change during the execution of a program.
- **Ordinal**: The position of an enum constant in its type, starting from zero.
- **Values() Method**: A built-in method that returns an array containing all the enum constants in the order they are declared.
- **Switch Statement**: A control statement that tests a variable against multiple conditions.

## Enum Definition in Java
Enums are defined using the `enum` keyword.

**Example**:
```java
public enum Day {
    MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, SUNDAY;
}
```

## Example 1: Basic Enum Usage
Enums can be used in a variety of ways, such as in switch statements or to simplify logic.

**Code Example**:
```java
public class EnumExample {
    public static void main(String[] args) {
        Day today = Day.FRIDAY;

        switch (today) {
            case MONDAY:
                System.out.println("Start of the work week.");
                break;
            case FRIDAY:
                System.out.println("It's almost the weekend!");
                break;
            case SATURDAY: case SUNDAY:
                System.out.println("It's the weekend!");
                break;
            default:
                System.out.println("Just another day.");
        }
    }
}
```

**Explanation**: 
- The `switch` statement matches the `today` variable with the corresponding `case`.
- Enums can be used to simplify checks without needing multiple `if` statements.

## Example 2: Enum with Fields and Methods
Enums can have fields, constructors, and methods. This makes them powerful for more complex scenarios.

**Code Example**:
```java
public enum Season {
    SPRING("Warm and blooming"),
    SUMMER("Hot and sunny"),
    FALL("Cool and windy"),
    WINTER("Cold and snowy");

    private String description;

    // Constructor
    Season(String description) {
        this.description = description;
    }

    // Getter method
    public String getDescription() {
        return description;
    }
}

public class EnumWithFieldsExample {
    public static void main(String[] args) {
        for (Season season : Season.values()) {
            System.out.println(season + ": " + season.getDescription());
        }
    }
}
```

**Explanation**:
- Each enum constant is associated with a description.
- The `getDescription()` method allows retrieval of the description.

## Enum Methods and Properties
- **`values()`**: Returns an array of all enum constants.
- **`valueOf(String name)`**: Returns the enum constant with the specified name.
- **`ordinal()`**: Returns the position of the enum constant.

**Example**:
```java
public class EnumMethodsExample {
    public static void main(String[] args) {
        Season currentSeason = Season.FALL;
        
        // Using ordinal()
        System.out.println("Ordinal of FALL: " + currentSeason.ordinal());
        
        // Using valueOf()
        Season summer = Season.valueOf("SUMMER");
        System.out.println("Using valueOf: " + summer);
    }
}
```

## Assignment: Enum-Based Task Management System
**Objective**: Create a program to manage and display tasks based on their priority level. The program should use an `enum` to define priority levels and provide a list of tasks associated with each level.

**Instructions**:
1. Create an `enum` called `Priority` with constants `LOW`, `MEDIUM`, and `HIGH`, each with a description (e.g., "Low urgency", "Medium urgency", etc.).
2. Create a `Task` class with the following fields:
   - `String name` (name of the task)
   - `Priority priority` (priority level of the task)
3. Implement methods in the `Task` class to:
   - Display task details.
4. Create a main class that:
   - Initializes an array or list of `Task` objects.
   - Sorts tasks by priority (e.g., from `HIGH` to `LOW`).
   - Displays the sorted list.

**Expected Output**:
A list of tasks printed in order of priority, showing their names and descriptions.

**Hints**:
- Use `Arrays.sort()` or a suitable collection sort method with a custom comparator for sorting tasks.
- You may find it useful to use the `ordinal()` method of `enum` in your comparator logic.

## Assignment Solution
**Code Example**:
```java
// Step 1: Define the Priority enum
public enum Priority {
    HIGH("High urgency"),
    MEDIUM("Medium urgency"),
    LOW("Low urgency");

    private String description;

    Priority(String description) {
        this.description = description;
    }

    public String getDescription() {
        return description;
    }
}

// Step 2: Create the Task class
class Task {
    private String name;
    private Priority priority;

    public Task(String name, Priority priority) {
        this.name = name;
        this.priority = priority;
    }

    public Priority getPriority() {
        return priority;
    }

    public void displayTask() {
        System.out.println("Task: " + name + " | Priority: " + priority + " (" + priority.getDescription() + ")");
    }
}

// Step 3: Main class to initialize and sort tasks
import java.util.Arrays;

public class TaskManager {
    public static void main(String[] args) {
        // Initialize tasks
        Task[] tasks = {
            new Task("Complete report", Priority.HIGH),
            new Task("Email client", Priority.MEDIUM),
            new Task("Schedule meeting", Priority.LOW),
            new Task("Prepare presentation", Priority.HIGH),
            new Task("Review code", Priority.MEDIUM)
        };

        // Sort tasks by priority (from HIGH to LOW)
        Arrays.sort(tasks, (task1, task2) -> task1.getPriority().ordinal() - task2.getPriority().ordinal());

        // Display sorted tasks
        System.out.println("Tasks sorted by priority:");
        for (Task task : tasks) {
            task.displayTask();
        }
    }
}
```

**Explanation**:
- The `Priority` enum has three levels, each with a description.
- The `Task` class includes fields for the task's name and priority, with a method to display the task details.
- The main class `TaskManager` creates an array of `Task` objects, sorts them by priority using a custom comparator, and displays them.
