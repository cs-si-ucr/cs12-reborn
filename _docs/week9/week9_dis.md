---
title: Week 9 Discussion
permalink: /docs/week9_dis/
---

###### Written by Josh Beto

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

## Practice

Recursion is an incredibly hard topic to understand without practice, but is essential for later data structure courses such as `CS014` and `CS141`. The only way to get better with recursion is to practice! Below are practice problems categorized by difficulty.

```cpp
// returns the minimum value inside the vector<int> v
int findMin(const vector<int> &v);

// returns true if the string is a palindrome
string isPalindrome(const string &s);

// reverses the contents of a vector, v = {1, 2, 3} - after reverse: v = {3, 2, 1}
void reverseVector(vector<int> &v);

// computes factorial
int factorial(int n);

// print a linked list backwards
void printBackwards(Node* curr);

// print a linked list forwards
void printForwards(Node* curr);
```

### Challenge
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

// Returns true if you can find the value inside the vector. The vector is SORTED
// Your algorithm MUST NOT scan through all the elements.
bool binarySearch(const vector<int> &v, unsigned start, unsigned end, int value);
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