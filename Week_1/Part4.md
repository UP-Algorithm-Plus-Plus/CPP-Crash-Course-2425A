# C++ Crash Course Week 1 Part 4 ~ C++ Basics

## Arrays

Arrays are fundamental data structures in C++ that allow you to store multiple values of the same data type in a single variable. Think of an array as a collection of elements, like a row of lockers, where each locker holds an item of the same kind.

**Key Points about Arrays**:

- **Fixed Size**: When you declare an array, you must specify its size, which cannot be changed during runtime.
- **Homogeneous Elements**: All elements in an array must be of the same data type.
- **Indexed Access**: Elements are accessed using an index, starting from `0` up to `size - 1`.

### Declaring and Initializing Arrays

**Syntax**:

```cpp
dataType arrayName[arraySize] = {element1, element2, ..., elementN};
```

- `dataType`: The type of data the array will hold (e.g., `int`, `double`, `char`).
- `arrayName`: The name you give to the array.
- `arraySize`: The number of elements the array can hold.
- `{...}`: The list of initial values for the array elements.

**Example**:

```cpp
#include <iostream>

int main() {
    int numbers[5] = {1, 2, 3, 4, 5}; // Declare and initialize an array of 5 integers

    // Access and print each element
    std::cout << "First element: " << numbers[0] << std::endl;
    std::cout << "Second element: " << numbers[1] << std::endl;
    std::cout << "Third element: " << numbers[2] << std::endl;
    std::cout << "Fourth element: " << numbers[3] << std::endl;
    std::cout << "Fifth element: " << numbers[4] << std::endl;

    return 0;
}
```

**Explanation**:

- **Declaration**: `int numbers[5];` declares an array named `numbers` that can hold 5 integers.
- **Initialization**: `{1, 2, 3, 4, 5}` initializes the array with values.
- **Accessing Elements**: Use `numbers[index]` to access elements, where `index` ranges from `0` to `4`.

**Important Notes**:

- **Zero-Based Indexing**: Arrays in C++ start at index `0`.
- **Out-of-Bounds Access**: Accessing indices outside the array bounds leads to undefined behavior.
- **Static Arrays**: The size of a static array must be known at compile time and cannot be changed during execution.

### Iterating Over Arrays

You can use loops to traverse arrays efficiently.

**Example Using a For Loop**:

```cpp
#include <iostream>

int main() {
    int numbers[5] = {1, 2, 3, 4, 5};

    // Iterate over the array using a for loop
    for (int i = 0; i < 5; i++) {
        std::cout << "Element at index " << i << ": " << numbers[i] << std::endl;
    }

    return 0;
}
```

**Explanation**:

- The loop variable `i` starts at `0` and increments by `1` until it reaches `5`.
- `numbers[i]` accesses each element in the array.

---

### Assignment

1. **Array Declaration**:

   - Write a program that declares arrays for the following data types: `double`, `int`, `char`, and `std::string`.
   - Each array should have 3 elements.
   - **Example**:

     ```cpp
     #include <iostream>
     #include <string>

     int main() {
         double decimalNumbers[3] = {2.718, 3.1415, 1.414};
         int integers[3] = {10, 20, 30};
         char letters[3] = {'X', 'Y', 'Z'};
         std::string words[3] = {"Hello", "C++", "World"};

         // Your code here

         return 0;
     }
     ```

2. **Accessing and Printing Elements**:

   - Using the same program, perform the following:
     - Print the **first element** of the `double` array.
     - Print the **second element** of the `int` array.
     - Print the **third element** of the `char` array.
     - Print **all elements** of the `std::string` array.
   - **Hint**: Use `std::cout` to print the values.

---

## Conditional Statements

Conditional statements allow your program to make decisions based on certain conditions. They control the flow of execution and enable your code to respond differently under varying circumstances.

### The `if`, `else if`, and `else` Statements

- **`if` Statement**: Executes a block of code if a specified condition is `true`.
- **`else if` Statement**: Checks an additional condition if the previous `if` or `else if` condition was `false`.
- **`else` Statement**: Executes a block of code if none of the previous conditions were `true`.

**Syntax**:

```cpp
if (condition1) {
    // Code to execute if condition1 is true
} else if (condition2) {
    // Code to execute if condition1 is false and condition2 is true
} else {
    // Code to execute if neither condition1 nor condition2 is true
}
```

**Example**:

```cpp
#include <iostream>

int main() {
    int wallet = 20; // Initialize wallet

    if (wallet == 20) {
        std::cout << "Your wallet contains $20" << std::endl;
    } else if (wallet < 20 && wallet != 0) {
        std::cout << "Your wallet contains less than $20 and is not empty." << std::endl;
    } else {
        std::cout << "Your wallet contains more than $20" << std::endl;
    }

    return 0;
}
```

