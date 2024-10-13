# C++ Crash Course Week 1 Part 3 ~ C++ Basics

## Introduction to C++

C++ is a versatile and high-performance programming language that has been a cornerstone of software development for decades. From operating systems like Windows to game engines like Unreal Engine, C++ powers many of the applications we use every day. In this guide, we'll embark on a journey to explore the fundamentals of C++ programming, providing you with a solid foundation to build upon. We'll dive into writing code from the very beginning, ensuring that you get practical experience as you learn.


<br>

## Parts of a Basic C++ Program

At its core, every C++ program contains certain essential components. Let's look at a simple program and break down each part to understand how it works:

```cpp
#include <iostream>            // Include the Input/Output stream library

int main() {                   // The main function where program execution begins
    std::cout << "Hello, World!" << std::endl; // Output "Hello, World!" to the console
    return 0;                  // Return 0 to indicate successful execution
}
```

**Breakdown**:

- `#include <iostream>`: This preprocessor directive tells the compiler to include the standard Input/Output stream library, which is necessary for using `std::cout` and `std::cin`.
- `int main()`: Every C++ program must have a `main` function, which serves as the entry point where the program starts executing.
- `std::cout << "Hello, World!" << std::endl;`: This line outputs the string "Hello, World!" to the console. `std::cout` is the standard output stream, `<<` is the insertion operator, and `std::endl` inserts a newline character and flushes the output buffer.
- `return 0;`: This statement indicates that the program executed successfully and returns control to the operating system.

**Note**: You might have seen examples that include `using namespace std;`, which allows you to omit the `std::` prefix. However, in professional code, it's generally better to avoid this practice to prevent potential naming conflicts and to make the code clearer.

<br>

### Assignment
---
1. Write the "Hello, World!" program yourself (type it manually for practice) and change the message to "Welcome to C++!". Then, compile and run it.
2. Modify your code by adding another `std::cout` statement to print your name. Try running the program again.

<br>

## Input and Output in C++

**Input** allows programs to receive data from the user, while **output** enables programs to display data to the user. In C++, we use streams to handle input and output operations:

- `std::cout`: The standard output stream used for writing to the console.
- `std::cin`: The standard input stream used for reading from the console.

Here's an example that demonstrates basic input and output:

```cpp
#include <iostream>  // Include the Input/Output stream library

int main() {
    int age;                                 // Declare an integer variable to store the age
    
    std::cout << "Enter your age: ";         // Prompt the user for input
    std::cin >> age;                         // Read the input from the user and store it in "age"
    
    std::cout << "You are " << age << " years old." << std::endl; // Display the age
    return 0;
}
```

**Explanation**:

- `std::cin >> age;`: The extraction operator `>>` reads input from the console and stores it in the variable `age`. The program waits for the user to input data and press "Enter".

**Try It Yourself**:

Type the code manually (avoid copy-pasting to improve retention), compile, and run it. When prompted, enter your age and see how the program responds.

<br>

### Using `std::getline()`

The `std::getline()` function allows you to read an entire line of input, including spaces, and store it in a string variable. This is particularly useful when you need to read a full sentence or a name that includes spaces.

**Example with `std::getline()`**:

```cpp
#include <iostream>    // Include the Input/Output stream library
#include <string>      // Include the string library to use std::string

int main() {
    std::string fullName;                           // Declare a string variable to store the name
    
    std::cout << "Enter your full name: ";          // Prompt the user for input
    std::getline(std::cin, fullName);               // Read the entire line of input and store it in "fullName"
    
    std::cout << "Hello, " << fullName << "!" << std::endl; // Greet the user by name
    return 0;
}
```

**Explanation**:

- `std::getline(std::cin, fullName);`: This function reads characters from the input stream `std::cin` until it encounters a newline character (`'\n'`), storing all characters read into the string `fullName`.

**Important Note**:

- If you use `std::cin` before `std::getline()`, you might encounter issues due to leftover newline characters in the input buffer. To handle this, you can clear the input buffer or use `std::cin.ignore()`.

**Handling Input Buffer Issues**:

```cpp
#include <iostream>
#include <string>
#include <limits> // Include this header to use std::numeric_limits

int main() {
    int age;
    std::string fullName;

    std::cout << "Enter your age: ";
    std::cin >> age;

    std::cin.ignore(std::numeric_limits<std::streamsize>::max(), '\n'); // Clear the input buffer

    std::cout << "Enter your full name: ";
    std::getline(std::cin, fullName);

    std::cout << "Hello, " << fullName << "! You are " << age << " years old." << std::endl;

    return 0;
}
```

**Explanation**:

- After reading `age` with `std::cin >> age;`, there is a leftover newline character in the input buffer.
- `std::cin.ignore(std::numeric_limits<std::streamsize>::max(), '\n');` discards characters in the input buffer until a newline character is found, effectively clearing it.

<br>



### Assignment
---
1. **Using `std::getline()`**:

   - Write a program that asks the user to enter their address, which may contain spaces and multiple lines. Use `std::getline()` to read the full address and then print it back to the user.

