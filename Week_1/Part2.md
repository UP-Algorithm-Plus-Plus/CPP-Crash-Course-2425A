# C++ Crash Course Week 1 Part 2 ~ Coding Environment Setup & Competitive Programming Introduction

---

## Introduction

Welcome to **Week 1 Part 2** of the C++ Crash Course! Before diving deep into coding, it's essential to have a properly configured programming environment. This ensures that you can write, compile, and debug your C++ programs efficiently. Additionally, we'll introduce you to the exciting world of **competitive programming**, a domain where programmers tackle algorithmic problems under time constraints, enhancing both their coding skills and problem-solving abilities.

By the end of this section, you'll have:

- A fully functional C++ programming environment on your machine.
- Written and executed your first C++ program.
- Gained insight into competitive programming and how it can accelerate your learning.

---

## Programming Environment Setup

Setting up a programming environment involves installing a code editor or Integrated Development Environment (IDE), along with the necessary compilers and tools to write and run your programs. We'll guide you through the process for **Windows**, **macOS**, and **Linux** platforms.

---

### Setting Up on Windows

#### Step 1: Install a Code Editor or IDE

For beginners, **Visual Studio Code** is highly recommended due to its simplicity and extensive plugin ecosystem.

- **To install it:**:
  - Download from [Visual Studio Code Website](https://code.visualstudio.com/).
  - Run the installer and follow the prompts.

#### Step 2: Install a C++ Compiler

To compile C++ code on Windows, you'll need to install the **MinGW-w64** compiler or use the **Microsoft C++ Build Tools**.

##### Option 1: Using MinGW-w64

1. **Download MSYS2**:
   - Go to the [MSYS2 Website](https://www.msys2.org/) and download the installer.

2. **Install MSYS2**:
   - Run the installer and follow the instructions.
   - Open the MSYS2 terminal from the Start menu.

3. **Update Package Database**:

   ```bash
   pacman -Syu
   ```

   - Close and reopen the terminal after the update.

4. **Install MinGW-w64 Compiler**:

   ```bash
   pacman -S --needed base-devel mingw-w64-x86_64-toolchain
   ```

5. **Add to System Path**:

   - Add `C:\msys64\mingw64\bin` to your system's PATH environment variable.

6. **Verify Installation**:

   ```bash
   g++ --version
   ```

   - You should see the version information of `g++`.
---

### Setting Up on macOS

#### Step 1: Install Xcode Command Line Tools

macOS comes with the **Clang** compiler, which is part of the Xcode Command Line Tools.

1. **Install Command Line Tools**:

   ```bash
   xcode-select --install
   ```

   - A dialog will appear; click **Install**.

2. **Verify Installation**:

   ```bash
   g++ --version
   ```

   - Should display version information for `g++` (which is a symbolic link to Clang).

#### Step 2: Install a Code Editor or IDE

- **Visual Studio Code**:
  - Download from [Visual Studio Code Website](https://code.visualstudio.com/).
  - Drag it into your Applications folder.

#### Step 3: Install C/C++ Extension for Visual Studio Code

- Open Visual Studio Code.
- Go to the **Extensions** view (click on the square icon on the sidebar).
- Search for **C/C++** and install the extension by Microsoft.

---

### Setting Up on Linux

Most Linux distributions come with the GNU Compiler Collection (**GCC**) pre-installed.

#### Step 1: Install the compiler if not already installed

- **For Debian/Ubuntu-based Systems**:

  ```bash
  sudo apt update
  sudo apt install gcc g++
  ```

- **For Fedora**:

  ```bash
  sudo dnf update
  sudo dnf install gcc gcc-c++
  ```

- **For Arch Linux**:

  ```bash
  sudo pacman -Syu
  sudo pacman -S gcc
  ```

**Important Note:** Updating is not required but recommended. For **Arch users** though, while I am sure you already know this, always be careful when updating your system. Ensure you have backups. If ever you see an important update in your update list (e.g. Kernel, wayland, xorg, systemd, etc.), please be sure to check the following places to ensure that it is safe to update:
- [Arch Wiki Home page](https://archlinux.org/)
- [Arch Wiki Forums](https://bbs.archlinux.org/)
- [Arch Subreddit](https://www.reddit.com/r/archlinux/)
- [Arch Community Discord Server](https://discord.gg/archlinux)

#### Step 2: Verify Compiler Installation

```bash
g++ --version
```

- You should see the version information for `g++`.

#### Step 3: Install a Code Editor or IDE

1. Install [Flatpak](https://flathub.org/setup) for your system
2. Download [Visual Studio Code Flatpak](https://flathub.org/apps/com.visualstudio.code). You may also choose [Vscodium](https://flathub.org/apps/com.vscodium.codium) if you want a 100% open source version of VSCode, just note that there are fewer extensions in VSCodium. 
3. You should find it in your app launcher now

**Note:** VSCode and VSCodium are both apps based on electron. You may face difficulty using them normally if your using Wayland/Xwayland instead of Xorg. If you do encounter problems, please ping `Nelson` in the Algo++ Discord Server. 

#### Step 4: Install C/C++ Extension for Visual Studio Code

- Open Visual Studio Code.
- Go to the **Extensions** view.
- Search for **C/C++** and install the extension.

---

### Text Editors and IDEs

If ever you wish to try out other IDEs or Text Editors, here are some recommendations!

- **Text Editors**:

  - **Visual Studio Code**: Lightweight, extensible, and supports multiple languages.
  - **Sublime Text**: Fast and customizable.
  - **Vim/Neovim**: Highly efficient once mastered, great for those who prefer keyboard-only navigation.

- **IDEs**:

  - **Eclipse CDT**: Offers robust features and plugins.
  - **CLion**: Advanced features like code analysis and refactoring tools.
  - **NetBeans**: Supports multiple languages, including C++.
  - **Visual Studio Community Edition** (Windows only): Comprehensive suite for development.

---

### Compilers

A compiler translates your C++ code into executable programs. The most commonly used C++ compilers are:

- **GCC (GNU Compiler Collection)**:
  - Available on Linux and via MinGW-w64 on Windows.
  - Command to compile: `g++ program.cpp -o program`

- **Clang**:
  - Default on macOS, also available on Linux and Windows.
  - Known for faster compilation times and better error messages.

---

## Getting Started with C++

With your environment set up, it's time to write your first C++ programs!

### Writing Your First Program: Hello World

The classic "Hello, World!" program is a simple way to verify that your compiler and editor are working correctly.

**Step 1: Create a New File**

- Open your code editor.
- Create a new file and save it as `hello_world.cpp`.

**Step 2: Write the Code**

```cpp
#include <iostream>

int main() {
    std::cout << "Hello, World!" << std::endl;
    return 0;
}
```

**Step 3: Compile the Program**

- Open your terminal or command prompt.
- Navigate to the directory containing `hello_world.cpp`.
- Compile the program:

  ```bash
  g++ hello_world.cpp -o hello_world
  ```

  - `g++` is the compiler command.
  - `hello_world.cpp` is your source file.
  - `-o hello_world` specifies the output executable name.

**Step 4: Run the Program**

- In the terminal, execute:

  - On Windows:

    ```bash
    hello_world.exe
    ```

  - On macOS/Linux:

    ```bash
    ./hello_world
    ```

**Expected Output**:

```
Hello, World!
```

**Troubleshooting Tips**:

- If you receive a "command not found" error, ensure your compiler is correctly installed and added to your system's PATH.
- Double-check the code for typos, especially semicolons and include statements.

---

## Brief Introduction to Competitive Programming

Competitive programming is a mind sport where participants write programs to solve well-defined problems within time and memory constraints. It's an excellent way to improve your algorithmic thinking and coding skills.

### What is Competitive Programming?

- **Problem-Solving**: Tackle algorithmic challenges that test logic, mathematics, and coding proficiency.
- **Time Constraints**: Solutions must be efficient to execute within given time limits.
- **Memory Constraints**: Programs must use memory efficiently.
- **Online Judges**: Platforms that automatically compile and run your code against test cases.

### Why Engage in Competitive Programming?

- **Enhance Coding Skills**: Writing efficient and optimized code becomes second nature.
- **Learn Algorithms and Data Structures**: Gain in-depth knowledge of essential concepts.
- **Problem-Solving Under Pressure**: Improves performance in high-stress situations.
- **Community and Recognition**: Join a global community, participate in contests, and earn rankings.

### Popular Competitive Programming Platforms

- **HackerRank**: [www.hackerrank.com](https://www.hackerrank.com/)
- **Codeforces**: [www.codeforces.com](https://codeforces.com/)
- **LeetCode**: [www.leetcode.com](https://leetcode.com/)
- **AtCoder**: [atcoder.jp](https://atcoder.jp/)
- **Kattis**: [open.kattis.com](https://open.kattis.com/)

### Getting Started

1. **Choose a Platform**: Start with beginner-friendly platforms like HackerRank or LeetCode.

2. **Understand the Problem Statement**:

   - Read carefully to understand the requirements.
   - Note input and output formats.

3. **Plan Your Approach**:

   - Identify the type of problem (e.g., sorting, dynamic programming).
   - Think about possible algorithms and data structures.

4. **Write and Test Your Code**:

   - Write code in your local environment first.
   - Test with sample inputs provided.

5. **Submit and Iterate**:

   - Submit your solution to the online judge.
   - If it fails, analyze the feedback and debug accordingly.

### Example Problem: Simple Addition

**Problem Statement**:

Write a program that takes two integers and outputs their sum.

**Sample Input**:

```
3 7
```

**Sample Output**:

```
10
```

**Solution in C++**:

```cpp
#include <iostream>

int main() {
    int a, b;
    std::cin >> a >> b; // Read two integers from input
    std::cout << a + b << std::endl; // Output their sum
    return 0;
}
```

### Tips for Success

- **Practice Regularly**: Consistency is key to improvement.
- **Learn from Others**: Read solutions and participate in discussions.
- **Study Algorithms and Data Structures**: Build a strong foundation.
- **Participate in Contests**: Apply your skills under time constraints.

---

## Additional Resources
This section offers useful links to relevant content. It's optional and meant to be extra material for further reading.(Note: Some resources might require you you to have access to the Algo++ Google drive in order to view it.)
- [UP Algo++ Intro to Programming and Setting Things Up Lecture Slides](https://docs.google.com/presentation/d/1gi76ZAgk72WNhFAxkk6ybceheU_7G_9gF3UrnChkgZg/edit#slide=id.g164c8dcc09a_1_48)
- [UP Algo++ The How to's of Competitive Programming Lecture Slides](https://docs.google.com/presentation/d/1Vn6f3Wz8f-wkIHIxFq5DklzPtwnFXY-4hsWzHX0Nno4/edit#slide=id.g164c8dcc09a_1_48)
---

## Summary

In this section, we've:

- **Set Up the Programming Environment**: Installed the necessary tools and configured your system for C++ development on Windows, macOS, or Linux.

- **Written and Compiled Your First C++ Programs**: Created the classic "Hello, World!" program and experimented with basic input/output operations.

- **Explored Competitive Programming**: Gained an understanding of what competitive programming entails and how it can benefit your coding journey.

### Next Steps

- **Practice Coding**: Try writing more programs to solidify your understanding.

- **Join a Platform**: Sign up on a competitive programming site and solve beginner-level problems.

- **Stay Curious**: Continue exploring additional resources and learning new concepts.

Remember, programming is a skill honed over time with practice and perseverance. Don't hesitate to revisit topics, ask questions, and engage with the community. Happy coding!

---


