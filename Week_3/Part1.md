# Part 1: Static Arrays Extended

## Recall

An **array** is a collection of elements of the same type placed in contiguous memory locations. Arrays are fundamental in C++ and are widely used in competitive programming for their simplicity and efficiency.

### One-Dimensional Arrays

A one-dimensional array represents a list of elements.

```cpp
int arr[5]; // Declares an array of 5 integers
```

**Example: Initializing and Accessing a 1D Array**

```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[5];

    // Initializing the array
    for (int i = 0; i < 5; ++i) {
        arr[i] = i * 2;
    }

    // Accessing the array
    for (int i = 0; i < 5; ++i) {
        cout << arr[i] << " ";
    }
    // Output: 0 2 4 6 8

    return 0;
}
```
<br>

## Two-Dimensional Arrays

Two-dimensional arrays are used to represent matrices or grids, which are common in problems like pathfinding, dynamic programming, and graph traversal.

```cpp
int grid[3][4]; // Declares a 3x4 2D array
```

**Example: Working with a 2D Array**

```cpp
#include <iostream>
using namespace std;

int main() {
    int rows = 3, cols = 4;
    int grid[3][4];

    // Initializing the 2D array
    for (int i = 0; i < rows; ++i) {
        for (int j = 0; j < cols; ++j) {
            grid[i][j] = i + j;
        }
    }

    // Accessing the 2D array
    for (int i = 0; i < rows; ++i) {
        for (int j = 0; j < cols; ++j) {
            cout << grid[i][j] << " ";
        }
        cout << endl;
    }
    /* Output:
    0 1 2 3
    1 2 3 4
    2 3 4 5
    */

    return 0;
}
```

## Time Complexities for Arrays
| Operation               | Time Complexity | Explanation                              |
|-------------------------|-----------------|------------------------------------------|
| **Access**              | O(1)            | Direct access via index                  |
| **Insertion at End**    | O(1)            | If space is available                    |
| **Insertion at Beginning/Middle** | O(n) | Requires shifting elements               |
| **Deletion at End**     | O(1)            |                                          |
| **Deletion at Beginning/Middle** | O(n) | Requires shifting elements               |
| **Search (Unsorted)**   | O(n)            | Linear search                            |
| **Search (Sorted)**     | O(log n)        | Binary search (requires sorted array)    |
