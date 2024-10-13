# C++ Crash Course Week 1 Part 5 ~ C++ Basics

## Loops

Loops are fundamental constructs in programming that allow you to execute a block of code multiple times, which is essential for tasks that require repetition. In C++, loops help you automate repetitive tasks efficiently, without writing redundant code.

### For Loop

A **for loop** is typically used when the number of iterations is known ahead of time. It consists of three parts: initialization, condition, and increment/decrement. The loop runs as long as the condition is `true`.

**Syntax**:

```cpp
for (initialization; condition; increment) {
    // Code to execute in each iteration
}
```

**Example**:

```cpp
#include <iostream>

int main() {
    // This loop will iterate 5 times, from i = 0 to i = 4
    for (int i = 0; i < 5; i++) {
        std::cout << "Loop iteration: " << i << std::endl;
    }
    return 0;
}
```

**Explanation**:

- **Initialization**: `int i = 0;` sets the starting point.
- **Condition**: `i < 5;` the loop continues as long as `i` is less than `5`.
- **Increment**: `i++` increases the value of `i` by `1` after each iteration.
- **Loop Body**: `std::cout << "Loop iteration: " << i << std::endl;` executes in each iteration.

### While Loop

A **while loop** is used when the number of iterations is not known in advance. It keeps running as long as a specified condition is `true`. The condition is checked before the loop body executes.

**Syntax**:

```cpp
while (condition) {
    // Code to execute as long as condition is true
}
```

**Example**:

```cpp
#include <iostream>

int main() {
    int i = 0;
    // This loop will continue to execute until i >= 5
    while (i < 5) {
        std::cout << "While loop iteration: " << i << std::endl;
        i++; // Increment i to avoid infinite loop
    }
    return 0;
}
```

**Explanation**:

- **Initialization**: `int i = 0;` before the loop starts.
- **Condition**: `i < 5;` the loop runs while `i` is less than `5`.
- **Increment**: `i++;` inside the loop body to change `i` after each iteration.

### Do-While Loop

A **do-while loop** is similar to a while loop, but it guarantees that the loop body executes at least once because the condition is evaluated after the loop body.

**Syntax**:

```cpp
do {
    // Code to execute at least once
} while (condition);
```

**Example**:

```cpp
#include <iostream>

int main() {
    int i = 0;
    do {
        std::cout << "Do-While loop iteration: " << i << std::endl;
        i++;
    } while (i < 5);
    return 0;
}
```

**Explanation**:

- The loop body runs first, printing the message and incrementing `i`.
- After the loop body, the condition `i < 5` is checked.
- The loop continues if the condition is `true`.

---

<br>

### Assignment

1. **Print Numbers from 1 to 10 Using a `for` Loop**:

   - **Objective**: Write a program that prints numbers from `1` to `10`.
   - **Hint**: Start the loop variable at `1` and iterate while it's less than or equal to `10`.

2. **Print the First 10 Numbers in the Fibonacci Sequence**:

   - **Objective**: Create a program that prints the first 10 numbers of the Fibonacci sequence.
   - **Hint**: The Fibonacci sequence starts with `0` and `1`, and each subsequent number is the sum of the previous two.

3. **Print Numbers from `n` Down to 1 Using a `while` Loop**:

   - **Objective**: Write a program that takes a positive integer `n` as input and prints all numbers from `n` down to `1`.
   - **Hint**: Use a `while` loop and decrement the counter in each iteration.

---

<br>

## Functions

Functions are reusable blocks of code that perform specific tasks. They help you organize your code, reduce repetition, and make your programs more modular and easier to maintain.

### Declaring and Defining Functions

**Declaration (Prototype)**:

- Tells the compiler about the function name, return type, and parameters.
- Typically placed before the `main` function or in a header file.

**Definition**:

- Contains the actual body of the function.
- Can be combined with the declaration.

**Syntax**:

```cpp
return_type function_name(parameter_list) {
    // Function body
    // ...
    return value; // if return_type is not void
}
```

**Example**:

