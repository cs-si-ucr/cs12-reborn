---
title: Week 4 Discussion
permalink: /docs/dis4/
---

###### Written by Josh Beto

## Intro

Pointers are *variables* that hold an address as its value. In many ways, pointers are similar to references. Just like any variable, pointers also have their own *type*. 
A pointer's type dictates what kind of objects or types that the pointer can reference.

```cpp
int* p = nullptr; // initializes pointer to reference nothing
int a = 1;
p = &a; // sets pointer p to reference a
cout << *p << endl; // dereferences pointer and prints out 1
```

**Note:** As best practice, *don't* leave a pointer uninitialized like so: `int* p;`, always initialize the pointer to reference another variable/object or `nullptr`!
Uninitialized pointers have *garbage* addresses and may cause `segmentation faults` if you try to dereference them.

## The `->` operator

It's common practice that you want to have a pointer point to some object. To access an object's *member functions / data*, you need to first dereference the pointer
to get the actual object, then do the `.` operator. This can become extremely tedious however, so a shortcut is using the `->` operator

```cpp
Rectangle a(6, 3); // initializes a 'Rectangle' object with length = 6 and width = 3
Rectangle* p = &a;
double area = (*p).getArea(); // dereference pointer p to get the Rectangle object 'a', then call a member function with the . operator
double area2 = p->getArea(); // same thing as above!
```

## New and Delete

The operator `new` allocates memory on the `heap` and returns to you a pointer that points to that alotted memory. This memory however, is not automatically deleted for you
when that pointer reaches the end of its scope or lifetime. To delete this memory and avoid *memory leaks*, call `delete` on a pointer that points to that memory to deallocate it.

```cpp
Rectangle* right = new Rectangle(6, 3); // creates a Rectangle object on the heap and returns a pointer to that memory address
delete right; // deallocates the Rectangle object on the heap and avoids memory leaks!

Rectangle* wrong = new Rectangle(6, 3);
Rectangle* corrected = wrong;
wrong = nullptr;
delete wrong; // This does NOT delete the memory at the heap. Calling 'delete' deletes the memory alotted in whatever the pointer *references*. In this case, it deletes nothing!
delete corrected; // This DOES delete the memory at the heap because 'corrected' *references* the Rectangle object's memory location.
```

**Note:** A key note is that calling `delete` isn't about deleting the exact same pointer that got returned by `new`. You have to call delete on a pointer that *references* the memory address returned by `new`. We call forever lost references as *memory leaks* because without the pointer to reference the memory, it becomes impossible to deallocate/delete that memory!

## Dangling Pointers

We call pointers that don't reference a properly allocated memory location a *dangling pointer*. Any attempts to dereference a dangling pointer may cause a `segmentation fault`.
```cpp
Rectangle* example = new Rectangle(6, 3); // creates a Rectangle object on the heap and returns a pointer to that memory address
delete example; // deallocates that memory location
double a = example->getArea(); // Example is a dangling pointer! Since you deallocated the memory that example pointed to, you may be accessing memory that doesn't belong to your program!
```

## Exercise: Identify any Errors

* Identify any errors (if there are errors)

Problem 1:
```cpp
Rectangle* a = new Rectangle(6, 2);
Rectangle* b = &a;
delete b;
double area = a->getArea();
```

Problem 2: 
```cpp
Rectangle* a;
double area = a->getArea();
```

Problem 3: 
```cpp
Rectangle* a;
a = &(Rectangle(6, 2));
double area = a->getArea();
```

Problem 4:
```cpp
Rectangle* a = new Rectangle(4, 5);
Rectangle* b = a;
*a = nullptr;
delete b;
```

Problem 5:
```cpp
int a = 9;
int* b = &a;
*b = 20;
cout << a << endl; // what does this print out?
delete b;
```

## Programming Activity

1. *Warm-up:* Create a function called `change` that takes in an `int* pointer` as an argument, and changes the *dereferenced* value of that pointer to 30.
2. Create a class called `Town` with the following specifications:
    * `vector<Town*> neighbors` - represents neighboring towns
    * `string townName` - town name
    * `Town(string name)` - constructor that takes in a town name
    * `void addNeighbor(const Town &t)` - adds the given town as a neighbor
    * `bool isNeighbor(string town)` - returns true if town given is a neighbor
    * `vector<string> getNeighborNames()` - returns a vector of the town's neighbors

## Conceptual Questions

1. Can you have a pointer to a pointer? If so, how do you create one?
2. If you make a pointer, `int* p = &a`, what is the value of `p` (Not dereferenced yet)?
3. *Challenge:* How does pointer arithmetic work (++, --) ?