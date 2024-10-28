# Part 2: Dynamic Linear Data Structures

In this part, we will explore dynamic linear data structures in C++, which are essential for efficient data manipulation and storage. We will cover vectors, strings, stacks, queues, and deques.

## Vectors

A **vector** is a dynamic array provided by the C++ Standard Template Library (STL). Unlike regular arrays, vectors can resize themselves automatically when an element is inserted or deleted, managing their own memory.

### Declaring a Vector

To use vectors, include the `<vector>` header file.

```cpp
#include <vector>
#include <iostream>

using namespace std;

int main() {
    vector<int> v; // An empty vector of integers
    return 0;
}
```

**Example: Using Vectors**

Let's see how to add elements to a vector, access them, and iterate over the vector.

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    vector<int> v;

    // Adding elements to the vector
    v.push_back(5);
    v.push_back(10);
    v.push_back(15);

    // Accessing elements using the index operator []
    cout << "First element: " << v[0] << endl; // Output: First element: 5

    // Iterating over elements using a for loop
    cout << "Vector elements: ";
    for (int i = 0; i < v.size(); ++i) {
        cout << v[i] << " ";
    }
    // Output: Vector elements: 5 10 15

    // Alternatively, using a range-based for loop
    cout << "\nVector elements using range-based for loop: ";
    for (int value : v) {
        cout << value << " ";
    }
    // Output: Vector elements using range-based for loop: 5 10 15

    return 0;
}
```

### Removing Elements from a Vector

Vectors provide several methods to remove elements:

- **`pop_back()`**: Removes the last element.
- **`erase()`**: Removes elements at a specified position or range.
- **`clear()`**: Removes all elements from the vector.

**Example: Removing Elements**

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    vector<int> v = {5, 10, 15, 20, 25};

    // Remove the last element
    v.pop_back(); // Vector now contains: 5, 10, 15, 20

    // Remove the element at index 1 (second element)
    v.erase(v.begin() + 1); // Vector now contains: 5, 15, 20

    // Remove elements from index 0 to index 1 (not including index 2)
    v.erase(v.begin(), v.begin() + 2); // Vector now contains: 20

    // Clear all elements
    v.clear(); // Vector is now empty

    cout << "Size of vector after clear: " << v.size() << endl; // Output: 0

    return 0;
}
```

> **Note:** When removing elements from a vector, be cautious with indices and iterators, as the size and order of the vector change.

### Time Complexities for Vectors

Understanding the time complexities of various operations helps in writing efficient code.

| Operation                           | Time Complexity      | Explanation                                       |
|-------------------------------------|----------------------|---------------------------------------------------|
| **Access**                          | O(1)                 | Direct access to element via index                |
| **Insertion/Deletion at End**       | Amortized O(1)       | Efficient, but may occasionally require resizing  |
| **Insertion/Deletion at Beginning/Middle** | O(n)        | Requires shifting elements                        |
| **Search (Unsorted)**               | O(n)                 | Linear search through the vector                  |
| **Search (Sorted)**                 | O(log n)             | Binary search, requires sorted vector             |

> **Note:** *Amortized O(1)* means that while a single insertion at the end might occasionally take longer (due to resizing), the average time per insertion is constant when inserting many elements.

<br>

## Strings as Vectors

In C++, the `string` class functions similarly to a vector of characters. It allows dynamic resizing and provides various methods for string manipulation.

