# Part 3: Structures and Classes

In this part, we will delve into **structures** (`struct`) and **classes** in C++. These are fundamental concepts in object-oriented programming that allow you to group related variables and functions.

## Structures (`struct`)

Structures are used to group variables of different types under a single name. They are particularly useful for representing complex data types.

### Defining and Using a `struct`

To define a structure, use the `struct` keyword followed by the structure name and its members enclosed in braces `{}`.

```cpp
#include <iostream>
#include <string> // Include the string library
using namespace std;

struct Student {
    string name;
    int age;
    double gpa;
};

int main() {
    // Creating an instance of Student and initializing it
    Student s1 = {"Alice", 20, 3.8};

    // Accessing struct members using the dot operator
    cout << "Name: " << s1.name << endl;
    cout << "Age: " << s1.age << endl;
    cout << "GPA: " << s1.gpa << endl;

    return 0;
}
```

**Explanation:**

- **Definition:** We define a `Student` structure with three members: `name`, `age`, and `gpa`.
- **Initialization:** We create an instance `s1` of `Student` and initialize it with values.
- **Accessing Members:** We access the members using the dot `.` operator.

<br>

### Assignment

---

**Task:** Write a C++ program that:

1. Defines a `struct` named `Book` with the following members:
   - `string title`
   - `string author`
   - `int pages`
2. Creates an instance of `Book` and initializes it with values of your choice.
3. Prints out the details of the book.

**Example Output:**

```
Title: The Great Gatsby
Author: F. Scott Fitzgerald
Pages: 180
```

**Hint:** Use the same structure as the `Student` example. Don't forget to include the `<string>` library.

---

<br>

## Classes

Classes are user-defined data types that allow you to model real-world entities by combining data and functions that operate on that data. They are fundamental to object-oriented programming in C++.

### Defining and Using a Basic Class

Let's start by defining a simple class without private members.

```cpp
#include <iostream>
#include <string>
using namespace std;

class Animal {
public:
    string name;
    int age;

    void speak() {
        cout << "My name is " << name << " and I am " << age << " years old." << endl;
    }
};

int main() {
    Animal dog;
    dog.name = "Buddy";
    dog.age = 5;
    dog.speak(); // Output: My name is Buddy and I am 5 years old.

    return 0;
}
```

**Explanation:**

- **Class Definition:** We define a class `Animal` with two public data members (`name` and `age`) and one member function `speak()`.
- **Creating an Object:** We create an instance of `Animal` named `dog`.
- **Accessing Members:** Since the members are public, we can access them directly using the dot `.` operator.
- **Member Function:** The `speak()` function prints out the animal's name and age.

<br>

### Introducing Access Control

In the previous example, all members were public. In practice, it's better to keep data members private and provide public methods to access them. This is called **encapsulation**.

```cpp
#include <iostream>
#include <string>
using namespace std;

class Animal {
private:
    string name;
    int age;

public:
    // Setter methods
    void setName(string n) {
        name = n;
    }

    void setAge(int a) {
        if (a >= 0) {
            age = a;
        } else {
            cout << "Age cannot be negative." << endl;
        }
    }

    // Getter methods
    string getName() const {
        return name;
    }

    int getAge() const {
        return age;
    }

    // Member function
    void speak() const {
        cout << "My name is " << name << " and I am " << age << " years old." << endl;
    }
};

int main() {
    Animal cat;
    cat.setName("Whiskers");
    cat.setAge(3);
    cat.speak(); // Output: My name is Whiskers and I am 3 years old.

    // Trying to set a negative age
    cat.setAge(-1); // Output: Age cannot be negative.

    return 0;
}
```

**Explanation:**

- **Private Members:** The data members `name` and `age` are declared as `private`, so they cannot be accessed directly from outside the class.
- **Public Methods:** We provide `setName()`, `setAge()`, `getName()`, and `getAge()` methods to interact with the private data.
- **Input Validation:** In `setAge()`, we check if the provided age is non-negative before setting it.
- **Member Function:** The `speak()` function uses the private members to output the animal's details.

<br>

### Constructors

A **constructor** is a special member function that is called when a new object is created. It can be used to initialize the object's data members.

```cpp
#include <iostream>
#include <string>
using namespace std;

class Animal {
private:
    string name;
    int age;

public:
    // Default constructor
    Animal() : name("Unknown"), age(0) {}

    // Parameterized constructor
    Animal(string n, int a) : name(n), age(a) {}

    // Member functions
    void speak() const {
        cout << "My name is " << name << " and I am " << age << " years old." << endl;
    }
};

int main() {
    Animal animal1; // Calls default constructor
    animal1.speak(); // Output: My name is Unknown and I am 0 years old.

    Animal animal2("Bella", 4); // Calls parameterized constructor
    animal2.speak(); // Output: My name is Bella and I am 4 years old.

    return 0;
}
```

**Explanation:**

- **Default Constructor:** Initializes `name` to "Unknown" and `age` to 0 when no arguments are provided.
- **Parameterized Constructor:** Allows initializing `name` and `age` with specific values.
- **Creating Objects:** We create `animal1` using the default constructor and `animal2` using the parameterized constructor.

<br>

### Adding a Second Example: `BankAccount` Class

Let's create a `BankAccount` class to represent a simple bank account.

