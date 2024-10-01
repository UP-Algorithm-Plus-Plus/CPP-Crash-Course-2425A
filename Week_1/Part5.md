# C++ Crash Course Week 1 Part 5 ~ C++ Basics

#### Loops

Loops are used to execute a block of code repeatedly.

**For Loop Example**:
```cpp
for (int i = 0; i < 5; i++) {
    std::cout << "Loop iteration: " << i << std::endl;
}
```

**While Loop Example**:
```cpp
int i = 0;
while (i < 5) {
    std::cout << "While loop iteration: " << i << std::endl;
    i++;
}
```

---

#### Functions

Functions group code into reusable blocks. Here’s how to define and use them:

```cpp
int add(int a, int b) {
    return a + b;
}

int main() {
    int sum = add(5, 3);
    std::cout << "Sum is: " << sum << std::endl;
    return 0;
}
```

---









**Additional Practice**: 
- [C++ Variable Declarations](https://www.learncpp.com/cpp-tutorial/variables-and-assignments/)
- [Arrays in C++](https://www.geeksforgeeks.org/arrays-in-cpp/)
- [Arrays and Data Structures Practice Problems](https://www.hackerrank.com/domains/tutorials/10-days-of-cplusplus)




**Mini-Assignments**: 
1. Write a program that checks if a number is even or odd.
2. Create a program that takes in a student's score and prints their letter grade (A, B, C, D, F).
3. Write a program that asks for the user's age and tells them if they are eligible to vote (18 or older).

**Additional Practice**: 
- [Conditional Statements in C++](https://www.learncpp.com/cpp-tutorial/if-statements/)
- [Conditional Statements Practice Problems](https://www.hackerrank.com/challenges/conditional-statements-in-c/problem)

---


**Mini-Assignments**: 
1. Write a program that prints numbers from 1 to 10 using a `for` loop.
2. Create a program that prints the first 10 numbers in the Fibonacci sequence.
3. Write a program that takes a positive integer `n` as input and prints all numbers from `n` down to 1 using a `while` loop.

**Additional Practice**: 
- [C++ Loops](https://www.learncpp.com/cpp-tutorial/loops/)
- [Looping Practice Problems](https://www.hackerrank.com/challenges/for-loop-in-c/problem)

---


**Mini-Assignments**: 
1. Write a function that takes two numbers as input and returns the larger of the two.
2. Create a function that calculates the factorial of a number.
3. Write a program that asks for two numbers and uses a function to return their greatest common divisor (GCD).

**Additional Practice**: 
- [Functions in C++](https://www.learncpp.com/cpp-tutorial/functions/)
- [Function Practice Problems](https://www.hackerrank.com/challenges/functions-in-c/problem)

---

## Additional Learning Resources
1. [C++ Documentation](https://en.cppreference.com/w/)
2. [C++ Track on Exercism](https://exercism.org/tracks/cpp)
3. [C++ Crash Course](https://www.learncpp.com/)
4. [Practice Problems on LeetCode](https://leetcode.com/problemset/all/)
5. [10 Days of C++ on HackerRank](https://www.hackerrank.com/domains/tutorials/10-days-of-cplusplus)

---



Your first C++ program!

```cpp
#include <iostream>

int main() {
    std::cout << "Hello, World!" << std::endl;
    return 0;
}
```

**Explanation:**

- `#include <iostream>`: Includes the standard input/output stream library.
- `int main()`: Entry point of the program.
- `std::cout`: Outputs data to the console.
- `std::endl`: Inserts a newline character and flushes the stream.

### Basic Input/Output

Taking user input and displaying output.

```cpp
#include <iostream>

int main() {
    int number;
    std::cin >> number;
    std::cout << "You entered: " << number << std::endl;
    return 0;
}
```

---

## Variables and Data Types

*Explain different data types (`int`, `float`, `char`, `bool`, etc.) and how to declare variables.*

---

## Operators

- **Arithmetic Operators**: `+`, `-`, `*`, `/`, `%`
- **Relational Operators**: `==`, `!=`, `<`, `>`, `<=`, `>=`
- **Logical Operators**: `&&`, `||`, `!`
- **Bitwise Operators**: `&`, `|`, `^`, `~`, `<<`, `>>`

*Provide examples for each type.*

---

## Control Structures

### Conditional Statements

**If-Else Statement**

```cpp
if (condition) {
    // code block
} else {
    // code block
}
```

### Loops

- **For Loop**

  ```cpp
  for (int i = 0; i < n; ++i) {
      // code block
  }
  ```

- **While Loop**

  ```cpp
  while (condition) {
      // code block
  }
  ```

- **Do-While Loop**

  ```cpp
  do {
      // code block
  } while (condition);
  ```

---

## Functions

*How to declare and define functions, pass parameters, and return values.*

```cpp
return_type function_name(parameter_list) {
    // code block
}
```

---

## Arrays and Strings

- **Arrays**

  ```cpp
  int arr[10]; // declares an array of size 10
  ```

- **Strings**

  ```cpp
  #include <string>

  std::string str = "Hello, World!";
  ```

*Discuss common operations and functions.*

---

## Pointers and References

- **Pointers**

  ```cpp
  int* ptr = &variable;
  ```

- **References**

  ```cpp
  int& ref = variable;
  ```

*Explain concepts with diagrams if possible.*

---

## Standard Template Library (STL)

### Vectors

Dynamic array replacement.

```cpp
#include <vector>

std::vector<int> vec;
vec.push_back(10);
```

### Pairs and Tuples

- **Pairs**

  ```cpp
  std::pair<int, int> p = {1, 2};
  ```

- **Tuples**

  ```cpp
  #include <tuple>

  std::tuple<int, int, int> t = {1, 2, 3};
  ```

### Maps and Sets

- **Map**

  ```cpp
  std::map<std::string, int> mp;
  mp["apple"] = 5;
  ```

- **Set**

  ```cpp
  std::set<int> s;
  s.insert(10);
  ```

### Algorithms

*Using functions like `sort`, `reverse`, `lower_bound`, `upper_bound`.*

---

## Advanced Topics

### Recursion

*Explain the concept with examples like factorial, Fibonacci sequence.*

### Bit Manipulation

*Discuss operations for efficient computation.*

### Macros and Preprocessors

- **Macros**

  ```cpp
  #define MAX 100
  ```

- **Conditional Compilation**

  ```cpp
  #ifdef DEBUG
    // debug code
  #endif
  ```

---

## Input/Output Optimization

*Techniques like using `scanf/printf` vs `cin/cout`, sync with stdio, fast I/O methods.*

```cpp
std::ios::sync_with_stdio(false);
std::cin.tie(0);
```

---

## Practice Problems

1. **Simple Input and Output**

   *Problem Statement*: Write a program that reads an integer and prints it.

2. **Array Manipulation**

   *Problem Statement*: Given an array of `n` integers, find the sum.

*Include links to online judges or attach problem descriptions.*

---

## Additional Resources

- **Books**
  - *Competitive Programming 3* by Steven Halim
  - *Introduction to Algorithms* by Cormen et al.

- **Online Judges**
  - [Codeforces](https://codeforces.com/)
  - [AtCoder](https://atcoder.jp/)
  - [UVa Online Judge](https://onlinejudge.org/)

- **Tutorials**
  - [GeeksforGeeks](https://www.geeksforgeeks.org/c-plus-plus/)
  - [CP-Algorithms](https://cp-algorithms.com/)