**Explanation**:

- **First Condition**: `if (wallet == 20)`
  - Checks if `wallet` is equal to `20`
- **Second Condition**: `else if (wallet < 20)`
  - Checks if `wallet` is less than `20`.
- **Else Block**:
  - Executes if none of the previous conditions are met.
  - In this case, it means wallet has a value of more than `20`

### Logical Operators
 These are used in if/else if statements to make code run under more complicated conditions. 
- **AND (`&&`)**: True if both operands are true.
- **OR (`||`)**: True if at least one operand is true.
- **NOT (`!`)**: Inverts the truth value of the operand.

**Example with Logical Operators**:

```cpp
#include <iostream>

int main() {
    bool isStudent = true;
    bool hasID = false;

    if (isStudent && hasID) {
        std::cout << "You get a student discount." << std::endl;
    } else if (isStudent || hasID) {
        std::cout << "Partial discount available." << std::endl;
    } else {
        std::cout << "No discount available." << std::endl;
    }

    return 0;
}
```

---

### Assignment

1. **Basic Calculator**:

   - Create a program that functions as a basic calculator.
   - **Requirements**:
     - Prompt the user to input two integers, `A` and `B`.
     - Ask the user to choose an operation: `+`, `-`, `*`, or `/`.
     - Perform the chosen operation and display the result.
     - If the operation is division `/`, also calculate and display the remainder (use the modulo operator `%`).
     - Handle division by zero appropriately by displaying an error message.

   - **Example Interaction**:

     ```
     Enter first number (A): 15
     Enter second number (B): 4
     Choose operation (+, -, *, /): /
     Result of 15 / 4 = 3
     Remainder: 3
     ```

   - **Hints**:
     - Use `std::cin` to get user input.
     - Use `if`, `else if`, and `else` statements to handle different operations.

2. **Quadrant Selection Problem**:

   - Solve the [Quadrant Selection](https://open.kattis.com/problems/quadrant) problem on Kattis.
   - **Submission**:
     - Write your solution in C++.
     - Submit your solution on Kattis to get instant feedback.

---

## Knowledge Check

These questions provide a chance to think about the important topics covered in this lesson. If you're unsure of an answer, revisit the material. Remember, you're not expected to memorize or fully master this information right now.

- [What is an array in C++, and how do you declare one?](https://github.com/UP-Algorithm-Plus-Plus/CPP-Crash-Course-2425A/blob/week_1/Week_1/Part4.md#arrays)
- [How do you access the third element of an array named `numbers`?](https://github.com/UP-Algorithm-Plus-Plus/CPP-Crash-Course-2425A/blob/week_1/Week_1/Part4.md#declaring-and-initializing-arrays)
- [Explain the difference between `if`, `else if`, and `else` statements.](https://github.com/UP-Algorithm-Plus-Plus/CPP-Crash-Course-2425A/blob/week_1/Week_1/Part4.md#conditional-statements)
- [How does the logical AND operator `&&` function in conditional statements? How about `||` and `!`?](https://github.com/UP-Algorithm-Plus-Plus/CPP-Crash-Course-2425A/blob/week_1/Week_1/Part4.md#logical-operators)
- [What will happen if you try to access an array element outside its defined range?](https://github.com/UP-Algorithm-Plus-Plus/CPP-Crash-Course-2425A/blob/week_1/Week_1/Part4.md#declaring-and-initializing-arrays)

---

## Additional Resources
This section offers useful links to relevant content. It's optional and meant to be extra material for further reading.(Note: Some resources might require you you to have access to the Algo++ Google drive in order to view it.)
- [UP Algo++ Static Linear Data Structures Lecture Slides](https://docs.google.com/presentation/d/1K3jiqlSqMxRToh926U01xdX73ib2k4xXWa2EpYysHFU/edit#slide=id.g164c8dcc09a_1_48)
- [UP Algo++ Control Flow and Loops Lecture Slides](https://docs.google.com/presentation/d/19vQAPQ4tASUD5gR1OjVtzKT7Ygc0HI8VTVcn_03uAaE/edit#slide=id.g164c8dcc09a_1_48)

---

## Summary

In this lesson, we've delved into arrays and conditional statements, two foundational concepts in C++ programming. Arrays allow you to store and manage collections of data efficiently, while conditional statements enable your programs to make decisions based on dynamic conditions. By understanding and practicing these concepts, you're building a strong base for more complex programming tasks ahead. Remember to experiment with code examples and challenge yourself with the assignments to solidify your learning.

---






