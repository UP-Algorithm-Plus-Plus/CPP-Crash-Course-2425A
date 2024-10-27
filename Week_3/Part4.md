# Part 4: Pairs and Tuples

In this part, we will explore **pairs** and **tuples**, which are useful data structures in C++ for grouping multiple values together.

## Pairs

A **pair** is a container that stores two values, which may be of different types. It is defined in the `<utility>` header.

### Using `pair`

To use a `pair`, include the `<utility>` header and use the `pair` template class.

```cpp
#include <iostream>
#include <utility> // Include the utility header for pair
#include <string>

using namespace std;

int main() {
    // Declaring a pair with a string and an int
    pair<string, int> person;

    // Assigning values to the pair
    person.first = "Bob";
    person.second = 25;

    // Alternatively, you can initialize it using make_pair
    // pair<string, int> person = make_pair("Bob", 25);

    // Accessing the elements of the pair
    cout << person.first << " is " << person.second << " years old." << endl;
    // Output: Bob is 25 years old.

    return 0;
}
```

**Explanation:**

- **Declaration:** We declare a `pair` named `person` that holds a `string` and an `int`.
- **Assignment:** We assign values to `person.first` and `person.second`.
- **Accessing Elements:** We access the elements using `.first` and `.second`.

### Common Uses in Competitive Programming

Pairs are often used in competitive programming for:

- **Coordinates:** `pair<int, int>` to represent `(x, y)` positions.
- **Graph Edges:** `pair<int, int>` to represent edges between nodes.
- **Key-Value Pairs:** Storing key-value pairs in maps.

**Example: Storing Coordinates**

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    // Vector of pairs to store points
    vector<pair<int, int>> points;

    // Adding points to the vector
    points.push_back({1, 2});
    points.push_back({3, 4});
    points.push_back({5, 6});

    // Iterating over the vector of pairs
    cout << "Points:" << endl;
    for (auto p : points) {
        cout << "(" << p.first << ", " << p.second << ")" << endl;
    }
    /* Output:
    Points:
    (1, 2)
    (3, 4)
    (5, 6)
    */

    return 0;
}
```

**Explanation:**

- **Vector of Pairs:** We use `vector<pair<int, int>>` to store multiple coordinate points.
- **Adding Elements:** We use `push_back` to add pairs to the vector.
- **Accessing Elements:** We access the elements using `.first` and `.second`.

<br>

### Assignment

---

**Task:** Write a C++ program that:

1. Creates a `pair` to store a country's name and its population (as an integer).
2. Initializes the pair with a country of your choice.
3. Prints out the country's name and population.

**Example Output:**

```
Country: Canada
Population: 37742154
```

**Hint:** Use `pair<string, int>` and initialize it using `make_pair` or by directly assigning to `.first` and `.second`.

---

<br>

## Tuples

A **tuple** can store multiple values of different types. Unlike pairs, tuples can hold more than two elements. Tuples are defined in the `<tuple>` header.

### Using `tuple`

To use a `tuple`, include the `<tuple>` header and use the `tuple` template class.

```cpp
#include <iostream>
#include <tuple> // Include the tuple header
#include <string>

using namespace std;

int main() {
    // Declaring a tuple with a string, int, and char
    tuple<string, int, char> person;

    // Assigning values to the tuple using make_tuple
    person = make_tuple("Charlie", 30, 'M');

    // Alternatively, you can initialize it directly
    // tuple<string, int, char> person("Charlie", 30, 'M');

    // Accessing tuple elements using std::get
    cout << get<0>(person) << ", Age: " << get<1>(person) << ", Gender: " << get<2>(person) << endl;
    // Output: Charlie, Age: 30, Gender: M

    // Modifying tuple elements
    get<1>(person) = 31; // Updating age to 31

    // Printing updated tuple
    cout << get<0>(person) << " is now " << get<1>(person) << " years old." << endl;
    // Output: Charlie is now 31 years old.

    return 0;
}
```

**Explanation:**

- **Declaration:** We declare a `tuple` named `person` that holds a `string`, `int`, and `char`.
- **Initialization:** We use `make_tuple` to initialize the tuple.
- **Accessing Elements:** We use `get<index>(tuple)` to access elements.
- **Modifying Elements:** We can modify elements by assigning to `get<index>(tuple)`.

### When to Use Tuples

- **Multiple Return Values:** Functions can return multiple values using a tuple.
- **Grouping Data:** When you need to group more than two related values.
- **Less Common in Competitive Programming:** Tuples are less commonly used in competitive programming due to their verbosity but can be useful in certain cases.

**Example: Returning Multiple Values from a Function**

```cpp
#include <iostream>
#include <tuple>
using namespace std;

// Function that returns multiple values using a tuple
tuple<int, int, int> calculate(int a, int b) {
    int sum = a + b;
    int diff = a - b;
    int prod = a * b;
    return make_tuple(sum, diff, prod);
}

int main() {
    int a = 5, b = 3;

    // Calling the function and storing the returned tuple
    tuple<int, int, int> results = calculate(a, b);

    // Unpacking the tuple
    int sum, diff, prod;
    tie(sum, diff, prod) = results;

    cout << "Sum: " << sum << endl;       // Output: Sum: 8
    cout << "Difference: " << diff << endl; // Output: Difference: 2
    cout << "Product: " << prod << endl;    // Output: Product: 15

    return 0;
}
```

**Explanation:**

- **Function Returning Tuple:** The `calculate` function returns a tuple containing three integers.
- **Unpacking Tuple:** We use `tie` to unpack the tuple into separate variables.

<br>

### Assignment

---

**Task:** Write a C++ program that:

1. Defines a `tuple` to store a student's name (`string`), age (`int`), grade (`char`), and GPA (`double`).
2. Initializes the tuple with a student's information.
3. Prints out each piece of information.

**Example Output:**

```
Name: Emily
Age: 22
Grade: A
GPA: 3.9
```

**Hint:**

- Use `tuple<string, int, char, double> student`.
- Access elements using `get<index>(student)`.
- You can use `make_tuple` to initialize the tuple.

---

<br>

By understanding how to use pairs and tuples, you can efficiently group and manage multiple related data elements in your C++ programs.

---

## Knowledge check
These questions provide a chance to think about the important topics covered in this lesson. If you're unsure of an answer, revisit the material. Remember, you're not expected to memorize or fully master this information right now.
- [How do you declare and initialize a two dimensional array?](https://github.com/UP-Algorithm-Plus-Plus/CPP-Crash-Course-2425A/blob/main/Week_3/Part1.md#two-dimensional-arrays)
- [How do you input and output data to and from a two dimensional array?](https://github.com/UP-Algorithm-Plus-Plus/CPP-Crash-Course-2425A/blob/main/Week_3/Part1.md#two-dimensional-arrays)

## Additional Resources
This section offers useful links to relevant content. It's optional and meant to be extra material for further reading.(Note: Some resources might require you you to have access to the Algo++ Google drive in order to view it.)
- [UP Algo++ Static Linear DS Lecture Slides](https://docs.google.com/presentation/d/1K3jiqlSqMxRToh926U01xdX73ib2k4xXWa2EpYysHFU/edit#slide=id.g164c8dcc09a_1_48)