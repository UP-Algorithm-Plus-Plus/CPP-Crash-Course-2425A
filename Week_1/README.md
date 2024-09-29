# C++ Crash Course for Competitive Programming Beginners (NOT DONE)
---

Welcome to your journey into the world of competitive programming with C++! This course is designed to equip you with the following:
- Programming Setup
- Brief Introduction to Competitive Programming
- C++ Basics
    - Intro to C++
    - Arrays
    - Conditionals
    - Loops
    - Functions
- Others (maybe coming soon)

---

## 📋 Table of Contents
- [Introduction](#introduction)
- [Getting Started](#getting-started)
  - [Hello World](#hello-world)
  - [Basic Input/Output](#basic-inputoutput)

---

## Programming Environment Set-up

Insert
- Guide for Windows
- Guide for Mac
- Guide for Linux
- Text editors and IDEs
- Compiler
- Use external resources

---

## Brief Introduction to Competitive Programming

aaa

---

## C++ Basics

### Intro to C++

#### Parts of Basic C++ Code

At its core, every C++ program contains a structure similar to this:

```cpp
#include <bits/stdc++.h>                       // Preprocessor directive/Library
using namespace std;                           // Makes the program use the "Standard Namespace"

int main() {                                   // The main function where execution starts
    cout << "Hello, World!" << endl;           // Print statement
    return 0;                                  // End the program
}
```

**Breakdown**:
- `#include <bits/stdc++.h>`: This imports the library for every function you would need. Functions like the math functions, input/output functions, algorithms, string handling, etc.
- `using napespace std;`: This makes it so that you don't need to type `cout` and `endl` as `std::cout << "Hello, World!" << std::end;`, its useful for simple/small programs, but not so much in larger programs as it might result in conflicts with other namespaces. 
- `int main()`: Every C++ program must have a `main` function, which is where the program starts executing.
- `cout`: Outputs data to the console. In this case, it's "Hello, World!" 
- `return 0`: Signals the end of the program.

#### Assignment
1. Try programming in C++ by copying the "Hello, World!" C++ program (Don't Copy paste it! Type it, so that you start building muscle memory.) and change "Hello, World!" to "Welcome to C++!" Then run it!
2. Modify what you did in #1 by adding another print statement that prints your name instead of "Hello, World!" After that, try and run your program!

#### Input/Output

**Input** allows users to provide data, and **output** displays the results. In C++:
- `std::cout` is used for output.
- `std::cin` is used for input.

```cpp
#include <iostream>                                                 // Imports the library for Input/Output functions

int main() {
    int age;                                                        // Creates an integer variable called "age"
    std::cout << "Enter your age: ";                                // Prints "Enter your age:" and does not move on to the next line in the console
    std::cin >> age;                                                // Input stored in variable 'age'
    std::cout << "You are " << age << " years old." << std::endl;   // Prints "You are <inputted age> years old."
    return 0;                                                       // Signals the end of the program
}
```

When you run the code above, you are expected to see something like this in the console:
```
Enter your age: 
```

What's happening here is that the program is waiting for you to type something. Try and copy the code above (again try not to copy paste the code) and then run it, then see what happens when you type a number in the console and press enter. 

#### Variables & Arithmethic Operators

Variables are things that store specific types of data (depending on what the variable is instructed to accept). Below is a basic example of variables in C++

**Basic Variables Example**:
```cpp
int x = 5;        // Integer variable that is initiliazed with the number 5

double y;         // y is declared as an empty double variable
y = 4.2;          // y is assigned the floating number 4.2

char grade = 'A'; // Character variable that is initialized with the character "A"

```

Variables are usually written like this. Its either `<data-type> <variable-name>;` like `double y;` or `<data-type> <variable-name> = <value>;` like `int x = 5;` and `char grade = 'A'`. You can either declare an empty one like `double y;` at first and give it a value later, or you can also choose to declare a variable and initiliaze it with a value. 

There are multiple more data types in C++, here is a list of data types that you should find very useful and their descriptions:
- `int`  
  *Comment:* Stores integers (whole numbers) like `42` or `-3`.
- `float`  
  *Comment:* Stores single-precision floating-point numbers (e.g., `3.14`).
- `double` 
  *Comment:* Stores double-precision floating-point numbers, more accurate decimal number represtantion than `float`.
- `char`  
  *Comment:* Stores a single character (e.g., `'A'`, `'3'`).
- `bool`  
  *Comment:* Stores boolean values, either `true` or `false`.
- `string`
  *Comment:* Stores strings of characters like "ABCDE" for example. Can only be used if you use the `bits/stdc++.h` library or `string` or `iostream`

Now let's talk about some useful basic operators that you will be regularly using. The example below shows all of the C++ arithmethic operators. 

```cpp
#include <iostream>         // Imports the library for Input/Output functions

int main() {                // Start of C++ code: The main function
    int num1 = 10;          // Declares num1 an integer and initiliazes it with 10                                     
    int num2 = 5;           // Declares num2 an int and inits it with 5
    int output;             // Declares output an int with no initial value

    output = num1 + 3       // output = 10 + 3 = 13 (Addition)
    output = num1 - num2    // output = 10 - 5 = 5  (Substraction)
    output = num2 * 5       // output = 5 * 5 = 25  (Multiplication)
    output = num1 / 2       // output = 10 / 2 = 5  (Division)
    output = 11 % 5         // output = 11 % 5 = 1  (Returns the remainder of a division between two values)

    // Note: % is known as the modulo operator

    return 0;                   // Signals the end of the program
}
```

**Assignment**: 
1. Try and apply what you've learned so far and create a program that accepts two integer numbers A and B and prints the result of A + B, A - B, A * B, and A / B with its remainder. 

#### Arrays


**Array Example**:
```cpp
int numbers[5] = {1, 2, 3, 4, 5};
std::cout << numbers[0]; // Access first element
```

**Assignment**: 
1. Create a program that takes a user's name and age, and then prints a message with this information.
2. Write a program that asks the user for two numbers and prints their sum, difference, product, and quotient.

**Assignment**: 
1. Write a program that declares variables of different types (e.g., `int`, `float`, `char`) and prints them.
2. Write a program that stores 5 different ages in an array and prints the average.
3. Create an array of 10 integers and print only the even numbers.

**Additional Practice**: 
- [C++ Variable Declarations](https://www.learncpp.com/cpp-tutorial/variables-and-assignments/)
- [Arrays in C++](https://www.geeksforgeeks.org/arrays-in-cpp/)
- [Arrays and Data Structures Practice Problems](https://www.hackerrank.com/domains/tutorials/10-days-of-cplusplus)

#### Knowledge check
These questions provide a chance to think about the important topics covered in this lesson. If you're unsure of an answer, click the question to revisit the material. Remember, you're not expected to memorize or fully master this information.
- Note: put resources below in "Additional resources"
- [How do you output things to the terminal and accept input in C++?](https://www.geeksforgeeks.org/basic-input-output-c/)
- [How do you create different types of variables in C++?](https://www.geeksforgeeks.org/cpp-variables/)

#### Additional Resources
This part offers useful links to relevant content. It's optional and meant to be extra material for further reading.
- a


**Additional Practice**: 
- [Basic I/O Practice Problems on HackerRank](https://www.hackerrank.com/challenges/cpp-input-and-output/problem)
---










### Arrays

### Conditionals

Conditionals control the flow of a program based on certain conditions.

```cpp
int age = 20;
if (age >= 18) {
    std::cout << "You are an adult.";
} else {
    std::cout << "You are not an adult.";
}
```

**Mini-Assignments**: 
1. Write a program that checks if a number is even or odd.
2. Create a program that takes in a student's score and prints their letter grade (A, B, C, D, F).
3. Write a program that asks for the user's age and tells them if they are eligible to vote (18 or older).

**Additional Practice**: 
- [Conditional Statements in C++](https://www.learncpp.com/cpp-tutorial/if-statements/)
- [Conditional Statements Practice Problems](https://www.hackerrank.com/challenges/conditional-statements-in-c/problem)

---

### Loops

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

**Mini-Assignments**: 
1. Write a program that prints numbers from 1 to 10 using a `for` loop.
2. Create a program that prints the first 10 numbers in the Fibonacci sequence.
3. Write a program that takes a positive integer `n` as input and prints all numbers from `n` down to 1 using a `while` loop.

**Additional Practice**: 
- [C++ Loops](https://www.learncpp.com/cpp-tutorial/loops/)
- [Looping Practice Problems](https://www.hackerrank.com/challenges/for-loop-in-c/problem)

---

### Functions

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

You can continue building on this guide by adding more advanced topics like pointers, object-oriented programming, and error handling!

```markdown

## Introduction

*Provide a brief overview of the course, its goals, and prerequisites.*

---

## Getting Started

### Hello World

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

---

*Happy Coding and Good Luck on Your Competitive Programming Journey!* 🎯
```

---

You can customize each section by adding explanations, examples, and practice problems relevant to the topic. This template uses clear headings, code blocks with syntax highlighting, and bullet points to enhance readability. Feel free to modify and expand upon this structure to suit your course's needs.
