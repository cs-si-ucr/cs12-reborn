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