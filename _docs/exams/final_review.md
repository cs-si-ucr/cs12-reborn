---
title: Final Review
permalink: /docs/final_review/
---

###### Written by Josh Beto


## Inheritance / Polymorphism

Design and implement the following classes: `UCRPerson`, `UCRProfessor`, `UCRStudent`. **State any assumptions**

A `UCRPerson` has the following specifications:
`string`: name, id
`int`: age
`print()` - prints out according to this format:
```
Name: <name>, ID: <id>, Age: <age>
```
Provide any appropriate getters and setters.
<br>
A `UCRStudent` has an `int` year, (freshman, sophomore, junior, senior), and a list of classes they are taking. You can use a given `Course` class without implementing it. A `Course` has the grade received as well as the course number.
* A `UCRStudent` has a getter function to return the `Course` with the highest grade achieved.
* A `UCRStudent` also has a function to return if a student is in academic probation. A student is in academic probation when their gpa for that quarter is below a 2.0. 
* When a`UCRStudent` object calls `print()`, you should print in the following format followed by a newline - 
```
Status: Student, Year: <year>, Name: <name>, ID: <id>, Age: <age> 
```
Provide any appropriate getters and setters. The year must be printed out as freshman, sophomore, junior, or senior, **not** 1, 2, 3, or 4.

A `UCRProfessor` has a `string` department they are associated with and a list of courses they teach. When a `UCRProfessor` object calls `print()`, you should print in the following format followed by a newline - 
```
Status: Professor, Department: <department>, Name: <name>, ID: <id>, Age: <age>
```
Provide any appropriate getters and setters.


## Linked List

Given the following class definition of Node:

```cpp
class Node {
    private:
        int value;
        Node* next;
    public:
        getNext();
        setNext(Node* next);
        getValue();
        setValue(int value);
};
```

##### You have access to the following data structure: `map`
A `map` is a data structure that stores a `key` - `value` pair, meaning you give the `map` a key and it gives you a value corresponding to that key, similar to how you give a `vector` an index and the `vector` returns the value at that index.
You have the following `map` functions:
* `find(key)` - you pass in a key and it returns the `end()` if the key was not found.
* `[] operator` - you access or set a value into the designated key inside the `[]`

<br>
1. Implement the function `remove_duplicates(Node n)`. Do this in `O(n)` running time i.e. a single pass
2. Implement the member function `IntList::remove_all(int n)`. This function removes all nodes that have the given value `n`. You are allowed to use `head` and `tail` and must update them appropriately for this function only.
3. Print the linked list backwards using recursion, you are given `head` only
4. Implement the function `bool isCircular(Node n)` that detects whether or not a linked list is circular i.e. the last node points back to the first node. Do this in `O(n)` i.e. a single pass

## Recursion
1. Implement a recursive function that returns the index of a rotated sorted array's *pivot*. A pivot is the index of the largest element in the rotated sorted array i.e. 3 4 5 6 1 2 3, the pivot is index 3.
2. Implement a function that does binary search on a rotated sorted array. 


## Short Response
Is there any problems with this code? Explain why there is or is not any problems:

```cpp
void pop_front() {
    // Assume no tail, just head
    if (head == nullptr) return;
    delete head;
    head = head->next;
}
```

Explain any differences (if any) between these 3 functions

```cpp
void print(IntNode* head) {
    if (head == nullptr) {
        return;
    }
    print(head->next);
    cout << head->value << endl;
}

void print(IntNode* head) {
    if (head == nullptr) {
        return;
    }
    cout << head->value << endl;
    print(head->next);
}

void print(IntNode* head) {
    cout << head->value << endl;
    print(head->next);
}
```

What does this code print out?

```cpp
int a = 9;
int* b = &a;
*b = 20;
cout << a << endl; // what does this print out?
delete b;
```