**Example: Manipulating Strings**

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s = "Hello";

    // Appending to the string
    s += " World"; // Now s is "Hello World"

    // Accessing characters using the index operator []
    cout << "Character at index 6: " << s[6] << endl; // Output: Character at index 6: W

    // Iterating over characters using a range-based for loop
    cout << "Characters in the string: ";
    for (char c : s) {
        cout << c << " ";
    }
    // Output: Characters in the string: H e l l o   W o r l d

    return 0;
}
```

### Time Complexities for Strings

| Operation                        | Time Complexity | Explanation                                       |
|----------------------------------|-----------------|---------------------------------------------------|
| **Access**                       | O(1)            | Direct access to character via index              |
| **Insertion/Deletion at End**    | O(1)            | Appending/removing at the end                     |
| **Insertion/Deletion at Beginning/Middle** | O(n) | Requires shifting characters                      |
| **Search**                       | O(n)            | Linear search through the string                  |

<br>

### Assignment

---

**Task:** Write a C++ program that does the following:

1. Creates an empty vector of strings.
2. Adds the names of three of your favorite fruits to the vector.
3. Prints out the number of fruits in the vector.
4. Uses a loop to print each fruit in the vector.

**Example Output:**

```
Number of fruits: 3
Fruits:
Apple
Banana
Cherry
```

**Hint:** Use `push_back` to add elements to the vector and `size()` to get the number of elements.

---

<br>

## Stacks, Queues, and Deques

These are specialized data structures that follow specific rules for insertion and deletion, making them suitable for particular kinds of tasks.

### Stack

A **stack** is a Last-In-First-Out (LIFO) data structure. Think of it like a stack of books; you can only take the top book off the stack or add a new book on top.

**Example: Using a Stack**

```cpp
#include <iostream>
#include <stack>
using namespace std;

int main() {
    stack<int> s;

    // Pushing elements onto the stack
    s.push(1); // Stack now contains: [1]
    s.push(2); // Stack now contains: [1, 2]
    s.push(3); // Stack now contains: [1, 2, 3]

    // Popping elements from the stack
    cout << "Stack elements: ";
    while (!s.empty()) {
        cout << s.top() << " "; // Access the top element
        s.pop();                // Remove the top element
    }
    // Output: Stack elements: 3 2 1

    return 0;
}
```

<br>

### Assignment

---

**Task:** Write a C++ program that:

1. Creates a stack of characters.
2. Reads a word from the user input.
3. Pushes each character of the word onto the stack.
4. Pops characters from the stack and prints them to display the word in reverse.

**Example Input:**

```
Enter a word: HELLO
```

**Example Output:**

```
Reversed word: OLLEH
```

**Hint:** Use `cin >> word` to read the input and a loop to push each character onto the stack.

---

<br>

### Queue

A **queue** is a First-In-First-Out (FIFO) data structure. It's like a line of people; the first person to get in line is the first person to be served.

**Example: Using a Queue**

```cpp
#include <iostream>
#include <queue>
using namespace std;

int main() {
    queue<int> q;

    // Enqueuing elements
    q.push(1); // Queue now contains: [1]
    q.push(2); // Queue now contains: [1, 2]
    q.push(3); // Queue now contains: [1, 2, 3]

    // Dequeuing elements
    cout << "Queue elements: ";
    while (!q.empty()) {
        cout << q.front() << " "; // Access the front element
        q.pop();                  // Remove the front element
    }
    // Output: Queue elements: 1 2 3

    return 0;
}
```

<br>

### Assignment

---

**Task:** Write a C++ program that:

1. Creates a queue of strings.
2. Simulates a ticketing system where users enter their names to get a ticket.
3. Reads three names from user input and adds them to the queue.
4. Processes the queue by greeting each person in order.

**Example Input:**

```
Enter name 1: Alice
Enter name 2: Bob
Enter name 3: Charlie
```

**Example Output:**

```
Serving: Alice
Serving: Bob
Serving: Charlie
```

**Hint:** Use `cin` to read the names and `push`, `front`, and `pop` to manage the queue.

---

<br>

### Deque

A **deque** (double-ended queue) allows insertion and deletion at both ends. It combines the features of both stacks and queues.

**Example: Using a Deque**

```cpp
#include <iostream>
#include <deque>
using namespace std;

