# C++ Crash Course Week 2 Part 1 - Time Complexity

#### Outline

- [Outline](#outline)
- [Why learn Time Complexity?](#why-learn-time-complexity)
- [Basics](#basics)
  - [Big-O Notation](#big-o-notation)
  - [The Rules](#the-rules)
  - [Common Time Complexities](#common-time-complexities)
  - [The Magic Number](#the-magic-number)
- [Summary](#summary)
 
## Why learn time complexity?

The main motivation in learning time complexity is to know if a program **will not timeout given the constraints of a problem beforehand**.

Your Big-O notation must be less than the [Magic Number](#the-magic-number). 

## Basics

### Big-O Notation

The Big-O notation or the **worst-case time complexity**, denoted as `O()`, describes how a program will be affected as the **input grows larger**.

Let us consider the following program.

```cpp
int main(){
    int n; cin>>n;

    // occurs at constant time regardless of n
    int a = 4*n; 

    // will run longer with larger n
    for(int i=0; i<n; i++)
        cout<<i;

    return 0;
}
```

Notice that the for-loop will run for longer as `n` increases. Big-O notations can be thought of as the *performance* of your code. The Big-O notation helps us describe our code mathematically.

### The Rules

Let's start with the basics.

1. All simple operations are of **constant time**.

    ```cpp
    int main(){
        int a = 0; // O(1)
        int b = 9; // O(1)

        int c = a + b // O(1)???
    }
    ```
    How about the line `int c = a + b`? It is therefore `O(2)`. It does addition AND assignment at the same time.
2. Loops are based on the **maximum runtime possible** or the **expected number of iterations**.

    ```cpp
    int main(){
        
        // O(n)
        for(int i=0; i<n; i++){
            cout<<i<<endl;
        }

        // O(m/2)
        for(int i=0; i<m; i+=2){
            cout<<i<<endl;
        }
    }
    ```
    
    If we don't use a loop and instead `cout<<i` n times, we would get `O(n)`. Because we don't know `n` beforehand, we place a variable inside our Big-O notation.
    
    How about the second loop? Why is it `O(m/2)`? This is because the increment is `i+=2`. If we try and process the loop, there will only be `m/2` operations. example, consider `m=10`.

    | iteration | i | notes |
    | --------- | - | ----- |
    | 1         | 0 | start |
    | 2         | 2 | `2<10`: continue loop |
    | 3         | 4 |`4<10`: continue loop |
    | 4         | 6 |`6<10`: continue loop |
    | 5         | 8 |`8<10`: continue loop |
    | 6         | 10 |`10<10`: false stop loop |

    It's not exactly `10/2` but close enough. (-.-')

    We can also do operations to our number of iterations. Consider the following loop.
    ```cpp
    // O(3n)
    for (int i=0; i<3*n; i++){
        cout<<i<<endl;
    }
    ```
    We expect it to run a total of `3n` iterations.

    >Okay, I actually lied to you. ¯\\\_(ツ)\_/¯. We actually need to add a constant to our notation because there's declaration of variables, checking of the statement, and update of our counter. But you will see in **Rule 5** that this doesn't matter much.

3.  Loops can also be **defined by functions**.

    Consider the following program
    ```cpp
    #include<bits/stdc++.h>

    using namespace std;

    int main(){
        int n; cin>>n;
        for(int i=0; i<pow(2,n); i++){
            cout<<i<<endl;
        }
        return 0;
    }
    ```
    `pow(2,n)` is a built-in function where we **raise 2 to the power of n**. Going back to the fundamentals, we basically just count the number of iterations. The loop will repeat a total of `2^n`, we just plug this in and we have `O(2^n)` as our Big-O notation.

    Consider the next example.

    *You should run this program on your own machine.*

    ```cpp
    #include<bits/stdc++.h>

    using namespace std;

    int main(){
        int n, ctr=1;
        cin>>n;
        for(int i=1; i<=n; i*=2){
            cout<<"iteration: "<<ctr;
            cout<<" | value: "<<i<<endl;
        }
        return 0;
    }
    ```

    Notice anything about the program?? It outputs all powers of two until `n`!

    How do we characterize it's Big-O notation?? (✿´‿`)

    We go back to the basics. The Big-O notation is just the number of iterations a loop. The loop iterates over all powers of two, so we just need to know **how many powers of two are there below `n`** or **how many times do I need to multiply two by itself to get to `n`**. $$O(x)\text{ where }2^x < n$$ We can use the `logarithm` function to get the value of $x$. The Big-O notation therefore is `O(log(n))`. Usually for loops where the counter is updated through a multiplication function it is of `O(log(n))`.

    >The next parts build upon the previous ideas. `(；一_一)`. You should have around 60% level of understanding of the previous topics before proceeding. You can also take a break right now!!

3. **Mix-and-Match!!**

    We can actually start mixing in these operations.

    ```cpp
    // O(3n*3)
    for (int i=0; i<3*n; i++){
        int a = i + 1;
        a = a*i;
        cout<<i<<endl;
    }

    // O(n^2)
    for(int i=0; i<n; i++){
        for(int j=0; j<n; j++){
            cout <<"hello"<<endl;
        }
    }
    
    // O(nlog(n))
    for(int i=0; i<n; i++){
        for(int j=1; j<n; j*=2){
            cout <<"hello"<<endl;
        }
    }

    // O(n^3 + n^2)
    for(int i=0; i<n; i++){ // loop a
        for(int j=0; j<n; j++){ // loop b
            for(int k=0; k<n; k++){ // loop c
                cout <<"hello"<<endl;
            }
        }
        for(int j=0; j<n; j++){//loop d
            cout <<"hello"<<endl;
        }
    }
    ```

    Let us consider the third example of `O(n^3 + n^2)`. Loop C and D have `n iterations`. Loop C is housed by Loop B, which iterates `n times`. Therefore, loop B prints `hello` `n*n` times or `n^2` times. Inside loop A, we then have `n^2 + n`. Because loop A repeats `n` times, we multiply `n^2 + n` to have `n^3 + n^2`. Worst-case here is `O(n^3 + n^2)`.

4. We can **factor out constants** and **keep the largest terms**.

    Because we just want to **know how our program scales with increasing input**, we can actually factor out constants inside the Big-O notation. Additionally, we can just keep the largest term for simplification.

    | Big-O Notation | Simplification |
    | -------------- | -------------- |
    | $O(1)$         | $O(1)$         |
    | $O(4)$         | $O(1)$         |
    | $O(n\log(n) +n)$  | $O(n\log(n))$ |
    | $O(52n)$       | $O(n)$         |
    | $O(n+100)$     | $O(n)$         |
    | $O(n^3 + n^2)$ | $O(n^3)$       |
    | $O(2^n + n^3)$ | $O(2^n)$       |

    > Okay?? But how do I know which one is larger??

    We can now which one is larger by solving the equations inside. One trick is also to just input a very large number, whoever is the biggest stays.

### Common Time Complexities

We have 6 common time complexities in programming.

| Name | Big-O | info |
| ---- | ----- | --- |
| Constant | $O(1)$ | for simple statements |
| Linear | $O(n)$ | for simple loops |
| Logarithmic | $O(n\log(n))$ | for loops with $\log (n)$ |
| Quadratic | $O(n^2)$ | for loops inside loops|
| Exponential | $O(2^n)$ | fibonacci numbers |
| Factorial | $O(n!)$ | permutations |

For purposes of competitive programming, you can simplify your program to any of these 6 time-complexities. It is arranged in increasing order, so the worst algorithms are in factorial time and the best are in constant time.

### The Magic Number

The magic number is `100,000,000`. It means when you evaluate the Big-O notation, it should be less than the magic number.

For example, let's say the constraints in the problem is that `n=5` then you can use any time-complexity including factorial time. But if `n=200000`, you are now limited to `O(nlog(n))` algorithms.

You can follow the cheatsheet below.

| Name | Big-O | Limit for $n$ |
| ---- | ----- | --- |
| Constant | $O(1)$ | any $n$ |
| Linear | $O(n)$ | $n\approx 100,000,000$ |
| Logarithmic | $O(n\log(n))$ | $n \approx 4,500,000$ |
| Quadratic | $O(n^2)$ | $n\approx 10,000$|
| Exponential | $O(2^n)$ | $n\approx 26$ |
| Factorial | $O(n!)$ | $n\approx 11$ |

Retrieved from https://www.dcc.fc.up.pt/~pribeiro/aulas/pc2122/material/bigo_table.html

## Summary

In this section, we've:

- **Learned what the Big-O notation is**: [The Big-O notation](#big-o-notation) is used to characterize the running time a program has.

- **Simplify the Big-O notation**: We basically need to get the dominating term then group it into one of the [6 time complexities](#common-time-complexities).

- **Apply Time Complexities in Competitive Programming**: We just need to make sure that when evaluated it is less than the [Magic Number](#the-magic-number)

<br>

Click [here](https://github.com/UP-Algorithm-Plus-Plus/CPP-Crash-Course-2425A/blob/main/Week_2/Part3.md) to move on to the next part!