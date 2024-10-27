# Part 4: Linked Lists

In this part, we will explore **linked lists**, which are fundamental data structures in computer science. Linked lists are sequences of nodes where each node contains data and a pointer to the next node (and possibly the previous node). We will cover both **singly linked lists** and **doubly linked lists**.

## Singly Linked Lists

A **singly linked list** is a linear data structure where each element (node) points to the next node in the sequence. The last node points to `nullptr`, indicating the end of the list.

### Structure of a Singly Linked List Node

In C++, we can define a node for a singly linked list using a `struct` or `class`. Each node contains the data and a pointer to the next node.

```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;       // Data stored in the node
    Node* next;     // Pointer to the next node

    // Constructor to initialize the node
    Node(int val) {
        data = val;
        next = nullptr;
    }
};
```

### Creating and Traversing a Singly Linked List

Let's create a simple singly linked list with three nodes and traverse it.

```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* next;

    // Constructor
    Node(int val) : data(val), next(nullptr) {}
};

int main() {
    // Creating individual nodes
    Node* head = new Node(10);
    Node* second = new Node(20);
    Node* third = new Node(30);

    // Linking the nodes together
    head->next = second;
    second->next = third;

    // Traversing the list
    Node* current = head;
    cout << "Singly Linked List elements: ";
    while (current != nullptr) {
        cout << current->data << " ";
        current = current->next;
    }
    // Output: Singly Linked List elements: 10 20 30

    // Freeing allocated memory
    current = head;
    while (current != nullptr) {
        Node* temp = current;
        current = current->next;
        delete temp;
    }

    return 0;
}
```

**Explanation:**

- **Node Creation:** We create three nodes with values 10, 20, and 30.
- **Linking Nodes:** We set the `next` pointer of each node to link them together.
- **Traversal:** We use a `while` loop to traverse the list and print each node's data.
- **Memory Management:** We delete each node to free up memory.

### Inserting a Node at the Beginning

To insert a new node at the beginning of the list, you adjust the `next` pointer of the new node to point to the current head and update the head to be the new node.

```cpp
void insertAtBeginning(Node*& head, int val) {
    Node* newNode = new Node(val);
    newNode->next = head;
    head = newNode;
}
```

**Usage:**

```cpp
int main() {
    Node* head = nullptr; // Start with an empty list

    insertAtBeginning(head, 30);
    insertAtBeginning(head, 20);
    insertAtBeginning(head, 10);

    // Now the list is: 10 -> 20 -> 30

    // Traversal code as before...
}
```

### Time Complexities for Singly Linked Lists

| Operation                   | Time Complexity | Explanation                                       |
|-----------------------------|-----------------|---------------------------------------------------|
| **Access by Index**         | O(n)            | Must traverse from the head                       |
| **Insertion at Beginning**  | O(1)            | Adjust pointers to insert node at the start       |
| **Insertion at End**        | O(n)            | Must traverse to the end to insert                |
| **Deletion of a Node**      | O(n)            | Need to find the node and adjust pointers         |
| **Search**                  | O(n)            | Must traverse nodes to find the element           |

---

### Assignment

---

**Task:** Write a C++ program that:

1. Creates an empty singly linked list.
2. Inserts five integers entered by the user at the **end** of the list.
3. Traverses the list and prints the elements.

**Example Input:**

```
Enter 5 integers:
10 20 30 40 50
```

**Example Output:**

```
Elements in the list: 10 20 30 40 50
```

**Hint:**

- Use a loop to read integers from the user.
- For insertion at the end, you need to traverse to the last node each time or maintain a tail pointer.

---

<br>

## Doubly Linked Lists

A **doubly linked list** is a linked list where each node contains pointers to both the **next** and **previous** nodes. This allows traversal in both forward and backward directions.

### Structure of a Doubly Linked List Node

```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;       // Data stored in the node
    Node* next;     // Pointer to the next node
    Node* prev;     // Pointer to the previous node

    // Constructor to initialize the node
    Node(int val) {
        data = val;
        next = nullptr;
        prev = nullptr;
    }
};
```

### Creating and Traversing a Doubly Linked List

Let's create a doubly linked list with three nodes and traverse it both forward and backward.

```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* next;
    Node* prev;

    // Constructor
    Node(int val) : data(val), next(nullptr), prev(nullptr) {}
};

int main() {
    // Creating nodes
    Node* head = new Node(10);
    Node* second = new Node(20);
    Node* third = new Node(30);

    // Linking nodes
    head->next = second;
    second->prev = head;

    second->next = third;
    third->prev = second;

    // Traversing forward
    Node* current = head;
    cout << "Doubly Linked List elements (forward): ";
    while (current != nullptr) {
        cout << current->data << " ";
        if (current->next == nullptr) break; // Stop at the last node
        current = current->next;
    }
    // Output: Doubly Linked List elements (forward): 10 20 30

    // Traversing backward
    cout << "\nDoubly Linked List elements (backward): ";
    while (current != nullptr) {
        cout << current->data << " ";
        current = current->prev;
    }
    // Output: Doubly Linked List elements (backward): 30 20 10

    // Freeing allocated memory
    current = head;
    while (current != nullptr) {
        Node* temp = current;
        current = current->next;
        delete temp;
    }

    return 0;
}
```

**Explanation:**

- **Node Creation and Linking:** We create nodes and link them using both `next` and `prev` pointers.
- **Forward Traversal:** Starting from `head`, we move to `next` nodes.
- **Backward Traversal:** Starting from the last node, we move to `prev` nodes.
- **Memory Management:** We delete each node to free up memory.

