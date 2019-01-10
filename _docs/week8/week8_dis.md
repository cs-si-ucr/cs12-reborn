---
title: Week 8 Discussion
permalink: /docs/week8/
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

## Selection Sort

Selection sort is a sorting algorithm that sorts a collection by scanning for minimum values. You can find out more about selection sort here: https://www.tutorialspoint.com/data_structures_algorithms/selection_sort_algorithm.htm

A key component of selection sort is finding the minimum value of a node to the end of the list.

Given a linked list:
* 2 -> 1 -> 5 -> 4 -> 3
* Find the minimum from the node with value 5 until the end of the list: {5 -> 4 -> 3}

To solve this problem, we need another function called `min(IntNode* h)` that finds the minimum value from the `IntNode* h` onwards. This function should keep going until the end of the list and keep track of a `int  &` reference to the **minimum** value found in the node. We need to keep track of a reference to be able to swap out the value with the current node. We swap values instead of shifting the node pointers themselves since it is more efficient for the `int` data type.

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

## Recursion vs. Iteration

Until now, you have been implementing your looping functions with *iterative* loop structures such as `for` and `while`. 
Recursion is an alternative to using a `for` or `while` loop by having a function *call itself*. 
<br><br>
There are two main components to recursion:
* Base case (when the recursion ends)
* Using *sub-problems* to answer the main problem
```cpp
int fibonacci(int n) {
    // Base case
    if (n <= 1) {
        return n;
    }
    // Recursive step
    // fibonacci(n-1) and fibonacci(n-2) are sub-problems
    return fibonacci(n-1) + fibonacci(n-2); // we use these subproblems to answer the main problem
}
```
Recursion uses *sub-problems*, which are smaller versions of the same problem to come up with the answer to the main problem. As an example, if we are interested in `fibonacci(5)`, the answer to `fibonacci(5)` is the sum of the *sub-problems* `fibonacci(3)` and `fibonacci(4)`. When we program recursively, we are only concerned with how to use these *sub-problems* and when the recursion ends, the *base case*.

## Recursion is Magic

One key tip to start programming recursively is to *stop tracing the function calls*. **You will wrap yourself in a loop trying to trace each recursive call**. Instead, follow the following steps:

1. Define what your recursive function does. How it does it is **magic** that you shouldn't worry about.
2. Define your *base cases*, the simplest examples you can think of
3. Build up from your *base case*. Think about the next simplest case after the *base case* and use the *base case* to come up with your answer. This will help you realize how to use *sub-problems* to answer the main problem.

**Note:** You can have **multiple** *base cases*, be sure to think of all the simplest cases!

Let's go over a simple example of how we can try coding recursively with the following function: 
<br>
`bool isPalindrome(const string &s)`

1. **Define what the function does:**
<br>
`bool isPalindrome(const string &s)` - This function returns `true` if the passed in `const string &s` is a palindrome.

2. **Define the base cases:**
<br>
Our *base cases* are the *empty* `string` and a `string` with 1 character. In both *base cases*, they are considered palindromes.
```cpp
bool isPalindrome(const string &s) {
    // base case
    if (s.size() <= 1) {
        return true;
    }
}
```
3. **Build up from the base case:**
<br>
Our next simplest cases are strings of length 2 and 3 respectively. For a `string` of lengh 2, you can think of it as such: `string: a {} b`, where `a` and `b` represent two characters appended to the *empty* `string`. We can think of a `string` of length 3 similarly: `string: a {c} b`, where c is our *base case* of a single character. In each case, we are *adding* on a characters to both sides of the base case. If the inner string, our *sub-problem*, is a palindrome and our outer two characters `a` and `b` are the same, we have a palindrome!

```cpp
bool isPalindrome(const string &s) {
    // base case
    if (s.size() <= 1) {
        return true;
    }
    /*
        if the inner string is a palindrome and the outer two characters
        are the same, we have a palindrome!
    */
    return s.front() == s.back() && isPalindrome(s.substr(1, s.size() - 2));
}
```
## Binary Search

As a quick aside, we will be lightly covering *binary search*. To understand what binary search is, let's give you an example: 
<br><br>
`vector<int> v = {1, 2, 3, 4, 5}`. 
<br><br>
I want you to tell me if the value 5 exists in our `vector<int> v`. You could just scan through all the elements and test if any of the elements equal 5. However, you could do this much faster by using *binary search*. A key property of this vector is that it is already **sorted**. If you test the **midpoint** of `v`, you can reduce your search space by *half* each time. Let's run through an example. 
<br><br>
1. Test the midpoint of our vector - it's 3.
2. Since our value 5 is higher than 3 and the vector is already **sorted**, we only need to search the right half of the vector.
3. Now we test the midpoint of the right half, 4. 4 is less than 5, so we test the right side of 4.
4. Since there is only 1 element on the right side of 4, we check it and it's 5. Our algorithm returns true.

Notice how in our example, we performed our search **recursively**. After we evaluated the midpoint, we recursed on the left or right half of that mid-point depending on the comparison. Our base cases are when the mid-point is equal to our value **or** we've run out of elements to check - the value doesn't exist in our vector.

## Practice

Recursion is an incredibly hard topic to understand without practice, but is essential for later data structure courses such as `CS014` and `CS141`. The only way to get better with recursion is to practice! Below are practice problems categorized by difficulty.

### **Easy**
```cpp
// returns the minimum value inside the vector<int> v
int findMin(const vector<int> &v);

// calculates the factorial of a given n, factorial(3) = 3 * 2 * 1
int factorial(int n);

// reverses the contents of a vector, v = {1, 2, 3} - after reverse: v = {3, 2, 1}
void reverseVector(vector<int> &v);
```
### **Medium**
```cpp
// Returns true if you can find the value inside the vector. The vector is SORTED
// Your algorithm MUST NOT scan through all the elements.
bool binarySearch(const vector<int> &v, unsigned start, unsigned end, int value);

// sorts the linked list recursively using selection sort
void selectionSort(IntNode* head)
```
### **Hard**
```cpp
/*
    returns all subsets of a vector v

    Example: getSubsets(v) // v = {1, 2, 3}
    getSubsets should return a vector of sets:
    {1}
    {2}
    {3}
    {1, 2}
    {1, 3}
    {2, 3}
    {1, 2, 3}
*/
vector<vector<int>> getSubsets(const vector<int> &v);

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