# Part 4: Linked Lists

In this section, we'll learn about **linked lists**, which are fundamental data structures in computer science. A linked list is a sequence of nodes where each node contains data and a reference (pointer) to the next node (and possibly the previous one). We'll use the C++ Standard Template Library (STL) implementations of linked lists to avoid manual pointer manipulation and make the topic easier to understand.

<br>

## What Is a Linked List?

Before we begin, let's understand what a linked list is:

- **Singly Linked List:** Each node contains data and a pointer to the next node in the sequence.
- **Doubly Linked List:** Each node contains data, a pointer to the next node, and a pointer to the previous node.

In the C++ Standard Template Library (STL):

- **`forward_list`:** Implements a singly linked list.
- **`list`:** Implements a doubly linked list.

Using these STL containers allows us to work with linked lists without worrying about manual memory management or pointers.

<br>

## What Is an Iterator?

Before working with linked lists, it's important to understand **iterators**.

An **iterator** is an object that points to an element in a container (like an array or list). It works like a pointer, allowing you to move through the elements of a container. You can think of it as a bookmark that keeps track of where you are.

- **Why Use Iterators?** They let you navigate through containers, access elements, and perform operations like insertion and deletion at specific positions.
- **Types of Iterators:**
  - **Forward Iterator:** Can move forward through the container.
  - **Bidirectional Iterator:** Can move both forward and backward.
  - **Random Access Iterator:** Can jump to any position (like an array index).

In our context:

- **`forward_list`:** Uses forward iterators (you can only move forward).
- **`list`:** Uses bidirectional iterators (you can move forward and backward).

---

## Singly Linked Lists with `forward_list`

The `forward_list` is an STL container that implements a singly linked list. It allows efficient insertion and deletion at the front, but you can't directly access elements by their index (like you can with an array).

### Basic Operations with `forward_list`

#### Including the Header File

To use `forward_list`, you need to include its header:

```cpp
#include <forward_list>
```

#### Creating a `forward_list`

```cpp
forward_list<int> flist; // Creates an empty singly linked list of integers
```

#### Inserting Elements

- **Insert at the Front:**

  ```cpp
  flist.push_front(10); // List now: 10
  flist.push_front(20); // List now: 20 -> 10
  ```

- **Insert After a Specific Position:**

  To insert after a specific position, you need an iterator pointing to the element **before** where you want to insert. For example:

  ```cpp
  auto it = flist.before_begin(); // Points to before the first element
  flist.insert_after(it, 30);     // Inserts 30 after 'it'
  // List now: 30 -> 20 -> 10
  ```

  **Explanation:**

  - **`before_begin()`** returns an iterator to the position **before** the first element.
  - **`insert_after(it, value)`** inserts `value` after the position `it` points to.

#### Inserting at the End

Since `forward_list` doesn't have a `push_back()` function, you need to traverse to the end of the list to insert an element there. Here's how you can do it:

```cpp
// Function to insert at the end
void insertAtEnd(forward_list<int>& flist, int value) {
    auto it = flist.before_begin(); // Start before the first element
    while (next(it) != flist.end()) {
        ++it;
    }
    flist.insert_after(it, value);
}

// Usage
insertAtEnd(flist, 40); // Inserts 40 at the end
// List now: 30 -> 20 -> 10 -> 40
```

**Explanation:**

- We start with an iterator `it` before the first element.
- We advance `it` until `next(it)` equals `flist.end()`, meaning `it` is pointing to the last element.
- We then insert after `it`.

#### Inserting in the Middle

To insert at a specific position (e.g., in the middle), you need to:

1. Traverse to the position **before** where you want to insert.
2. Use `insert_after()` to insert the new element.

```cpp
// Function to insert after N elements
void insertAfterN(forward_list<int>& flist, int position, int value) {
    auto it = flist.before_begin(); // Start before the first element
    for (int i = 0; i < position; ++i) {
        if (it == flist.end()) {
            break; // Position is beyond the list length
        }
        ++it;
    }
    flist.insert_after(it, value);
}

// Usage
insertAfterN(flist, 2, 25); // Inserts 25 after the second element
// Now the list is: 30 -> 20 -> 25 -> 10 -> 40
```

**Explanation:**

- We move the iterator `it` forward `position` times.
- Then we insert after `it`.

#### Deleting Elements

- **Delete After a Specific Position:**

  ```cpp
  auto it = flist.before_begin(); // Points to before the first element
  flist.erase_after(it);          // Deletes the element after 'it'
  // Now the list is: 20 -> 25 -> 10 -> 40
  ```

  **Explanation:**

  - **`erase_after(it)`** removes the element immediately after the iterator `it`.

- **Remove Specific Value:**

  ```cpp
  flist.remove(25); // Removes all elements equal to 25
  // Now the list is: 20 -> 10 -> 40
  ```

#### Traversing the List

```cpp
for (int value : flist) {
    cout << value << " ";
}
// Output: 20 10 40
```

### Example: Using `forward_list`

Let's create a singly linked list and perform various operations.

