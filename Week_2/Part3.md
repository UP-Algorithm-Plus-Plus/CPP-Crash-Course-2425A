# C++ Crash Course Week 2 Part 2 - Sorting Algorithms

#### Outline

- [Outline](#outline)
- [The Sorting Problem](#the-sorting-problem)
- [Basic Sorting Algorithms](#basic-sorting-algorithms)
  - [Bubble Sort](#bubble-sort)
  - [Merge Sort](#merge-sort)
  - [Quick Sort](#quick-sort)
  - [STL Sort](#stl-sorting-algorithm)
- [Exercises](#exercises)
- [Summary](#summary)
 
## The Sorting Problem

Sorting is a very basic application of programming. One could sort by number, alphabetically, or even a custom sorting protocol.

Sorting also shows us the importance of worst case time-complexities.

## Basic Sorting Algorithms

We will be looking at three sorting algorithms + the standard template library(STL) of C++.

To summarize the sorting algorithms.

| Sorting Algorithm | Pros | Cons |
| ----------------- | ---- | ---- |
| Bubble Sort       | Simple | Slow ass. `O(n^2)` |
| Merge Sort        | Fast `O(nlog(n))` | Takes up more space |
| Quick Sort        | Constant Space | Time complexity ranges from `O(nlog(n))` to `O(n^2)`|
| STL Sort | Easy to use and fast | Less editable |

You can also view their visualizations [here](https://visualgo.net/en/sorting).

### Bubble Sort

For bubble sort, think of it as taking each element then **moving it up** if the next element is smaller than the current one.

Here is the code.

```cpp
#include <iostream>
using namespace std;

void bubbleSort(int arr[], int n) {
    for (int i = 0; i < n - 1; i++) {
        // Last i elements are already in place
        for (int j = 0; j < n - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                // Swap arr[j] and arr[j + 1]
                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }
}

void printArray(int arr[], int size) {
    for (int i = 0; i < size; i++)
        cout << arr[i] << " ";
    cout << endl;
}

int main() {
    int arr[] = {64, 34, 25, 12, 22, 11, 90};
    int n = sizeof(arr)/sizeof(arr[0]);
    cout << "Unsorted array: ";
    printArray(arr, n);

    bubbleSort(arr, n);

    cout << "Sorted array: ";
    printArray(arr, n);

    return 0;
}

```

> Try and simulate bubble sort on your own!! Tip: try printing the state of the array after every loop.

### Merge Sort

The idea for merge sort is to divide the array into two halves and sort these individual halves. To sort these halves, we do merge sort again and again until we only have one element.

```cpp
#include <iostream>
using namespace std;

// Function to merge two halves of the array
void merge(int arr[], int left, int mid, int right) {
    int n1 = mid - left + 1;  // Size of the left subarray
    int n2 = right - mid;     // Size of the right subarray

    // Create temporary arrays
    int L[n1], R[n2];

    // Copy data to temporary arrays L[] and R[]
    for (int i = 0; i < n1; i++)
        L[i] = arr[left + i];
    for (int j = 0; j < n2; j++)
        R[j] = arr[mid + 1 + j];

    // Merge the temporary arrays back into arr[left..right]
    int i = 0; // Initial index of the first subarray
    int j = 0; // Initial index of the second subarray
    int k = left; // Initial index of the merged subarray

    while (i < n1 && j < n2) {
        if (L[i] <= R[j]) {
            arr[k] = L[i];
            i++;
        } else {
            arr[k] = R[j];
            j++;
        }
        k++;
    }

    // Copy the remaining elements of L[], if any
    while (i < n1) {
        arr[k] = L[i];
        i++;
        k++;
    }

    // Copy the remaining elements of R[], if any
    while (j < n2) {
        arr[k] = R[j];
        j++;
        k++;
    }
}

// Function that divides the array into two halves
void mergeSort(int arr[], int left, int right) {
    if (left < right) {
        int mid = left + (right - left) / 2;

        // Sort first and second halves
        mergeSort(arr, left, mid);
        mergeSort(arr, mid + 1, right);

        // Merge the sorted halves
        merge(arr, left, mid, right);
    }
}

// Function to print the array
void printArray(int arr[], int size) {
    for (int i = 0; i < size; i++)
        cout << arr[i] << " ";
    cout << endl;
}

int main() {
    int arr[] = {12, 11, 13, 5, 6, 7};
    int arr_size = sizeof(arr) / sizeof(arr[0]);

    cout << "Given array is: ";
    printArray(arr, arr_size);

    mergeSort(arr, 0, arr_size - 1);

    cout << "Sorted array is: ";
    printArray(arr, arr_size);
    
    return 0;
}
```

Consider a simple example of an array of 4 elements.

```cpp
x = {3,1,2,4};
```

We first partition the array into two parts.
```cpp
{3,1} and {2,4}
```
We can further divide the first half to
```cpp
{3} and {1}
```
Because we can't divide them more, we **merge them**. Merging is done by checking the **smallest in each array to check which to place first**.

We place 1 first then 3. We then have the combination.
```cpp
{1,3} and {2,4}
```
We then divide the `{2,4}` array then do the same operation.
```cpp
{2} and {4}
```
Because `2<4`, we store 2 first. So we then have,
```cpp
{1,3} and {2,4}
```

>(Umulit lang so bat mo pa ginawa,,, -> bc di tayo sure if sorted ba talaga siya, the computer doesn't know that)

We can then apply the **merging** to both halves.

```cpp
{1,3} and {2,4}
sorted = {}

check: 1 > 2

{3} and {2,4}
sorted = {1}

check: 3 < 2

{3} and {4}
sorted = {1,2}

check 3 > 4

{} and {4}
sorted = {1,2,3}

only one remains
sorted = {1,2,3,4}
```



### Quick Sort

In quick sort, we select an element $x$(a.k.a. pivot) in the array. Place all other elements less than $x$ to the left and elements greater than $x$ to the right.

```cpp
#include <iostream>
using namespace std;

// Function to swap two elements
void swap(int* a, int* b) {
    int t = *a;
    *a = *b;
    *b = t;
}

// Function to partition the array on the basis of pivot
int partition(int arr[], int low, int high) {
    int pivot = arr[high];  // Choosing the last element as pivot
    int i = (low - 1);  // Index of smaller element

    for (int j = low; j <= high - 1; j++) {
        // If current element is smaller than the pivot
        if (arr[j] < pivot) {
            i++;  // Increment index of smaller element
            swap(&arr[i], &arr[j]);
        }
    }
    // Swap the pivot element with the element at i+1
    swap(&arr[i + 1], &arr[high]);
    return (i + 1);
}

// Function implementing quicksort
void quickSort(int arr[], int low, int high) {
    if (low < high) {
        // Partition the array around pivot and get the pivot index
        int pi = partition(arr, low, high);

        // Recursively sort elements before and after partition
        quickSort(arr, low, pi - 1);
        quickSort(arr, pi + 1, high);
    }
}

// Function to print the array
void printArray(int arr[], int size) {
    for (int i = 0; i < size; i++)
        cout << arr[i] << " ";
    cout << endl;
}

int main() {
    int arr[] = {10, 7, 8, 9, 1, 5};
    int n = sizeof(arr) / sizeof(arr[0]);
    cout << "Unsorted array: ";
    printArray(arr, n);

    quickSort(arr, 0, n - 1);

    cout << "Sorted array: ";
    printArray(arr, n);
    return 0;
}

```

Let us walk through an example for the first iteration.

Consider the array.
```cpp
x = {10, 7, 8, 9, 1, 5}
```

We first call to `quickSort(arr, 0, 5)` low = 0 and high = 5, so we call `partition(arr, 0, 5)`.

The pivot element is `arr[5] = 5`.

Partitioning around pivot = 5. Start with i = -1 and iterate j from low (0) to high-1 (4).

  1. `j = 0`, `arr[j] = 10`. Since 10 > 5, no swap, and i remains -1.
  2. `j = 1`, `arr[j] = 7`. Since 7 > 5, no swap, and i remains -1.
  3. `j = 2`, `arr[j] = 8`. Since 8 > 5, no swap, and i remains -1.
  4. `j = 3`, `arr[j] = 9`. Since 9 > 5, no swap, and i remains -1.
  5. `j = 4`, `arr[j] = 1`. Since 1 < 5, increment i to 0 and swap `arr[i]` and `arr[j]`. 
  
The array becomes:
```cpp
x = {1, 7, 8, 9, 10, 5}
```

After the loop, swap the pivot `arr[5] = 5` with `arr[i+1] = arr[1] = 7`. The array becomes:
```cpp
x = {1, 5, 8, 9, 10, 7}
```

Notice that the array is not completely sorted, but with our chosen `pivot=5` all elements that are less than 5 are to the left and greater than 5 to the right.

We repeat the sorting on a segment not yet sorted.

### STL Sorting Algorithm

Even though learning how these algorithms work are useful so you know how they work and can manipulate them. Most of the time, you don't need to make these algorithms everytime you use them. We usually use the standard library.

The standard library has it's own sorting function.

```cpp
sort(begin, end, comparator);
```

Consider the simple example of sorting a vector.

```cpp
// Example 1: Sorting in descending order
std::vector<int> v = {3, 1, 4, 1, 5, 9};

// Using a custom comparator for ascending order
std::sort(v.begin(), v.end());
// Output: 1 1 3 4 5 9


// Using a custom comparator for descending order
std::sort(v.begin(), v.end(), std::greater<int>());
// Output: 9 5 4 3 1 1
```

One could also define a lambda function as the comparator.

```cpp
sort(x.begin(), x.end(), [](const int &a, const int &b) {
        if(a<b) return true;
        return false;
    });
```

We basically return the value of `True` if we want to sorting algorithm to treat `a<b`.

What if I want to sort the even and odd numbers separately and have the even numbers be treated as smaller.
```cpp
sort(x.begin(), x.end(), [](const int &a, const int &b) {
    if (a%2 == 0 and b%2 == 1) 
        return true;  // prioritize a if it is even
    
    if (a%2 == 1 and b%2 == 0) // prioritize b if even
        return false;

    return a < b;  // sort normally
});
```

## EXERCISE TIME !!!

- [ ] I have already given you the code for bubble, merge sort, and quick sort. Try creating your own bubble sort, merge sort, and quick sort but **sorting based on the length of the string**.
- [ ] Using the lambda functions for STL sorting algorithm. Sort a vector of integers such that **all multiple of `3` is treated as bigger**.
 - Example: `input: 1 2 3 4 5 6 7 8 9` `output: 1 2 4 5 7 8 3 6 9`
- [ ] Using the lambda functions for STL sorting algorithm. Sort a vector of integers such **even numbers are sorted in ascending** order and **odd numbers are sorted in descending order**, and **even numbers are treated smaller than odd numbers**.
 - Example: `input: 5 2 6 1 3 4` `output: 2 4 6 5 3 1`

You can send me the code on discord!!

## Summary

In this section, we've:

- **Learned the three sorting algorithms: bubble, merge, and quick sort** 

- **Learned how to use the STL sort**

- **(hopefully) Did the practice exercies**

<br>

>[!NOTE]
>Chat `Goodbye Rad!` at the discord server if you have reached this far!! 