### Inserting a Node at the Beginning

```cpp
void insertAtBeginning(Node*& head, int val) {
    Node* newNode = new Node(val);
    newNode->next = head;
    if (head != nullptr)
        head->prev = newNode;
    head = newNode;
}
```

**Usage:**

```cpp
int main() {
    Node* head = nullptr; // Start with an empty list

    insertAtBeginning(head, 30);
    insertAtBeginning(head, 20);
    insertAtBeginning(head, 10);

    // Now the list is: 10 <-> 20 <-> 30

    // Traversal code as before...
}
```

### Time Complexities for Doubly Linked Lists

| Operation                   | Time Complexity | Explanation                                            |
|-----------------------------|-----------------|--------------------------------------------------------|
| **Access by Index**         | O(n)            | Must traverse from the head                            |
| **Insertion at Beginning**  | O(1)            | Adjust pointers to insert node at the start            |
| **Insertion at End**        | O(1) if tail is maintained, O(n) otherwise | With a tail pointer, we can insert in O(1) time |
| **Deletion of a Node**      | O(1)            | If the node is known; adjust pointers                  |
| **Search**                  | O(n)            | Must traverse nodes to find the element                |

---

### Assignment

---

**Task:** Write a C++ program that:

1. Creates an empty doubly linked list.
2. Inserts integers entered by the user at the **beginning** of the list.
3. After insertion, traverses the list forward and prints the elements.
4. Then traverses the list backward and prints the elements.

**Example Input:**

```
Enter numbers to insert at the beginning (-1 to stop):
5 10 15 20 -1
```

**Example Output:**

```
Elements in the list (forward): 20 15 10 5
Elements in the list (backward): 5 10 15 20
```

**Hint:**

- Use a loop to read integers until `-1` is entered.
- For insertion at the beginning, adjust both `next` and `prev` pointers.

---

By understanding linked lists, you gain insight into how dynamic data structures work and how to manage memory manually in C++. Linked lists are fundamental in computer science and are the basis for many advanced data structures.

---

# Singly Linked List Assignment Solution Example

Here's a sample code to help you get started with the singly linked list assignment.

```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* next;

    Node(int val) : data(val), next(nullptr) {}
};

void insertAtEnd(Node*& head, int val) {
    Node* newNode = new Node(val);
    if (head == nullptr) {
        head = newNode;
        return;
    }
    Node* current = head;
    while (current->next != nullptr) {
        current = current->next;
    }
    current->next = newNode;
}

void printList(Node* head) {
    cout << "Elements in the list: ";
    Node* current = head;
    while (current != nullptr) {
        cout << current->data << " ";
        current = current->next;
    }
    cout << endl;
}

int main() {
    Node* head = nullptr;
    int num;
    cout << "Enter 5 integers:" << endl;
    for (int i = 0; i < 5; ++i) {
        cin >> num;
        insertAtEnd(head, num);
    }

    printList(head);

    // Freeing allocated memory
    Node* current = head;
    while (current != nullptr) {
        Node* temp = current;
        current = current->next;
        delete temp;
    }

    return 0;
}
```

# Doubly Linked List Assignment Solution Example

Here's a sample code to help you with the doubly linked list assignment.

```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* next;
    Node* prev;

    Node(int val) : data(val), next(nullptr), prev(nullptr) {}
};

void insertAtBeginning(Node*& head, int val) {
    Node* newNode = new Node(val);
    newNode->next = head;
    if (head != nullptr)
        head->prev = newNode;
    head = newNode;
}

void printListForward(Node* head) {
    cout << "Elements in the list (forward): ";
    Node* current = head;
    Node* last = nullptr;
    while (current != nullptr) {
        cout << current->data << " ";
        if (current->next == nullptr)
            last = current;
        current = current->next;
    }
    cout << endl;

    // Printing backward
    cout << "Elements in the list (backward): ";
    current = last;
    while (current != nullptr) {
        cout << current->data << " ";
        current = current->prev;
    }
    cout << endl;
}

int main() {
    Node* head = nullptr;
    int num;
    cout << "Enter numbers to insert at the beginning (-1 to stop):" << endl;
    while (true) {
        cin >> num;
        if (num == -1)
            break;
        insertAtBeginning(head, num);
    }

    printListForward(head);

    // Freeing allocated memory
    Node* current = head;
    while (current != nullptr) {
        Node* temp = current;
        current = current->next;
        delete temp;
    }

    return 0;
}
```

## Knowledge check
These questions provide a chance to think about the important topics covered in this lesson. If you're unsure of an answer, revisit the material. Remember, you're not expected to memorize or fully master this information right now.
- [How do you declare and initialize a two dimensional array?](https://github.com/UP-Algorithm-Plus-Plus/CPP-Crash-Course-2425A/blob/main/Week_3/Part1.md#two-dimensional-arrays)
- [How do you input and output data to and from a two dimensional array?](https://github.com/UP-Algorithm-Plus-Plus/CPP-Crash-Course-2425A/blob/main/Week_3/Part1.md#two-dimensional-arrays)

## Additional Resources
This section offers useful links to relevant content. It's optional and meant to be extra material for further reading.(Note: Some resources might require you you to have access to the Algo++ Google drive in order to view it.)
- [UP Algo++ Static Linear DS Lecture Slides](https://docs.google.com/presentation/d/1K3jiqlSqMxRToh926U01xdX73ib2k4xXWa2EpYysHFU/edit#slide=id.g164c8dcc09a_1_48)