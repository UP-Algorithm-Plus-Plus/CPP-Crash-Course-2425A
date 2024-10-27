# Part 3: Structures and Classes

In this part, we will delve into **structures** (`struct`) and **classes** in C++. These are fundamental concepts in object-oriented programming that allow you to group related variables and functions.

## Structures (`struct`)

Structures are used to group variables of different types under a single name. They are particularly useful for representing complex data types.

### Defining and Using a `struct`

To define a structure, use the `struct` keyword followed by the structure name and its members enclosed in braces `{}`.

```cpp
#include <iostream>
#include <string> // Include the string library
using namespace std;

struct Student {
    string name;
    int age;
    double gpa;
};

int main() {
    // Creating an instance of Student and initializing it
    Student s1 = {"Alice", 20, 3.8};

    // Accessing struct members using the dot operator
    cout << "Name: " << s1.name << endl;
    cout << "Age: " << s1.age << endl;
    cout << "GPA: " << s1.gpa << endl;

    return 0;
}
```

**Explanation:**

- **Definition:** We define a `Student` structure with three members: `name`, `age`, and `gpa`.
- **Initialization:** We create an instance `s1` of `Student` and initialize it with values.
- **Accessing Members:** We access the members using the dot `.` operator.

<br>

### Assignment

---

**Task:** Write a C++ program that:

1. Defines a `struct` named `Book` with the following members:
   - `string title`
   - `string author`
   - `int pages`
2. Creates an instance of `Book` and initializes it with values of your choice.
3. Prints out the details of the book.

**Example Output:**

```
Title: The Great Gatsby
Author: F. Scott Fitzgerald
Pages: 180
```

**Hint:** Use the same structure as the `Student` example. Don't forget to include the `<string>` library.

---

<br>

## Classes

Classes are similar to structures but provide additional features like access control, constructors, and member functions. They are the building blocks of object-oriented programming in C++.

### Basic Class Definition

Classes encapsulate data (attributes) and functions (methods) that operate on that data.

```cpp
#include <iostream>
using namespace std;

class Circle {
private:
    double radius;

public:
    // Constructor
    Circle(double r) : radius(r) {}

    // Setter method
    void setRadius(double r) {
        radius = r;
    }

    // Getter method
    double getRadius() const {
        return radius;
    }

    // Member function to calculate area
    double area() const {
        return 3.1416 * radius * radius;
    }
};

int main() {
    Circle c(5.0);

    cout << "Radius: " << c.getRadius() << endl;
    cout << "Area: " << c.area() << endl;

    // Changing the radius
    c.setRadius(3.0);

    cout << "New Radius: " << c.getRadius() << endl;
    cout << "New Area: " << c.area() << endl;

    return 0;
}
```

**Explanation:**

- **Private Members:** The `radius` variable is private, meaning it cannot be accessed directly from outside the class.
- **Constructor:** Initializes the `radius` when a new `Circle` object is created.
- **Getter and Setter:** `getRadius()` and `setRadius()` methods allow controlled access to the private `radius` variable.
- **Member Functions:** Functions like `area()` perform operations related to the class.

<br>

### Assignment

---

**Task:** Write a C++ program that:

1. Defines a `class` named `Rectangle` with private members `width` and `height`.
2. Includes the following:
   - A constructor that initializes `width` and `height`.
   - Getter and setter methods for both `width` and `height`.
   - A member function `area()` that returns the area of the rectangle.
3. Creates an instance of `Rectangle`, sets its width and height, and prints out its area.

**Example Output:**

```
Width: 4
Height: 5
Area: 20
```

**Hint:** Follow the pattern from the `Circle` class example. Use getter and setter methods to access private members.

---

<br>

## Key Differences Between `struct` and `class`

- **Default Access Modifier:**
  - **`struct`:** Members are **public** by default.
  - **`class`:** Members are **private** by default.
- **Usage:**
  - **`struct`:** Often used for passive objects with public data members and no functions.
  - **`class`:** Used when you need encapsulation, access control, and member functions.

> **Note:** In competitive programming, using `struct` is often sufficient for grouping data without the overhead of access control.


## Knowledge check
These questions provide a chance to think about the important topics covered in this lesson. If you're unsure of an answer, revisit the material. Remember, you're not expected to memorize or fully master this information right now.
- [How do you declare and initialize a two dimensional array?](https://github.com/UP-Algorithm-Plus-Plus/CPP-Crash-Course-2425A/blob/main/Week_3/Part1.md#two-dimensional-arrays)
- [How do you input and output data to and from a two dimensional array?](https://github.com/UP-Algorithm-Plus-Plus/CPP-Crash-Course-2425A/blob/main/Week_3/Part1.md#two-dimensional-arrays)

## Additional Resources
This section offers useful links to relevant content. It's optional and meant to be extra material for further reading.(Note: Some resources might require you you to have access to the Algo++ Google drive in order to view it.)
- [UP Algo++ Static Linear DS Lecture Slides](https://docs.google.com/presentation/d/1K3jiqlSqMxRToh926U01xdX73ib2k4xXWa2EpYysHFU/edit#slide=id.g164c8dcc09a_1_48)