```cpp
#include <iostream>
#include <string>
using namespace std;

class BankAccount {
private:
    string owner;
    double balance;

public:
    // Constructor
    BankAccount(string o, double b) : owner(o), balance(b) {}

    // Method to deposit money
    void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
            cout << "Deposited $" << amount << " into " << owner << "'s account." << endl;
        } else {
            cout << "Deposit amount must be positive." << endl;
        }
    }

    // Method to withdraw money
    void withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
            cout << "Withdrew $" << amount << " from " << owner << "'s account." << endl;
        } else {
            cout << "Invalid withdrawal amount." << endl;
        }
    }

    // Method to check balance
    double getBalance() const {
        return balance;
    }

    // Method to display account info
    void display() const {
        cout << "Owner: " << owner << ", Balance: $" << balance << endl;
    }
};

int main() {
    BankAccount account("John Doe", 1000.0);

    account.display(); // Output: Owner: John Doe, Balance: $1000

    account.deposit(500); // Output: Deposited $500 into John Doe's account.
    account.withdraw(200); // Output: Withdrew $200 from John Doe's account.

    account.display(); // Output: Owner: John Doe, Balance: $1300

    account.withdraw(1500); // Output: Invalid withdrawal amount.

    return 0;
}
```

**Explanation:**

- **Private Members:** `owner` and `balance` are private.
- **Constructor:** Initializes the account with an owner and a starting balance.
- **Methods:** Provides methods to deposit, withdraw, check balance, and display account information.
- **Validation:** Ensures that deposit and withdrawal amounts are valid.

<br>

### Key Concepts in Classes

- **Encapsulation:** Bundling data and methods that operate on that data within a single unit (class), and restricting access to some of the object's components.
- **Access Specifiers:** Keywords like `private`, `protected`, and `public` that control access to class members.
- **Constructors:** Special functions called when an object is created. They can be used to initialize data members.
- **Member Functions (Methods):** Functions defined inside a class that operate on its objects.

<br>

### Assignment
---

**Task:** Write a C++ program that:

1. Defines a `class` named `Car` with the following private members:
   - `string make`
   - `string model`
   - `int year`
   - `double mileage`
2. Includes the following public methods:
   - A constructor that initializes all the data members.
   - Getter and setter methods for each data member.
   - A method `drive(double miles)` that increases the `mileage` by `miles`.
   - A method `displayInfo()` that prints out all the car's information.
3. In `main()`, create an instance of `Car`, set its attributes, drive it for a certain number of miles, and display its information.

**Example Output:**

```
Car Information:
Make: Toyota
Model: Camry
Year: 2015
Mileage: 50000

Driving the car for 150 miles.

Updated Car Information:
Make: Toyota
Model: Camry
Year: 2015
Mileage: 50150
```

**Hint:** Use the pattern from the `BankAccount` class example. Remember to validate inputs where appropriate.

---

<br>

## Key Differences Between `struct` and `class`

- **Default Access Modifier:**
  - **`struct`:** Members are **public** by default.
  - **`class`:** Members are **private** by default.
- **Usage:**
  - **`struct`:** Traditionally used for passive objects with public data members and no functions.
  - **`class`:** Used when you need encapsulation, access control, constructors, and member functions.

> **Note:** In modern C++, both `struct` and `class` can have member functions and access control; the only difference is the default access level.

### When to Use `struct` or `class`

- Use `struct` for simple data structures that primarily hold data and have minimal or no functions.
- Use `class` when you need to enforce encapsulation, have complex behavior, or need constructors and destructors.

<br>

## Summary

Classes and structures in C++ allow you to create your own custom data types that can model real-world entities. By understanding and utilizing access specifiers, constructors, and member functions, you can write more organized, maintainable, and robust code.

- **Structures (`struct`):** Best for simple groupings of data where encapsulation isn't a concern.
- **Classes (`class`):** Ideal for complex data types that require encapsulation, data hiding, and member functions.

<br>

## Knowledge check
These questions provide a chance to think about the important topics covered in this lesson. If you're unsure of an answer, revisit the material. Remember, you're not expected to memorize or fully master this information right now.
- [How to define a struct and how can you use them in your C++ code?](https://github.com/UP-Algorithm-Plus-Plus/CPP-Crash-Course-2425A/blob/main/Week_3/Part3.md#structures-struct) 
- [How to define a class without private members?](https://github.com/UP-Algorithm-Plus-Plus/CPP-Crash-Course-2425A/blob/main/Week_3/Part3.md#defining-and-using-a-basic-class)
- [How do you create an object using a class? How do you modify the object's data and run functions/methods using the object?](https://github.com/UP-Algorithm-Plus-Plus/CPP-Crash-Course-2425A/blob/main/Week_3/Part3.md#defining-and-using-a-basic-class)
- [How do define a class with private members?](https://github.com/UP-Algorithm-Plus-Plus/CPP-Crash-Course-2425A/blob/main/Week_3/Part3.md#introducing-access-control)
- [What are constructors and how do you use them?](https://github.com/UP-Algorithm-Plus-Plus/CPP-Crash-Course-2425A/blob/main/Week_3/Part3.md#constructors)

<br>

## Additional Resources
This section offers useful links to relevant content. It's optional and meant to be extra material for further reading.(Note: Some resources might require you you to have access to the Algo++ Google drive in order to view it.)
- [UP Algo++ Struct and Class Lecture Slides](https://docs.google.com/presentation/d/1RXYMykyswn3_voSt6wEDM7K2uMmIf0KAwH96WhVoUTQ/edit#slide=id.g164c8dcc09a_1_48)


