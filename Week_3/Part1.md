# Part 1: Static Arrays Extended

## Recall

An **array** is a collection of elements of the same type stored in contiguous memory locations. Arrays are fundamental in C++ and are widely used in competitive programming due to their simplicity and efficiency.

### One-Dimensional Arrays

A one-dimensional array represents a sequence or list of elements.

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

### Two-Dimensional Arrays

Two-dimensional arrays represent matrices or grids, which are common in problems involving pathfinding, dynamic programming, and graph traversal. While arrays can be extended to more than two dimensions, we will focus on two-dimensional arrays for now.

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

    /*
    Alternatively, you can initialize the two-dimensional array at the time of declaration like this:
    int grid[3][4] = {{0, 1, 2, 3}, {1, 2, 3, 4}, {2, 3, 4, 5}};
    This is only allowed during the declaration, not after the array has been created.
    */

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
<br>

## Time Complexities for Array Operations

| Operation                       | Time Complexity | Explanation                                   |
|---------------------------------|-----------------|-----------------------------------------------|
| **Access**                      | O(1)            | Direct access via index                       |
| **Insertion at End**            | O(1)            | Only if space is available                    |
| **Insertion at Beginning/Middle** | O(n)         | Requires shifting elements                    |
| **Deletion at End**             | O(1)            | Removes the last element without shifting     |
| **Deletion at Beginning/Middle** | O(n)         | Requires shifting elements                    |
| **Search (Unsorted)**           | O(n)            | Linear search                                 |
| **Search (Sorted)**             | O(log n)        | Binary search (only if the array is sorted)   |

<br>

## Assignment

1. Declare and initialize a two-dimensional array in which each element contains information about a student. Each student record should include 3 elements: the student’s name, year, and degree program. Populate the array with details of 5 students (fictional or real). Then, print the details of each student in this format:

```
Student 1
Name: [Name]
Year: [Year]
Degree Program: [Program]

Student 2
Name: [Name]
Year: [Year]
Degree Program: [Program]

...

Student N
Name: [Name]
Year: [Year]
Degree Program: [Program]
```


## Knowledge check
These questions provide a chance to think about the important topics covered in this lesson. If you're unsure of an answer, revisit the material. Remember, you're not expected to memorize or fully master this information right now.
- [How do you declare and initialize a two dimensional array?](https://github.com/UP-Algorithm-Plus-Plus/CPP-Crash-Course-2425A/blob/main/Week_3/Part1.md#two-dimensional-arrays)
- [How do you input and output data to and from a two dimensional array?](https://github.com/UP-Algorithm-Plus-Plus/CPP-Crash-Course-2425A/blob/main/Week_3/Part1.md#two-dimensional-arrays)

## Additional Resources
This section offers useful links to relevant content. It's optional and meant to be extra material for further reading.(Note: Some resources might require you you to have access to the Algo++ Google drive in order to view it.)
- [UP Algo++ Static Linear DS Lecture Slides](https://docs.google.com/presentation/d/1K3jiqlSqMxRToh926U01xdX73ib2k4xXWa2EpYysHFU/edit#slide=id.g164c8dcc09a_1_48)