```cpp
#include <iostream>

// Function declaration and definition
int add(int a, int b) {
    return a + b;
}

int main() {
    int sum = add(5, 3);
    std::cout << "Sum is: " << sum << std::endl;
    return 0;
}
```

**Explanation**:

- **Function Name**: `add`
- **Parameters**: `int a`, `int b` (inputs to the function)
- **Return Type**: `int` (the function returns an integer)
- **Function Body**: `return a + b;` computes the sum.

### Passing Parameters and Returning Values

- **Parameters**:

  - **By Value**: Copies of the arguments are passed; changes inside the function don't affect the originals.
  - **By Reference**: References to the arguments are passed; changes inside the function affect the originals.

- **Return Values**:

  - A function can return a value using the `return` statement.
  - If a function does not return a value, its return type is `void`.

**Example of Passing by Value**:

```cpp
void increment(int num) {
    num++; // This change won't affect the original variable
}
```

**Example of Passing by Reference**:

```cpp
void increment(int &num) {
    num++; // This change will affect the original variable
}
```

**Void Function Example**:

```cpp
void greet() {
    std::cout << "Hello, World!" << std::endl;
}
```

---

<br>

### Assignment

1. **Function to Return the Larger of Two Numbers**:

   - **Objective**: Write a function that takes two numbers as input and returns the larger of the two.
   - **Hint**: Use an `if-else` statement to compare the numbers.

2. **Function to Calculate the Factorial of a Number**:

   - **Objective**: Create a function that calculates the factorial of a non-negative integer.
   - **Hint**: Factorial of `n` is `n * (n-1) * (n-2) * ... * 1`. The factorial of `0` is `1`.

3. **Function to Return the Greatest Common Divisor (GCD)**:

   - **Objective**: Write a program that asks for two numbers and uses a function to return their greatest common divisor (GCD).
   - **Hint**: Use the Euclidean algorithm for finding GCD.

---

<br>

## Knowledge Check

These questions provide a chance to reflect on the important topics covered in this lesson. If you're unsure of an answer, revisit the material.
- [What are the three main types of loops in C++, and when would you use each?]()
- [How does passing parameters by value differ from passing by reference in functions?]()
- [Explain the purpose of the `return` statement in a function.]()
- [What is the difference between a function declaration and a function definition?]()
- [Why is it important to avoid infinite loops, and how can you prevent them?]()

---

<br>

## Additional Resources
This section offers useful links to relevant content. It's optional and meant to be extra material for further reading.(Note: Some resources might require you you to have access to the Algo++ Google drive in order to view it.)
- [UP Algo++ Control Flow and Loops Lecture Slides](https://docs.google.com/presentation/d/19vQAPQ4tASUD5gR1OjVtzKT7Ygc0HI8VTVcn_03uAaE/edit#slide=id.g164c8dcc09a_1_48)
- [UP Algo++ Functions Lecture Slides](https://docs.google.com/presentation/d/1yNLnBwnIMmlVDKh6m-b6r_EPMyabi9EBiTr37HE6q9w/edit#slide=id.g164c8dcc09a_1_48)

---

<br>

## Summary

In this lesson, we've explored two fundamental concepts in C++ programming: **loops** and **functions**.

- **Loops** allow your programs to execute code repeatedly, which is essential for tasks that require iteration, such as processing arrays, generating sequences, or performing calculations until a certain condition is met.
  - **For Loops** are ideal when you know the exact number of iterations needed.
  - **While Loops** are useful when the number of iterations depends on a condition evaluated before each iteration.
  - **Do-While Loops** guarantee that the loop body executes at least once, with the condition evaluated after each iteration.

- **Functions** enable you to encapsulate code into reusable blocks, making your programs more organized and modular. By passing parameters and returning values, functions can perform specific tasks and computations that can be used throughout your program.

By completing the mini-assignments and exploring the additional resources, you've gained practical experience with loops and functions, strengthening your understanding of these core programming constructs. Keep practicing, and don't hesitate to revisit these concepts as you continue your journey in learning C++.

