# Part 4: Pairs and Tuples

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