2. **Handling Input Buffer**:

   - Modify the previous program to first ask for the user's name using `std::cin >> name;`, then ask for the address using `std::getline()`. Handle the input buffer appropriately so that both inputs are correctly read and displayed.


<br>

## Variables and Data Types

In programming, variables are like containers that hold data values. Each variable has a specific data type that determines the kind of data it can store and the operations you can perform on it.



### Declaring Variables

Variables in C++ are declared by specifying the data type followed by the variable name. You can also initialize the variable at the time of declaration.

**Syntax**:

```cpp
<data-type> <variable-name>;            // Declaration without initialization
<data-type> <variable-name> = <value>;  // Declaration with initialization
```

**Examples**:

```cpp
int x = 5;            // Integer variable initialized to 5

double y;             // Declare a double variable without initializing
y = 4.2;              // Assign the value 4.2 to y

char grade = 'A';     // Character variable initialized with 'A'

bool isStudent = true; // Boolean variable initialized to true

std::string name = "Alice"; // String variable initialized with "Alice"
```

**Common Data Types in C++**:

- `int`: Represents integer numbers, both positive and negative (e.g., `42`, `-7`).
- `float`: Represents single-precision floating-point numbers (e.g., `3.14`, `-0.001`).
- `double`: Represents double-precision floating-point numbers, offering more precision than `float` (e.g., `2.71828`).
- `char`: Represents a single character (e.g., `'A'`, `'b'`, `'3'`).
- `bool`: Represents Boolean values `true` or `false`.
- `std::string`: Represents a sequence of characters (e.g., `"Hello, World!"`). To use `std::string`, include the `<string>` header.



### Variable Naming Rules

When naming variables in C++, follow these rules:

- Names can contain letters (both uppercase and lowercase), digits, and underscores (`_`).
- Names must begin with a letter or an underscore, not a digit.
- Names are case-sensitive (`myVar` and `myvar` are different variables).
- Avoid using reserved keywords (like `int`, `double`, `class`, etc.) as variable names.



### Constants

If you have a value that should not change during the program execution, you can declare it as a constant using the `const` keyword.

**Example**:

```cpp
const double PI = 3.14159; // PI is a constant and cannot be modified
```

Attempting to modify a constant variable will result in a compilation error.

<br>



### Assignment
---
1. **Variable Declaration and Printing**:

   - Declare variables of different data types (`int`, `double`, `char`, `bool`, `std::string`) and initialize them with values of your choice.
   - Write a program to print these variables to the console in a formatted way.

2. **Calculating the Area of a Circle**:

   - Create a program that calculates the area of a circle.
   - Prompt the user to enter the radius as a `double`.
   - Use a `const` variable for π (`PI = 3.14159`).
   - Calculate the area using the formula: Area = π × radius².
   - Display the calculated area to the user.


<br>

## Arithmetic Operators

C++ supports various arithmetic operators that allow you to perform mathematical calculations. These operators work with numeric data types like `int`, `float`, and `double`.

### Basic Arithmetic Operators

- **Addition (`+`)**: Adds two operands.
- **Subtraction (`-`)**: Subtracts the second operand from the first.
- **Multiplication (`*`)**: Multiplies two operands.
- **Division (`/`)**: Divides the numerator by the denominator.
- **Modulo (`%`)**: Returns the remainder of an integer division.

**Example Program**:

```cpp
#include <iostream>

int main() {
    int num1 = 10;    // Declare and initialize num1
    int num2 = 5;     // Declare and initialize num2

    int sum = num1 + num2;          // Addition: 10 + 5 = 15
    int difference = num1 - num2;   // Subtraction: 10 - 5 = 5
    int product = num1 * num2;      // Multiplication: 10 * 5 = 50
    int quotient = num1 / num2;     // Division: 10 / 5 = 2
    int remainder = num1 % num2;    // Modulo: 10 % 5 = 0

    std::cout << "Sum: " << sum << std::endl;
    std::cout << "Difference: " << difference << std::endl;
    std::cout << "Product: " << product << std::endl;
    std::cout << "Quotient: " << quotient << std::endl;
    std::cout << "Remainder: " << remainder << std::endl;

    return 0;
}
```

**Output**:

```
Sum: 15
Difference: 5
Product: 50
Quotient: 2
Remainder: 0
```

**Notes**:

- **Integer Division**: When dividing two integers, the result is an integer. Any fractional part is discarded (not rounded).
  - Example: `7 / 2` results in `3` (not `3.5`).
- **Modulo Operator `%`**: Only works with integer operands. It returns the remainder after division.
  - Example: `11 % 3` results in `2` because `11` divided by `3` is `3` with a remainder of `2`.



### Operator Precedence

Operator precedence determines the order in which operations are performed in an expression without parentheses. In C++, arithmetic operators have the following precedence (from highest to lowest):

1. Multiplication (`*`), Division (`/`), and Modulo (`%`)
2. Addition (`+`) and Subtraction (`-`)

Operators with higher precedence are evaluated before operators with lower precedence.

**Example**:

```cpp
int result = 10 + 5 * 2; // Multiplication is performed before addition
// result = 10 + (5 * 2) = 10 + 10 = 20
```

