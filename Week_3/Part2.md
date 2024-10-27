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