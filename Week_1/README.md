# C++ Crash Course Week 1 (NOT DONE)
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

C++ is a powerful programming language used for a variety of applications, from system software to game development. In this guide, you'll learn the basics and get hands-on with coding right away.

---

#### Parts of Basic C++ Code

At its core, every C++ program contains a structure similar to this:

```cpp
#include <bits/stdc++.h>                       // Preprocessor directive/Library
using namespace std;                           // Use the Standard Namespace

int main() {                                   // The main function where execution starts
    cout << "Hello, World!" << endl;           // Print statement
    return 0;                                  // End the program
}
```

**Breakdown**:
- `#include <bits/stdc++.h>`: This directive imports all standard libraries, covering a wide range of functions like math operations, input/output, algorithms, and string handling.
- `using namespace std;`: This allows you to write `cout` and `endl` without the `std::` prefix, which simplifies small programs but may cause conflicts in larger ones.
- `int main()`: Every C++ program must have a `main` function, which is the entry point where the program starts executing.
- `cout`: This is used to output text to the console. In this case, it prints "Hello, World!".
- `return 0;`: This signals the program has executed successfully and terminates it.

---

#### Assignment
1. Write the "Hello, World!" program yourself (type it manually for practice) and change the message to "Welcome to C++!". Then, compile and run it.
2. Modify your code by adding another `cout` statement to print your name. Try running the program again.

---


#### Input/Output

**Input** allows users to provide data, and **output** displays the results. In C++:
- `std::cout` is used for output.
- `std::cin` is used for input.


```cpp
#include <iostream>            // Import the library for Input/Output

int main() {
    int age;                                                      
    std::cout << "Enter your age: ";             // Prompt the user for input
    std::cin >> age;                             // Store the input in the "age" variable

    std::cout << "You are " << age << " years old." << std::endl; // Output the result
    return 0;
}
```

Here’s a revised version of your paragraph:

When you run the code above, you'll see:

```
Enter your age:
```

Try typing the code yourself (no copy-pasting!), run it, and when prompted, input your age and press "Enter." The program will then display your age in the following format: `You are <inputted age> years old.`

---

#### Variables

Variables are things that store specific types of data (depending on what the variable is instructed to accept). Below is a basic example of variables in C++

**Basic Variables Example**:
Variables are placeholders that store different types of data. Here's an example:

```cpp
int x = 5;               // Integer variable initialized to 5

double y;                // Declare an empty double variable
y = 4.2;                 // Assign the value 4.2 to y

char grade = 'A';        // Character variable initialized with 'A'
```

Variables follow the format: `<data-type> <variable-name>;` or `<data-type> <variable-name> = <value>;`. You can declare a variable first and assign a value later, or initialize it immediately.

**Common Data Types**:
- `int`: Stores integers (e.g., `42`, `-3`).
- `float`: Stores single-precision floating-point numbers (e.g., `3.14`).
- `double`: Stores double-precision floating-point numbers with more accuracy than `float`.
- `char`: Stores a single character (e.g., `'A'`, `'3'`).
- `bool`: Stores boolean values (`true` or `false`).
- `string`: Stores sequences of characters (e.g., `"Hello!"`). Use with `#include <string>`.

---

#### Arithmetic Operators

The code below shows all of the arithmethic operators that you can use when coding in C++!

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
    // Additional Note: These operators are also used in other programming languages

    return 0;                   // Signals the end of the program
}
```

---

#### Assignment

1. Create a program that accepts two integers, A and B, then prints the results of A + B, A - B, A * B, A / B, and the remainder (A % B).
2. Write a program that declares variables of different types and prints them.

---

#### Knowledge check
These questions provide a chance to think about the important topics covered in this lesson. If you're unsure of an answer, click the question to revisit the material. Remember, you're not expected to memorize or fully master this information.
- Note: put resources below in "Additional resources"
- [How do you output things to the terminal and accept input in C++?](https://www.geeksforgeeks.org/basic-input-output-c/)
- [How do you create different types of variables in C++?](https://www.geeksforgeeks.org/cpp-variables/)

---

#### Additional Resources
This part offers useful links to relevant content. It's optional and meant to be extra material for further reading.
- [Basic I/O Practice Problems on HackerRank](https://www.hackerrank.com/challenges/cpp-input-and-output/problem)

---

#### Arrays

Arrays are things that contain a serious of different values (depending on what it is declared to contain). For other programming languages, arrays may accept more than 1 type of data type. For now, we will only be talking about one-dimensional arrays.

Below is an example of an array (that can be placed inside of the `int main` function)

**Array Example**:
```cpp
int numbers[5] = {1, 2, 3, 4, 5};     
/*
  numbers is declared to be a static 1-dimensional array that will contain 5 integer values divided by ","

  static here means that its something that will always hold a specific number of elements at all times,
  and the size of the array cannot be change. 
*/

// Note: We start counting at 0
std::cout << numbers[0] << std::end;              // Access and print first element
std::cout << numbers[1] << std::end;              // Access and print second element
std::cout << numbers[2] << std::end;              // Access and print third element
std::cout << numbers[3] << std::end;              // Access and print fourth element
std::cout << numbers[4] << std::end;              // Access and print fifth element
```

---

#### Assignment
1. Write a program that declares arrays for the following data types: double, int, char, and string (Note that if you do not use `using namespace std;`, ensure that string is declared as `std::string arrayName[number of elements] = {elements};`). Each array must have 3 elements each.
2. Using the same program you made, print the first element of the double array, the second element of the int array, the third element of the char array, and all of the elements of the string array.

---

#### Knowledge check
These questions provide a chance to think about the important topics covered in this lesson. If you're unsure of an answer, click the question to revisit the material. Remember, you're not expected to memorize or fully master this information.
- Note: put resources below in "Additional resources"
- 

---

#### Additional Resources
This part offers useful links to relevant content. It's optional and meant to be extra material for further reading.
- [Basi

---

#### Conditional Statements

Conditional statements control the flow of a program based on certain conditions.

```cpp
int age = 20;

if (age >= 18) {
    std::cout << "You are an adult.";
} else {
    std::cout << "You are not an adult.";
}
```

---

#### Assignment
1. Create a basic Calculator using C++! Make it so that the Calculator can take in two integer inputs A and B from the user and ask the user what operation does the user want to perform (A + B, A - B, A * B, or A / B). Have the calculator print the result of its calculations. Ensure that when the user picks division, the remainder from the division operation is also printed. 
2. Try solving the [Quadrant Selection](https://open.kattis.com/problems/quadrant) programming problem!

---

#### Knowledge check
These questions provide a chance to think about the important topics covered in this lesson. If you're unsure of an answer, click the question to revisit the material. Remember, you're not expected to memorize or fully master this information.
- N

---

#### Additional Resources
This part offers useful links to relevant content. It's optional and meant to be extra material for further reading.
- 

---







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

