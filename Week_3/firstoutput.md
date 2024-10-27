


---

## Part 2: Dynamic Linear Data Structures

```markdown
# Part 2: Dynamic Linear Data Structures

## Vectors

A **vector** is a dynamic array provided by the C++ Standard Template Library (STL). Vectors can resize themselves automatically when an element is inserted or deleted.

### Declaring a Vector

```cpp
#include <vector>
vector<int> v; // An empty vector of integers
```

**Example: Using Vectors**

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    vector<int> v;

    // Adding elements
    v.push_back(5);
    v.push_back(10);
    v.push_back(15);

    // Accessing elements
    cout << "First element: " << v[0] << endl; // Output: 5

    // Iterating over elements
    for (int i = 0; i < v.size(); ++i) {
        cout << v[i] << " ";
    }
    // Output: 5 10 15

    return 0;
}
```

### Time Complexities for Vectors

- **Access**: O(1)
- **Insertion/Deletion at End**: Amortized O(1)
- **Insertion/Deletion at Beginning/Middle**: O(n)
- **Search (Unsorted)**: O(n)
- **Search (Sorted)**: O(log n) with algorithms like `binary_search`

## Strings as Vectors

In C++, the `string` class functions similarly to a vector of characters.

**Example: Manipulating Strings**

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s = "Hello";

    // Appending
    s += " World";

    // Accessing characters
    cout << s[6] << endl; // Output: W

    // Iterating over characters
    for (char c : s) {
        cout << c << " ";
    }
    // Output: H e l l o   W o r l d

    return 0;
}
```

### Time Complexities for Strings

- **Access**: O(1)
- **Insertion/Deletion at End**: O(1)
- **Insertion/Deletion at Beginning/Middle**: O(n)
- **Search**: O(n)

## Stacks, Queues, and Deques

These are specialized data structures that follow specific rules for insertion and deletion.

### Stack

A **stack** is a Last-In-First-Out (LIFO) data structure.

**Example: Using a Stack**

```cpp
#include <iostream>
#include <stack>
using namespace std;

int main() {
    stack<int> s;

    // Pushing elements
    s.push(1);
    s.push(2);
    s.push(3);

    // Popping elements
    while (!s.empty()) {
        cout << s.top() << " ";
        s.pop();
    }
    // Output: 3 2 1

    return 0;
}
```

### Queue

A **queue** is a First-In-First-Out (FIFO) data structure.

**Example: Using a Queue**

```cpp
#include <iostream>
#include <queue>
using namespace std;

int main() {
    queue<int> q;

    // Enqueuing elements
    q.push(1);
    q.push(2);
    q.push(3);

    // Dequeuing elements
    while (!q.empty()) {
        cout << q.front() << " ";
        q.pop();
    }
    // Output: 1 2 3

    return 0;
}
```

### Deque

A **deque** (double-ended queue) allows insertion and deletion at both ends.

**Example: Using a Deque**

```cpp
#include <iostream>
#include <deque>
using namespace std;

int main() {
    deque<int> d;

    // Inserting elements at both ends
    d.push_back(1);
    d.push_front(2);

    // Accessing elements
    cout << d.front() << " "; // Output: 2
    cout << d.back() << endl; // Output: 1

    // Iterating over elements
    for (int num : d) {
        cout << num << " ";
    }
    // Output: 2 1

    return 0;
}
```

### Time Complexities

| Operation                 | Stack | Queue | Deque |
|---------------------------|-------|-------|-------|
| Insertion at End          | O(1)  | O(1)  | O(1)  |
| Deletion at End           | O(1)  | N/A   | O(1)  |
| Insertion at Beginning    | N/A   | N/A   | O(1)  |
| Deletion at Beginning     | N/A   | O(1)  | O(1)  |
| Access (Random)           | N/A   | N/A   | O(1)  |

*Note:* Stacks and queues do not allow random access; you can only access the element at the top (stack) or front (queue).

---

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

