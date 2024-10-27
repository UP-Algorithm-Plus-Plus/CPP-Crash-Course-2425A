## Part 3: Structures and Classes

```markdown
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

---

## Part 5: Pairs and Tuples

```markdown
# Part 5: Pairs and Tuples

## Pairs

A **pair** is a container that stores two values, which may be of different types.

**Example: Using `pair`**

```cpp
#include <iostream>
#include <utility>
using namespace std;

int main() {
    pair<string, int> person;

    person.first = "Bob";
    person.second = 25;

    cout << person.first << " is " << person.second << " years old." << endl;
    // Output: Bob is 25 years old.

    return 0;
}
```

### Common Uses in Competitive Programming

- **Coordinates**: `pair<int, int>` to represent `(x, y)` positions.
- **Graph Edges**: `pair<int, int>` to represent edges between nodes.

**Example: Storing Coordinates**

```cpp
vector<pair<int, int>> points;

points.push_back({1, 2});
points.push_back({3, 4});
points.push_back({5, 6});

for (auto p : points) {
    cout << "(" << p.first << ", " << p.second << ")" << endl;
}
/* Output:
(1, 2)
(3, 4)
(5, 6)
*/
```

## Tuples (Optional)

A **tuple** can store multiple values of different types.

**Example: Using `tuple`**

```cpp
#include <iostream>
#include <tuple>
using namespace std;

int main() {
    tuple<string, int, char> t;

    t = make_tuple("Charlie", 30, 'M');

    cout << get<0>(t) << ", Age: " << get<1>(t) << ", Gender: " << get<2>(t) << endl;
    // Output: Charlie, Age: 30, Gender: M

    return 0;
}
```

### When to Use Tuples

- When you need to store more than two values together.
- Less common in competitive programming but useful in certain scenarios.

