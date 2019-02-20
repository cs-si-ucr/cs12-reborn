---
title: Week 7 Discussion
permalink: /docs/week7_dis/
---

###### Written by Josh Beto

# Lesson Plan

This week we'll be covering linked list and an introduction to recursion

**Note:** If you can't compile with `nullptr` in c++, that's because you're forgetting the `-std=c++11` flag when you compile i.e. `g++ main.cpp -std=c++11`.

## Linked List

A linked list is an alternative to a `vector`. Both fundamentally represent a *collection* of items or data, but their implementations are different. Linked lists represent their data as a series of *linked nodes*. A node is an object that has both *data* and a pointer that points to the *next node*.

```cpp
struct IntNode {
    int value; // the actual data
    IntNode* next; // a pointer to the next node
}
```
Typically, linked list have two node pointers, `head` and `tail`, which point to the first and last node in the list repsectively. To iterate through a linked list you can do a simple `for` loop insead of a `while` loop.

```cpp
// for loop option
for (IntNode* curr = head; curr != nullptr; curr = curr->next) {}

// while loop option
IntNode* curr = head;
while (curr != nullptr) {
    curr = curr->next;
}
```

## Cases
There are 3 main cases to worry about in any linked list implementation:
1. `head == nullptr` - The linked list is *empty*
2. `head == tail` - The linked list has *one* node
3. `head != tail` - The linked list has *more than one* node

**NOTE:** Keep in mind that the order you should check these cases should be *exactly* as presented in the steps. When the linked list is *empty*, `head == tail` is `true` since they both point to `nullptr`.p Check them in the order of steps provided!

`Case 1: head == nullptr:` 
* **Insertion:** You need to set *both* the `head` and `tail` pointer to point to the single node being inserted.
* **Deletion:** You can't delete from an empty linked list! Throw an error.

`Case 2: head == tail:` 
* **Insertion:** You need to set either the `head` or `tail` to the node being inserted depending on if you are *pre-pending* or *appending* the node. Set the node connections as usual.
* **Deletion:** Set `head` and `tail` to `nullptr`. Don't forget to delete the node!

`Case 3: head != tail:` 
* **Insertion:** Set the node connections as usual with the inserted node's neighbors. Depending on if you are inserting at the `head` or `tail`, set their respective pointers.
* **Deletion:** Set the node connections as usual. If you delete the `head` or `tail`, be sure to adjust the `head` or `tail` to point to the next or previous element respectively. Don't forget to delete the node!

## Exercises

```cpp
/*
Implement the following functions

You have access to the following private variables:
IntNode* head
IntNode* tail
*/

// Removes duplicate values from the linked list
void removeDuplicates();

// Deletes that specific node from the list. Assume the node always exist in the list
void deleteNode(IntNode* toDelete);

// Deletes the first node found with the same value as the argument given
void deleteNode(int value);

// Detects if the linked list is circular i.e. the last node points back to the first node
bool isCircular();
```

## Conceptual Questions

* What's the difference between the following code snippets?
```cpp
void print(IntNode* head) {
    if (head == nullptr) {
        return;
    }
    print(head->next);
    cout << head->value << endl;
}
```
```cpp
void print(IntNode* head) {
    if (head == nullptr) {
        return;
    }
    cout << head->value << endl;
    print(head->next);
}
```
```cpp
void print(IntNode* head) {
    cout << head->value << endl;
    print(head->next);
}
```