```cpp
#include <iostream>
#include <forward_list>
using namespace std;

// Function to insert at the end
void insertAtEnd(forward_list<int>& flist, int value) {
    auto it = flist.before_begin();
    while (next(it) != flist.end()) {
        ++it;
    }
    flist.insert_after(it, value);
}

// Function to insert after N elements
void insertAfterN(forward_list<int>& flist, int position, int value) {
    auto it = flist.before_begin();
    for (int i = 0; i < position; ++i) {
        if (it == flist.end()) {
            break; // Position is beyond the list length
        }
        ++it;
    }
    flist.insert_after(it, value);
}

int main() {
    forward_list<int> flist;

    // Inserting elements at the front
    flist.push_front(10); // List: 10
    flist.push_front(20); // List: 20 -> 10
    flist.push_front(30); // List: 30 -> 20 -> 10

    // Inserting at the end
    insertAtEnd(flist, 40); // Now: 30 -> 20 -> 10 -> 40

    // Inserting in the middle
    insertAfterN(flist, 2, 25); // Now: 30 -> 20 -> 25 -> 10 -> 40

    // Deleting the element after the first element (which is 20)
    auto it = flist.begin(); // Points to 30
    flist.erase_after(it);   // Deletes 20
    // Now: 30 -> 25 -> 10 -> 40

    // Traversing the list
    cout << "Singly Linked List elements: ";
    for (int value : flist) {
        cout << value << " ";
    }
    // Output: Singly Linked List elements: 30 25 10 40

    return 0;
}
```

**Explanation:**

- We start by inserting elements at the front using `push_front()`.
- We insert at the end using our custom `insertAtEnd()` function.
- We insert in the middle using `insertAfterN()`.
- We delete an element after a specific position using `erase_after()`.
- Finally, we traverse and print the list.

### Time Complexities for `forward_list`

| Operation                   | Time Complexity | Explanation                          |
|-----------------------------|-----------------|--------------------------------------|
| **Access by Index**         | O(n)            | Must traverse from the beginning     |
| **Insertion at Beginning**  | O(1)            | Directly insert at the front         |
| **Insertion After Element** | O(1)            | Insert after a known position        |
| **Insertion at End**        | O(n)            | Must traverse to the end             |
| **Deletion After Element**  | O(1)            | Delete after a known position        |
| **Deletion by Value**       | O(n)            | Must traverse to find the value      |
| **Search**                  | O(n)            | Must traverse to find the element    |

<br>

### Assignment

**Task:** Write a C++ program that:

1. Creates an empty singly linked list using `forward_list`.
2. Inserts five integers entered by the user at the **end** of the list.
3. Inserts an element in the middle of the list.
4. Traverses the list and prints the elements.

**Example Input:**

```
Enter 5 integers:
10 20 30 40 50
Enter the position to insert a new element (0-based index):
2
Enter the new element:
25
```

**Example Output:**

```
Elements in the list after insertion: 10 20 25 30 40 50
```

**Hints:**

- Use the `insertAtEnd()` function to insert at the end.
- Use the `insertAfterN()` function to insert at the specified position.

<br>

## Doubly Linked Lists with `list`

The `list` container in the STL implements a doubly linked list. It allows efficient insertion and deletion at both the front and back, as well as at any position in the list.

### Basic Operations with `list`

#### Including the Header File

```cpp
#include <list>
```

#### Creating a `list`

```cpp
list<int> dlist; // Creates an empty doubly linked list of integers
```

#### Inserting Elements

- **Insert at the Front:**

  ```cpp
  dlist.push_front(10); // List now: 10
  dlist.push_front(20); // List now: 20 <-> 10
  ```

- **Insert at the Back:**

  ```cpp
  dlist.push_back(30); // List now: 20 <-> 10 <-> 30
  ```

- **Insert at a Specific Position (Middle):**

  ```cpp
  auto it = dlist.begin(); // Points to the first element (20)
  advance(it, 1);          // Move iterator to the second position (10)
  dlist.insert(it, 25);    // Inserts 25 before the element at 'it'
  // List now: 20 <-> 25 <-> 10 <-> 30
  ```

  **Explanation:**

  - **`advance(it, n);`** moves the iterator `it` forward by `n` positions.
  - **`insert(it, value);`** inserts `value` before the position pointed to by `it`.

#### Deleting Elements

- **Delete Specific Element by Iterator:**

  ```cpp
  auto it = dlist.begin(); // Points to the first element (20)
  advance(it, 2);          // Move iterator to the third element (10)
  dlist.erase(it);         // Deletes the element at 'it' (10)
  // List now: 20 <-> 25 <-> 30
  ```

- **Remove Specific Value:**

  ```cpp
  dlist.remove(25); // Removes all elements equal to 25
  // List now: 20 <-> 30
  ```

#### Traversing the List Forward

```cpp
for (int value : dlist) {
    cout << value << " ";
}
// Output: 20 30
```

#### Traversing the List Backward

```cpp
for (auto it = dlist.rbegin(); it != dlist.rend(); ++it) {
    cout << *it << " ";
}
// Output: 30 20
```

