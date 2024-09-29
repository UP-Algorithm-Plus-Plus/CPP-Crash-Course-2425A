```cpp
#include <iostream>

void testFunction(int* ptr) {
    int unusedVar;  // Unused variable, Cppcheck will flag this
    int uninitializedVar;  // Uninitialized variable, Cppcheck will flag its usage
    if (ptr) {
        *ptr = 42;  // This is safe since we check if ptr is not null
    }
    
    std::cout << uninitializedVar << std::endl;  // Using uninitialized variable, flagged by Cppcheck

    int* nullPtr = nullptr;
    *nullPtr = 100;  // Dereferencing a null pointer, Cppcheck will flag this
}

int main() {
    int* validPtr = new int;
    testFunction(validPtr);
    delete validPtr;
    return 0;
}
