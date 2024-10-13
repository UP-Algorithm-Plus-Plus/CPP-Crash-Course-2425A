# C++ Crash Course Week 1 Part 2 ~ Coding Environment Setup & Competitive Programming Introduction

## Introduction

Welcome to **Week 1 Part 2** of the C++ Crash Course! Before diving deep into coding, it's essential to have a properly configured programming environment. This ensures that you can write, compile, and debug your C++ programs efficiently. Additionally, we'll introduce you to the exciting world of **competitive programming**, a domain where programmers tackle algorithmic problems under time constraints, enhancing both their coding skills and problem-solving abilities.

By the end of this section, you'll have:

- A fully functional C++ programming environment on your machine.
- Written and executed your first C++ program.
- Gained insight into competitive programming and how it can accelerate your learning.

<br>


## Programming Environment Setup

Setting up a programming environment involves installing a code editor or Integrated Development Environment (IDE), along with the necessary compilers and tools to write and run your programs. We'll guide you through the process for **Windows**, **macOS**, and **Linux** platforms.

<br>


### Setting Up on Windows
#### Step 1: Install a Code Editor or IDE

For beginners, **Visual Studio Code** is highly recommended due to its simplicity and extensive plugin ecosystem.

- **To install it:**
  - Download from [Visual Studio Code Website](https://code.visualstudio.com/).
  - Run the installer and follow the prompts.

#### Step 2: Install a C++ Compiler

To compile C++ code on Windows (or translate C++ code to a language your computer would understand on Winows), you'll need to install the **MinGW-w64** compiler

##### Installing MinGW-w64

**Note** If you prefer a video guide, you can watch [this](https://youtu.be/oC69vlWofJQ?si=a0AU2jNLOmpdxHvc)

1. **Download MSYS2**:
   - Go to the [MSYS2 Website](https://www.msys2.org/) and download the installer.

2. **Install MSYS2**:
   - Run the installer and follow the instructions.
   - Open the MSYS2 terminal from the Start menu.(Or use the MSYS terminal that appears)

3. **Update Package Database**:

   ```bash
   pacman -Syu
   ```

   - Close and reopen the terminal after the update.

4. **Install MinGW-w64 Compiler**:

   ```bash
   pacman -S --needed base-devel mingw-w64-ucrt-x86_64-toolchain 
   ```

   When prompted, press enter to accept the default number of packages then type Y when prompted then enter again.

5. **Add to System Path**:
  
  - Via the start menu, search for `Edit environment variables for your account` then click on it. 
  - After that, click on path environment variable then press edit
  - Under the environment variable, click new and then browse
  - Add `C:\msys64\ucrt64\bin` to your system's PATH environment variable. This lets you use the latest C++ compiler.

6. **Verify Installation**:
   Open up a command prompt and type
   
   ```bash
   gcc --version
   ```

   - You should see the version information of `gcc`.

<br>


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

<br>

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

<br>


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

<br>


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

<br>

## Brief Introduction to Competitive Programming

Competitive programming is a mind sport where participants write programs to solve well-defined problems within time and memory constraints. It's an excellent way to improve your algorithmic thinking and coding skills.

<br>

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
- **Online Judge**: [onlinejudge.org](https://onlinejudge.org/)

### Tips for Success

- **Practice Regularly**: Consistency is key to improvement.
- **Learn from Others**: Read solutions and participate in discussions.
- **Study Algorithms and Data Structures**: Build a strong foundation.
- **Participate in Contests**: Apply your skills under time constraints.

<br>


## Additional Resources
This section offers useful links to relevant content. It's optional and meant to be extra material for further reading.(Note: Some resources might require you you to have access to the Algo++ Google drive in order to view it.)
- [UP Algo++ Intro to Programming and Setting Things Up Lecture Slides](https://docs.google.com/presentation/d/1gi76ZAgk72WNhFAxkk6ybceheU_7G_9gF3UrnChkgZg/edit#slide=id.g164c8dcc09a_1_48)
- [UP Algo++ The How to's of Competitive Programming Lecture Slides](https://docs.google.com/presentation/d/1Vn6f3Wz8f-wkIHIxFq5DklzPtwnFXY-4hsWzHX0Nno4/edit#slide=id.g164c8dcc09a_1_48)

<br>


## Summary

In this section, we've:

- **Set Up the Programming Environment**: Installed the necessary tools and configured your system for C++ development on Windows, macOS, or Linux.

- **Written and Compiled Your First C++ Programs**: Created the classic "Hello, World!" program and experimented with basic input/output operations.

- **Explored Competitive Programming**: Gained an understanding of what competitive programming entails and how it can benefit your coding journey.


<br><br>

Click [here](https://github.com/UP-Algorithm-Plus-Plus/CPP-Crash-Course-2425A/blob/main/Week_1/Part3.md) to move on to the next part!