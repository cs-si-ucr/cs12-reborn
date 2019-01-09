---
title: Final Review Session
permalink: /docs/review_session/
---

###### Written by Josh Beto


## Linked List - Remove Duplicates

Given the following class definition of Node:

```cpp
class Node {
    public:
        int data;
        Node* next;
};
```

##### You have access to the following data structure: `map`
A `map` is a data structure that stores a `key` - `value` pair, meaning you give the `map` a key and it gives you a value corresponding to that key, similar to how you give a `vector` an index and the `vector` returns the value at that index.
You have the following `map` functions:
* `find(key)` - you pass in a key and it returns the `end()` if the key was not found.
* `[] operator` - you access or set a value into the designated key inside the `[]`

To remove duplicates in a linked list with a single pass (single for loop), consider how we can use a `map`. If we use the `map` to store values that we have already seen as keys, we can check duplicates very easily!
```cpp
void remove_duplicates(Node* n) {
    map <int, bool> m; // map that stores the data value seen (key) and whether it's been seen before (value).
    Node* prev = head;
    while (n != null) {
        if (m.find(n->data) != m.end()) { // If we found a duplicate
            prev->next = n->next;
            delete n;
            n = prev->next;
        }
        else {
            m[n->data] = true; // Stores whether or not we've seen this data value
            prev = n; // updates the previous to follow behind n
            n = n->next; // iterates through the linked list
        }
    }
}
```
Let's step through the code. 
* Our while loop iterates through the linked list. In our first if statement, we check if the current node is a duplicate by checking through our map. 
* If the map has the value, meaning we've seen this value before previously, it will return an iterator that does not point to the end of the list, != m.end().
*  Once we have found this duplicate, we delete it with the usual methods. 
*  Else, if this value has not been seen in our map, we should add this key to our map to essentially 'save' that value as seen for our future loop iterations. 
<br>


## Recursion - Rotated Sorted Array
 

https://www.geeksforgeeks.org/search-an-element-in-a-sorted-and-pivoted-array/

 Let's consider the following problem: Searching for an element in a rotated sorted array. First, let's define what a rotated sorted array is:
 ```cpp
[3 4 5 1 2 3]
 ```
 This is an example of a rotated sorted array, you can think of a rotated sorted array as essentially *shifting* the array to the left or right. 
 
 There is one major consideration in this problem: A rotated sorted array is essentially **two** sorted arrays that are next to each other. If we do *binary search* on both of these sorted individual arrays, we can come up with the answer! This leaves one issue however, how do we find the *pivot*, or when one sorted array ends and when the next begins.
 
To find the pivot point, we can *scan* through all the elements in a for loop and find when the current value is greater than the next value. This would run in O(n) time however and would not be efficient. To get around this, we can do a variation of *binary search* to find the pivot:
```cpp 
/* Function to get pivot. For array 3, 4, 5, 6, 1, 2 
   it returns 3 (index of 6) */
int findPivot(int arr[], int low, int high) 
{ 
  // base cases 
  if (high < low) return -1; 
  if (high == low) return low; 
  
   int mid = (low + high)/2; /*low + (high - low)/2;*/
   if (mid < high && arr[mid] > arr[mid + 1]) 
    return mid; 
      
   if (mid > low && arr[mid] < arr[mid - 1]) 
    return (mid-1); 
      
   if (arr[low] >= arr[mid]) 
    return findPivot(arr, low, mid-1); 
      
   return findPivot(arr, mid + 1, high); 
} 
```
Let's go through the code:
* Base Case: `high < low` - that means this is an invalid array and we should return -1.
* Base Case: `high == low` - meaning we are looking at an array with one element, return that index as the pivot
* Check if the mid value or the value before mid is the *pivot*. If so, return that index
* Else - recurse on the left half or right half respectively. 

Once we have the pivot with this binary search variation, we simply perform *binary search* on both sorted arrays. The code for this is as follows:
```cpp
/* Standard Binary Search function*/
int binarySearch(int arr[], int low,  
                  int high, int key) 
{ 
  if (high < low) 
    return -1; 
      
  int mid = (low + high)/2; /*low + (high - low)/2;*/
  if (key == arr[mid]) 
    return mid; 
      
  if (key > arr[mid]) 
    return binarySearch(arr, (mid + 1), high, key); 
      
  // else 
    return binarySearch(arr, low, (mid -1), key); 
} 
  
/* Function to get pivot. For array 3, 4, 5, 6, 1, 2 
   it returns 3 (index of 6) */
int findPivot(int arr[], int low, int high) 
{ 
  // base cases 
  if (high < low) return -1; 
  if (high == low) return low; 
  
   int mid = (low + high)/2; /*low + (high - low)/2;*/
   if (mid < high && arr[mid] > arr[mid + 1]) 
    return mid; 
      
   if (mid > low && arr[mid] < arr[mid - 1]) 
    return (mid-1); 
      
   if (arr[low] >= arr[mid]) 
    return findPivot(arr, low, mid-1); 
      
   return findPivot(arr, mid + 1, high); 
} 
  
/* Searches an element key in a pivoted 
   sorted array arr[] of size n */
int pivotedBinarySearch(int arr[], int n, int key) 
{ 
  int pivot = findPivot(arr, 0, n-1); 
  
  // If we didn't find a pivot,  
  // then array is not rotated at all 
  if (pivot == -1) 
    return binarySearch(arr, 0, n-1, key); 
  
  // If we found a pivot, then first compare with pivot 
  // and then search in two subarrays around pivot 
  if (arr[pivot] == key) 
    return pivot; 
      
  if (arr[0] <= key) 
    return binarySearch(arr, 0, pivot-1, key); 
      
    return binarySearch(arr, pivot+1, n-1, key); 
} 
```

* **Note:** To better understand recursion, visit week 8: 
  https://cs-si-ucr.github.io/CS12_Fall_2018/docs/week8/


## Inheritance / Polymorphism

* Polymorphism - A way to **generalize** different types of objects as a single kind of object. How this works:

```cpp
class Animal {
    virtual void print() = 0;
};

class Dog : public Animal {
    print() {
        cout << "Woof" << endl;
    };
};

class Cat : public Animal {
    print() {
        cout << "Meow" << endl;
    };
};
```

If we call print() on different `Animal` objects, each call will evaluate during *runtime*. 
* `protected` - derived classes can access these types of variables.
