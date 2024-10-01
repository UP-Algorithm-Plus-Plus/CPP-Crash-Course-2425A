# C++ Crash Course Week 1 Part 4 ~ C++ Basics

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

Conditional statements control the flow of a program based on certain conditions. Below is an example of conditional statements (You can put this directly into `int main` function)

```cpp
int age = 20;                                               // Declare age as an integer and init with value 20

// Runs code depending if (18 <= age < 21) and (age >= 21) and if none of the above
if (age >= 18 && age < 21) {    
    std::cout << "You are considered an adult in a lot of places" << std::endl;

} else if (age >= 21) {
    std::cout << "You are considered an adult who can do what they want in any place of the world." << std::endl;

} else {
    std::cout << "You are not an adult." << std::endl;
}



```

As you can see above, there are three types of conditional statements. 
- `if statement`: This is how you make a conditional statement. If this happens, do this is what it's saying. It can work as a standalone conditional statement. In other words, you don't need to put an `else if` or `else` after it. It's optional.  
- `else if statement`: You can extend your `if statement` with this to make your code work with additional specific conditions in case the `if statement` condition wasn't met. You can also put an `else if statement` before another `else if statement`
- `else statement`: This is always the last part of a conditional statement structure (should you choose to add it, adding it is optional). What this does is if all the conditions before it are not met, the code under the `else statement` is what runs. 

---

#### Assignment
1. Create a basic Calculator using C++! Make it so that the Calculator can take in two integer inputs A and B from the user and ask the user what operation does the user want to perform (A + B, A - B, A * B, or A / B). Have the calculator print the result of its calculations. Ensure that when the user picks division, the remainder from the division operation is also printed. 
2. Try solving the [Quadrant Selection](https://open.kattis.com/problems/quadrant) programming problem!

---

#### Knowledge check
These questions provide a chance to think about the important topics covered in this lesson. If you're unsure of an answer, click the question to revisit the material. Remember, you're not expected to memorize or fully master this information.
- Ho

---

#### Additional Resources
This part offers useful links to relevant content. It's optional and meant to be extra material for further reading.
- 

---







