---
title: Week 6 Discussion
permalink: /docs/week6/
---

###### Written by Josh Beto

# Lesson Plan

This week we'll be covering arrays and introducing version control with `git`. 

## Arrays

Arrays are more limited compared to vectors and have the following features:
* Fixed size
* No error checking for `out_of_bounds`
* Less operations compared to vectors, such as `erase()` and `size()`

As a result, you have to manually keep track of the size of the array as well as be
extra careful when accessing array indices to make sure you are not going out of bounds.

```cpp
int main() {
    int a[5]; // array with 5 values
    int a[] = {1, 2, 3}; // array with 3 values
    int a[6] = {1, 2, 3}; // array with 6 values, the first 3 are 1, 2, 3. The remaining are filled with a default value.
    return 0;
}
```

When you pass an array as an argument, make sure you always pass the size of the array as well.
Otherwise, you may access the array out of bounds or your function may only work for one array size.
```cpp
int sum(int a[], a_size) {
    int sum = 0;
    for (int i = 0; i < a_size; i++) {
        sum += a.at(i);
    }
    return sum;
}
```

## Logical Delete

To *delete* an element from an array, you have to instead shift the values from the right of the removed index
to the left by one, and then decrement the total size by 1. This is known as a *logical delete* because you never
reallocate another array and copy the values over to the new array's size, but rather update the size so you know
what indicies are valid
