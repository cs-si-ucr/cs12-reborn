---
title: Week 1 Lab
permalink: /docs/lab1/
---

###### Written by John Pham

## CS10 Review

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

  // we clearly know what's going on here
  printVector(items);

  // we have to read these 4 lines to figure out what's going on
  for (auto index : items) {
    cout << index << " ";
  }
  cout << endl;

  return 0;
}
```

### Testing

As programmers, we need to strive to writing correct code. This means our code should work properly for any set of inputs.

* Asserts
  * `#include <cassert>`
    * Need to include `cassert` to use the `assert` function
  * `assert(func(a, b) == c)`
    * This will test whether the output of `func(a, b)` equals `c`.

```cpp
#include <iostream>
#include <math>
using namespace std;

int pow(int a, int b) {
  return pow(a, b);
}
int main() {
  assert(pow(2, 2) == 4);
  assert(pow(2, 3) == 8);
  assert(pow(3, 3) == 10); // this will throw an error

  return 0;
}
```

### Pass by value vs. pass by reference

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

### Function Overloading

Function overloading allows us to create functions that share the same name but accept different argument types

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

void printVector(const vector<string>& v) {
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

  return 0;
}
```

## Week 1 Lab Exercises

1. Write a function that swaps the value in 2 variables
2. Write a function that reverses a string
3. Write a function that performs bubble sort
