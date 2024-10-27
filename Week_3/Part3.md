# Part 3: Structures and Classes

## Structures (`struct`)

Structures are used to group variables of different types under a single name.

**Example: Defining and Using a `struct`**

```cpp
#include <iostream>
using namespace std;

struct Student {
    string name;
    int age;
    double gpa;
};

int main() {
    Student s1 = {"Alice", 20, 3.8};

    cout << "Name: " << s1.name << endl;
    cout << "Age: " << s1.age << endl;
    cout << "GPA: " << s1.gpa << endl;

    return 0;
}
```

## Classes

Classes are similar to structures but provide additional features like access control and member functions.

**Example: Basic Class Definition**

```cpp
#include <iostream>
using namespace std;

class Circle {
private:
    double radius;

public:
    // Constructor
    Circle(double r) : radius(r) {}

    // Member function
    double area() {
        return 3.1416 * radius * radius;
    }
};

int main() {
    Circle c(5.0);
    cout << "Area: " << c.area() << endl; // Output: 78.54

    return 0;
}
```

### Key Differences Between `struct` and `class`

- **Default Access Modifier**: Members of a `struct` are public by default, while those of a `class` are private.
- In competitive programming, using `struct` is often sufficient for grouping data.