int main() {
    deque<int> d;

    // Inserting elements at both ends
    d.push_back(1);  // Deque now contains: [1]
    d.push_front(2); // Deque now contains: [2, 1]
    d.push_back(3);  // Deque now contains: [2, 1, 3]

    // Accessing elements
    cout << "Front element: " << d.front() << endl; // Output: Front element: 2
    cout << "Back element: " << d.back() << endl;   // Output: Back element: 3

    // Iterating over elements
    cout << "Deque elements: ";
    for (int num : d) {
        cout << num << " ";
    }
    // Output: Deque elements: 2 1 3

    return 0;
}
```

### Removing Elements from a Deque

Deques allow you to remove elements from both ends:

- **`pop_front()`**: Removes the first element.
- **`pop_back()`**: Removes the last element.

**Example: Removing Elements**

```cpp
#include <iostream>
#include <deque>
using namespace std;

int main() {
    deque<int> d = {1, 2, 3, 4, 5};

    // Remove element from the front
    d.pop_front(); // Deque now contains: [2, 3, 4, 5]

    // Remove element from the back
    d.pop_back();  // Deque now contains: [2, 3, 4]

    // Displaying the deque
    cout << "Deque after popping from both ends: ";
    for (int num : d) {
        cout << num << " ";
    }
    // Output: Deque after popping from both ends: 2 3 4

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

> **Note:** Stacks and queues do not allow random access; you can only access the element at the top (stack) or front (queue). Deques allow random access via indexing, similar to vectors.

<br>

### Assignment

---

**Task:** Write a C++ program that:

1. Creates a deque of integers.
2. Adds numbers 1 to 5 to the deque, alternating between `push_front` and `push_back`.
3. Prints the contents of the deque.
4. Removes an element from both the front and back using `pop_front` and `pop_back`.
5. Prints the contents of the deque again.

**Example Output:**

```
Deque after adding elements: 5 2 3 4 1
Deque after removing from both ends: 2 3 4
```

**Hint:** Use `push_front`, `push_back`, `pop_front`, `pop_back`, and a loop to print the deque's contents.

---

## Knowledge check
These questions provide a chance to think about the important topics covered in this lesson. If you're unsure of an answer, revisit the material. Remember, you're not expected to memorize or fully master this information right now.
- [How do you use vectors in C++?](https://github.com/UP-Algorithm-Plus-Plus/CPP-Crash-Course-2425A/blob/main/Week_3/Part2.md#vectors)
- [What are the adavntages of vectors?](https://github.com/UP-Algorithm-Plus-Plus/CPP-Crash-Course-2425A/blob/main/Week_3/Part2.md#vectors)
- [What are stacks?](https://github.com/UP-Algorithm-Plus-Plus/CPP-Crash-Course-2425A/blob/main/Week_3/Part2.md#stack)
- [How do you input, access, and pop elements of a stack?](https://github.com/UP-Algorithm-Plus-Plus/CPP-Crash-Course-2425A/blob/main/Week_3/Part2.md#stack)
- [What are queues?](https://github.com/UP-Algorithm-Plus-Plus/CPP-Crash-Course-2425A/blob/main/Week_3/Part2.md#queue)
- [How do you input, access, and pop elements of a queue?]()https://github.com/UP-Algorithm-Plus-Plus/CPP-Crash-Course-2425A/blob/main/Week_3/Part2.md#queue
- [What are deques?](https://github.com/UP-Algorithm-Plus-Plus/CPP-Crash-Course-2425A/blob/main/Week_3/Part2.md#deque)
- [How do you input, access, and pop elements of a deque?](https://github.com/UP-Algorithm-Plus-Plus/CPP-Crash-Course-2425A/blob/main/Week_3/Part2.md#deque)

## Additional Resources
This section offers useful links to relevant content. It's optional and meant to be extra material for further reading.(Note: Some resources might require you you to have access to the Algo++ Google drive in order to view it.)
- [UP Algo++ Dynamic Linear DS](https://docs.google.com/presentation/d/1XFdVQdtezbnQopp6LqhKQAuBA8KxUZk_5GU-bhR3b3E/edit#slide=id.g164c8dcc09a_1_48)