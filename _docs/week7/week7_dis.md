---
title: Week 7 Discussion
permalink: /docs/week7/
---

###### Written by Josh Beto

# Lesson Plan

This week we'll be covering an introduction to the zyBooks program, `IntVector`

## Stack vs. Heap

Until now, you never had to worry about memory management since all your memory was allocated to the *stack*. 
```cpp
int main() {
    int x = 5; // 'x' is allocated on the stack
}
```
The heap comes into play when *you*, the programmer allocate the memory yourself. This also means that you are responsible for cleaning up that data, or deleting it.
To delete this data, you simply call delete on the pointer. This **DOES NOT** delete the pointer itself, but the memory *referenced* by the pointer.
```cpp
int main() {
    int* p = new int[6]; // allocates an array of size 6 on the heap, you have to delete this later on
}
```
<br>
**Warm-Up:** Identify whether the memory goes on the stack or heap

```cpp
Rectangle* r = new Rectangle(4, 3);
```

```cpp
ExampleObject* g(4, 3);
```

```cpp
    int x = 6;
    int* g = &x
```


## Pointers as Arrays

Under the hood, arrays are implemented as pointers! The `[]` operator does pointer arithmetic followed by a dereference.

```cpp
int main() {
    int a[5]; // array with 5 values
    a[3] = 2; // sets the value at index 3 to 2
    *(a + 3) = 2; // does the same thing as the line above!
}
```
Your *array* object is really just a pointer that points to the *first element* of the array. When you do the `[]` operator,
you really just add memory address offsets until you get to the element you want. From there, you call the `*`, dereference operator
to actually grab the value at that index. Likewise, you can use the `[]` operator on a pointer returned from new!

```cpp
int main() {
    int* a = new int[5];
    a[3] = 2; // adds 3 memory addresses to the pointer, then dereferences it
    *(a+3) = 2; // see above
}
```

## `expand` function

Internally, your IntVector class is composed of a raw array. Whenever you need to increase the size of this array if it runs out of capacity,
you can simply allocate a new array of a bigger size and copy the values over. This is known as *expanding*.

Process:
1. Create a new array of the required size
2. Copy the values from the old *data* to this new array
3. Delete the old array (No memory leaks!)
4. Set the data pointer to the new array

This process will effectively construct an array of a greater capacity that still holds all your previous elements.

## `pop_back` / `clear`

Look back at last weeks' logical deletion section. Again, you don't need to actually delete the elements, you simply need to make them inaccessible by setting the `sz`.
The rest of your functions will implement this *contract*, ensuring no indicies >= `sz` will ever be accessed by the user

## `push_back` / `resize` / `assign` / `insert`

Process:
1. Check if the indice given is even valid. If not, throw an error
2. Check if the vector needs to be expanded, if so, call `expand()` or `expand(unsigned amt)` respectively
3. *Shift* the values over to their correct positions. If you insert an element at the *beginning* of the array, all the elements need to be shifted one to the right.
4. Assign the index to the given value of that function

## Common Pitfalls

* Comparing (2 * cap) > (cap - sz), think about the logistics of what you are actually comparing. The first element represents a total capacity while the second ...
* using `delete` does **NOT DELETE THE POINTER**, it delete's the *data* the pointer is pointing to!
* use *logical deletion*, you don't have to actually delete the element, you just need to make it inaccessible
* check your `for` loops, chances are the starting index or ending index is wrong!
* don't forget that `unsigned` can never be < 0!