### Example: Inserting in the Middle

Let's see how to insert an element in the middle of a doubly linked list.

```cpp
#include <iostream>
#include <list>
using namespace std;

int main() {
    list<int> dlist = {10, 20, 30, 40, 50};

    // Move iterator to the third position
    auto it = dlist.begin();
    advance(it, 2); // Points to 30

    // Insert 25 before 30
    dlist.insert(it, 25); // Now: 10 <-> 20 <-> 25 <-> 30 <-> 40 <-> 50

    // Traversing forward
    cout << "Doubly Linked List elements after insertion (forward): ";
    for (int value : dlist) {
        cout << value << " ";
    }
    // Output: 10 20 25 30 40 50

    return 0;
}
```

### Time Complexities for `list`

| Operation                   | Time Complexity         | Explanation                                 |
|-----------------------------|-------------------------|---------------------------------------------|
| **Access by Index**         | O(n)                    | Must traverse from the beginning            |
| **Insertion at Beginning**  | O(1)                    | Directly insert at the front                |
| **Insertion at End**        | O(1)                    | Directly insert at the back                 |
| **Insertion in Middle**     | O(1) (after traversal)  | Insert at a known position using an iterator |
| **Deletion by Iterator**    | O(1)                    | Delete at a known position                  |
| **Deletion by Value**       | O(n)                    | Must traverse to find the value             |
| **Search**                  | O(n)                    | Must traverse to find the element           |

---

### Assignment

**Task:** Write a C++ program that:

1. Creates a doubly linked list using `list` and initializes it with integers.
2. Inserts a new element in the middle of the list.
3. Traverses the list forward and prints the elements.
4. Deletes an element from the middle of the list.
5. Traverses the list backward and prints the elements.

**Example Input:**

```
Enter initial elements (end with -1):
10 20 30 40 50 -1
Enter the position to insert a new element (0-based index):
2
Enter the new element:
25
Enter the position to delete an element (0-based index):
3
```

**Example Output:**

```
Elements in the list after insertion (forward): 10 20 25 30 40 50
Elements in the list after deletion (backward): 50 40 25 20 10
```

**Hints:**

- Use `advance()` to move the iterator to the desired position.
- Use `insert(it, value)` to insert at a specific position.
- Use `erase(it)` to delete the element at a specific position.
- For backward traversal, use reverse iterators.

<br>

## Benefits of Using STL Containers

- **Simplified Code:** No need to manually manage memory or pointers.
- **Safety:** Reduces the risk of memory leaks and dangling pointers.
- **Efficiency:** STL containers are well-optimized.
- **Functionality:** Provides a rich set of member functions for common operations.

## When to Implement Custom Linked Lists

While the STL provides robust implementations, there are times when you might need to implement your own linked list:

- **Learning Purposes:** To understand how linked lists work internally.
- **Custom Behavior:** When you need specific functionality not provided by STL.
- **Memory Management:** For fine-tuned control over memory allocation.

For most applications, especially in competitive programming and general development, using STL containers like `forward_list` and `list` is recommended for simplicity and reliability.

<br>

## Summary

- **Iterators:** Objects that point to elements in a container. Essential for traversing and manipulating elements.
  - **In `forward_list`:** Use iterators for insertion and deletion after specific positions.
  - **In `list`:** Use iterators to insert or delete at specific positions, both forward and backward.
- **Linked Lists:** Sequences of nodes where each node points to the next (and possibly previous) node.
  - **`forward_list`:** An STL container implementing a singly linked list.
    - Efficient insertion and deletion at the front.
  - **`list`:** An STL container implementing a doubly linked list.
    - Supports bidirectional traversal.
    - Efficient insertion and deletion at both ends and in the middle (using iterators).
- **Inserting at Specific Positions:**
  - **In `forward_list`:** Use `insert_after()` and traverse to the position before where you want to insert.
  - **In `list`:** Use `insert()` with an iterator pointing to the exact position.
- **Deleting at Specific Positions:**
  - **In `forward_list`:** Use `erase_after()` to remove the element after a given position.
  - **In `list`:** Use `erase()` with an iterator pointing to the exact position.

By understanding iterators and how to use them with `forward_list` and `list`, you can effectively manipulate linked lists in C++. The STL provides powerful tools that simplify working with these data structures, making them accessible even to beginners.

Feel free to experiment with the provided code examples and assignments to deepen your understanding. Happy coding!

<br>

## Knowledge check
These questions provide a chance to think about the important topics covered in this lesson. If you're unsure of an answer, revisit the material. Remember, you're not expected to memorize or fully master this information right now.
- a

<br>

## Additional Resources
This section offers useful links to relevant content. It's optional and meant to be extra material for further reading.(Note: Some resources might require you you to have access to the Algo++ Google drive in order to view it.)
- [UP Algo++ Linked List Lecture Slides](https://docs.google.com/presentation/d/1qe7LcNVJLQOJ4nPvTNoTrKJ4MUuo2zb6-tNcCucjNT8/edit#slide=id.g164c8dcc09a_1_48)