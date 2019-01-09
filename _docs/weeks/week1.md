---
title: Week 1 Discussion
permalink: /docs/week1/
---

###### Written by John Pham
###### Modified by Josh Beto

## CS10 Review

### Types
* `double` - decimals
```cpp
double a = 3.3;
```
* `int` - integers
```cpp
int a = 3;
```
* `char` - a character ie. ASCII
```cpp
char a = 'a';
```
* `string` - string of characters
  * Don't forget `#include <string>` or `#include <iostream>`!
```cpp
string abc = "abc";
```

* Integer Division vs. Double Division Pitfall!
```cpp
#include <iostream>
using namespace std;

double a = 5 / 2; // WRONG: Performs integer division, then converts to double!
cout << a << endl; // prints 2
```

```cpp
#include <iostream>
using namespace std;

double a = 5 / 2.0; //CORRECT: Converts to double before division!
cout << a << endl; // prints 2.5
```

### Functions

* Improve readability
* Modularize your code/avoid writing redudant code

```cpp
#include <iostream>
#include <vector>
using namespace std;

void printVector(const vector<int>& v) {
    for (auto index : v) {
        cout << index << " ";
    }
    cout << endl;
}

int main() {
    vector<int> items = {1, 2, 3, 4, 5};

    // we clearly know what's going on here and can be reused as many times as needed
    printVector(items);

    // we have to read these 4 lines to figure out what's going on, must copy-paste to keep printing vector
    for (auto index : items) {
    cout << index << " ";
    }
    cout << endl;

    return 0;
}
```

### Vectors vs. Arrays

* Vectors
  * Variable size
  * Convenient functions available: `erase()`, `size()`, `push_back()`, `pop_back()`
  * Throws an exception if there is an out of range error using `at()`

* Arrays
  * Fixed size
  * Lack of convenience functions
  * Undefined behavior if there is an out of range error using `[]`

```cpp
#include <vector>
#include <iosteam>
using namespace std;

int main() {
    vector<int> v;
    v.push_back(2); // v is {1}
    v.push_back(5); // v is {2 5}
    v.push_back(1); // v is {2 5 1}

    // Common pitfall: pop_back() does not return a value!
    v.pop_back(); // v is {2 5}
    cout << v.at(2) << endl; // Throws an exception!

    int a[5]; // a is an array of size 5
    a[0] = 3;
    a[5] = 1; // Undefined behavior! Program may or may not crash

  return 0;
}
```

### Pass by Value vs. Pass by Reference

These are 2 options for when you need to pass variables into functions

* Pass by value
  * The function creates a local variable with the same value
  * Uses time and memory to create a new variable
  * Changes to the local variable **do not** affect the original variable
* Pass by reference
  * The function creates a reference that points to the original variable
  * Does not use additional memory to create a copy
  * Changes to the referenced variable will apply to the original variable
    * You can prevent this by prefixing with `const`.

```cpp
#include <iostream>
using namespace std;

void passByValue(int x) {
    x = x + 1; // Copy of x is incremented, but then thrown away
}

void passByReference(int &x) {
    x = x + 1; // Reference to x is actually incremented
}

int main() {
    int variable = 0;

    passByValue(variable);
    cout << variable << endl; // prints '0'

    passByReference(variable);
    cout << variable << endl; // prints '1'

    return 0;
}

```


### Function Overloading

Function overloading allows us to create functions that share the same name but accept different argument types
and/or a different number of arguments

```cpp
#include <iostream>
#include <vector>
#include <string>
using namespace std;

void printVector(const vector<int>& v) {
    for (auto index : v) {
        cout << index << " ";
    }
    cout << endl;
}

// Different parameter type
void printVector(const vector<string>& v) {
    for (auto index : v) {
        cout << index << " ";
    }
    cout << endl;
}

// Different number of parameters
void printVector(const vector<string>& v, string title) {
    cout << title << endl;
    for (auto index : v) {
        cout << index << " ";
    }
    cout << endl;
}

int main() {
    vector<int> itemsA = {1, 2, 3, 4, 5};
    vector<string> itemsB = {"Foo", "Boo", "Bar"}

    printVector(itemsA);
    printVector(itemsB);
    printVector(itemsB, "Example");

    return 0;
}
```

## Exercises

1. Write a function that swaps the value in 2 variables
2. Write a function that reverses a vector
3. Write a function that checks if a string is a palindrome