To control the order of operations, use parentheses:

```cpp
int result = (10 + 5) * 2; // Parentheses change the order
// result = (10 + 5) * 2 = 15 * 2 = 30
```



### Assignment Operators

C++ also provides shorthand assignment operators that combine arithmetic and assignment:

- `+=`: Addition assignment (`x += y` is equivalent to `x = x + y`)
- `-=`: Subtraction assignment (`x -= y` is equivalent to `x = x - y`)
- `*=`: Multiplication assignment (`x *= y` is equivalent to `x = x * y`)
- `/=`: Division assignment (`x /= y` is equivalent to `x = x / y`)
- `%=`: Modulo assignment (`x %= y` is equivalent to `x = x % y`)

**Example**:

```cpp
int x = 10;
x += 5;  // x is now 15
x *= 2;  // x is now 30
```

<br>




### Assignment
---
1. **C++ Arithmethic**:

   - Create a program that accepts two integers, `A` and `B`, from the user.
   - Perform and print the results of the following operations: `A + B`, `A - B`, `A * B`, `A / B`, and `A % B`.
   - Ensure your program handles division by zero appropriately (display an error message if `B` is zero).

2. **Variable Types and Printing**:

   - Write a program that declares variables of different types (`int`, `double`, `char`, `bool`, `std::string`).
   - Assign values to these variables.
   - Print the values and data types to the console in a formatted manner.

3. **Area and Circumference Calculator**:

   - Write a program that asks the user to enter the radius of a circle.
   - Calculate and display the area and circumference of the circle.
   - Use `const double PI = 3.14159;` for π.
   - Formulas:
     - Area = π × radius²
     - Circumference = 2 × π × radius


<br>

## Summary

In this lesson, we've introduced the fundamental concepts of C++ programming. You've learned about the structure of a basic C++ program, how to perform input and output operations, declare and use variables of different data types, and utilize arithmetic operators to perform calculations. By completing the assignments, you'll gain practical experience that reinforces these concepts. As you progress, you'll build upon this foundation to tackle more complex programming challenges.


<br>

## Knowledge check
These questions provide a chance to think about the important topics covered in this lesson. If you're unsure of an answer, revisit the material. Remember, you're not expected to memorize or fully master this information right now.
- [What are the different parts of a C++ program?](https://github.com/UP-Algorithm-Plus-Plus/CPP-Crash-Course-2425A/blob/week_1/Week_1/Part3.md#parts-of-a-basic-c-program)
- [How do you display a message on the console in C++?](https://github.com/UP-Algorithm-Plus-Plus/CPP-Crash-Course-2425A/blob/week_1/Week_1/Part3.md#parts-of-a-basic-c-program)
- [What are the two methods for accepting user input in C++, and how do you implement them?](https://github.com/UP-Algorithm-Plus-Plus/CPP-Crash-Course-2425A/blob/week_1/Week_1/Part3.md#input-and-output-in-c)
- [What are the different C++ data types you can use?](https://github.com/UP-Algorithm-Plus-Plus/CPP-Crash-Course-2425A/blob/week_1/Week_1/Part3.md#variables-and-data-types)
- [How do you create variables of different data types in C++ and initialize them with values?](https://github.com/UP-Algorithm-Plus-Plus/CPP-Crash-Course-2425A/blob/week_1/Week_1/Part3.md#variables-and-data-types)
- [What are the C++ arithmetic operators?](https://github.com/UP-Algorithm-Plus-Plus/CPP-Crash-Course-2425A/blob/week_1/Week_1/Part3.md#arithmetic-operators)
- [What are the C++ assignment operators?](https://github.com/UP-Algorithm-Plus-Plus/CPP-Crash-Course-2425A/blob/week_1/Week_1/Part3.md#assignment-operators)


<br>

## Additional Resources
This section offers useful links to relevant content. It's optional and meant to be extra material for further reading.(Note: Some resources might require you you to have access to the Algo++ Google drive in order to view it.)
- [UP Algo++ C++ Basics Lecture Slides](https://docs.google.com/presentation/d/1GTqu2WP6rm03Y3yAxIiNY4M2I0Lk1kRFdhG84h0_h7g/edit?usp=drive_link)
- [UP Algo++ C++ Input/Output Lecture Slides](https://docs.google.com/presentation/d/171anDJYv_f7trafJEeXXEmoSze4iB0SCJBSn7I16MSg/edit?usp=drive_link)
- [UP Algo++ Operators Lecture Slides](https://docs.google.com/presentation/d/1LPdjDwG50FknS5a6r6U_7k1mDqxk9QMrVt4uEKo8n70/edit#slide=id.g164c8dcc09a_1_48)
- [Writing your first C++ Program](https://youtu.be/S3nx34WFXjI?si=bl7KWLkNVqV127f1&t=555)
- [C++ Variables and Data Types](https://youtu.be/4psGUiKacPQ?si=ofueh2lltS3fswlY)
- [How to accept user input in C++?](https://youtu.be/imiIhu9u670?si=wXMfukWzcjxbN-Gq)
