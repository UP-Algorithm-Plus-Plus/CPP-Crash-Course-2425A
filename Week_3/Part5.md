# Part 5: Pairs and Tuples

In this part, we'll explore **pairs** and **tuples** in C++, which are data structures used to group multiple values together. They are especially useful when you need to combine different types of data without creating a full-fledged `struct` or `class`.

## Pairs

A **pair** is a simple container that holds exactly two values, which can be of different types. It's defined in the `<utility>` header.

### How to Use `pair`

To use a `pair`, include the `<utility>` header. Here's how you can declare and initialize a pair:

```cpp
#include <iostream>
#include <utility> // For std::pair
#include <string>

using namespace std;

int main() {
    // Declaring a pair to hold a string and an int
    pair<string, int> person;

    // Assigning values to the pair
    person.first = "Bob";
    person.second = 25;

    // Alternatively, initialize the pair using make_pair
    // pair<string, int> person = make_pair("Bob", 25);

    // Or using list initialization (C++11 and later)
    // pair<string, int> person{"Bob", 25};

    // Accessing the elements of the pair
    cout << person.first << " is " << person.second << " years old." << endl;
    // Output: Bob is 25 years old.

    return 0;
}
```

**Explanation:**

- **Declaration:** We declare a `pair` named `person` that holds a `string` and an `int`.
- **Assigning Values:** We assign values to `person.first` and `person.second`, which represent the first and second elements of the pair.
- **Accessing Elements:** We access the elements using `.first` and `.second`.

### Common Uses of Pairs

Pairs are often used in competitive programming and general C++ programming for:

- **Storing Coordinates:** `pair<int, int>` can represent a point `(x, y)` in 2D space.
- **Associating Data:** Combining two related pieces of information, like a value and its index.
- **Map Iteration:** When iterating over a `map`, each element is a `pair` containing a key and a value.

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
    for (const auto& p : points) {
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
- **Adding Elements:** We add pairs to the vector using `push_back`.
- **Accessing Elements:** We access each pair's elements using `.first` and `.second`.

### Simplifying with `auto`

To make the code cleaner, especially when dealing with complex types, you can use the `auto` keyword:

```cpp
for (const auto& p : points) {
    // ...
}
```

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

**Hint:** Use `pair<string, int>` and initialize it using `make_pair`, list initialization, or by directly assigning to `.first` and `.second`.

---

<br>

## Tuples

A **tuple** is similar to a pair but can hold more than two values, each potentially of different types. Tuples are defined in the `<tuple>` header.

### How to Use `tuple`

Include the `<tuple>` header to use tuples. Here's how to declare and initialize a tuple:

```cpp
#include <iostream>
#include <tuple> // For std::tuple
#include <string>

using namespace std;

int main() {
    // Declaring a tuple with a string, int, and char
    tuple<string, int, char> person;

    // Assigning values to the tuple using make_tuple
    person = make_tuple("Charlie", 30, 'M');

    // Alternatively, initialize it directly
    // tuple<string, int, char> person("Charlie", 30, 'M');

    // Or using tie-like syntax (C++17 and later)
    // auto person = make_tuple("Charlie", 30, 'M');

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

- **Declaration:** We declare a `tuple` named `person` that holds a `string`, an `int`, and a `char`.
- **Initialization:** We use `make_tuple` to initialize the tuple.
- **Accessing Elements:** We use `get<index>(tuple)` to access elements, where `index` starts from 0.
- **Modifying Elements:** We can modify elements by assigning to `get<index>(tuple)`.

### Unpacking Tuples

To extract all the values from a tuple at once, you can use `tie`:

```cpp
string name;
int age;
char gender;

tie(name, age, gender) = person;
```

Or in C++17 and later, you can use structured bindings:

```cpp
auto [name, age, gender] = person;
```

### When to Use Tuples

- **Multiple Return Values:** Functions can return multiple values using a tuple.
- **Grouping Data:** When you need to group several related values without creating a `struct` or `class`.
- **Temporary Grouping:** Useful for short-term grouping of values.

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
    auto results = calculate(a, b);

    // Unpacking the tuple using tie
    int sum, diff, prod;
    tie(sum, diff, prod) = results;

    cout << "Sum: " << sum << endl;          // Output: Sum: 8
    cout << "Difference: " << diff << endl;  // Output: Difference: 2
    cout << "Product: " << prod << endl;     // Output: Product: 15

    // Alternatively, in C++17 and later, use structured bindings
    // auto [sum, diff, prod] = calculate(a, b);

    return 0;
}
```

**Explanation:**

- **Function Returning Tuple:** The `calculate` function returns a tuple containing three integers.
- **Unpacking Tuple:** We use `tie` to unpack the tuple into separate variables.
- **Alternative with Structured Bindings:** In C++17 and later, you can use structured bindings to unpack tuples more conveniently.

### Important Notes on Tuples

- **Verbosity:** Tuples can become hard to manage when they hold many elements because you have to remember the order and types of elements.
- **Readability:** For complex data, consider using a `struct` or `class` for better readability.

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
- You can initialize the tuple using `make_tuple` or directly.

---

<br>

## Summary

- **Pairs and Tuples** are useful for grouping multiple values together without defining a new `struct` or `class`.
- **Pairs** hold exactly two values, accessible via `.first` and `.second`.
- **Tuples** can hold any number of values, accessible via `get<index>(tuple)`.
- Use **pairs** and **tuples** when you need to group data temporarily or for simple data structures.

## When to Use Pairs and Tuples

- **Quick Grouping:** When you need to combine a few values without extra overhead.
- **Standard Library Functions:** Some STL functions return pairs or tuples.
- **Competitive Programming:** Useful for concise code, but be cautious about readability.


<br>

## Knowledge check
These questions provide a chance to think about the important topics covered in this lesson. If you're unsure of an answer, revisit the material. Remember, you're not expected to memorize or fully master this information right now.
- [

<br>

## Additional Resources
This section offers useful links to relevant content. It's optional and meant to be extra material for further reading.(Note: Some resources might require you you to have access to the Algo++ Google drive in order to view it.)
- [UP Algo++ Pair and Tuple Lecture Slides](https://docs.google.com/presentation/d/1b1v8-ZOV59bWb5JiuyHhRG5QGKAhGA3eYALBvQIJCtA/edit#slide=id.g164c8dcc09a_1_48)