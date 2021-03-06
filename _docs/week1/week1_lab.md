---
title: Lab
permalink: /docs/week1_lab/
---

###### Written by Josh Beto

## Problem Solving Tips
* If you get stuck on a part, skip to the parts you know and *abstract* the parts you do not know. *Abstract* means to understand what something does, but not think about how it is done. 
* **Example:** You have a function ```bool isAcceptable(int x)```
* You need to remove elements within a ```vector<int> v``` that are considered not acceptable. 
* You can simply call ```isAcceptable(int x)``` to check for which elements to remove even if you do not know how to write ```bool isAcceptable(int x)```

Be sure to unit test your functions!

## Program 1
Write a program to print out all *prime* numbers from 1 to 100
<br>
**Implement** the following functions:
* `bool isPrime(int n)` - returns true if number n is prime
* `void printPrimes(int n)` - prints all primes from 1 to n

## Program 2
Write a program that tests whether a `string` or `int` is a palindrome
<br>
**Implement** the following functions:
* `bool isPalindrome(const string &s)` - returns true if `string` is a palindrome i.e. racecar
* **Bonus:** `bool isPalindrome(int n)` - returns true if `int` is a palindrome i.e. 12321

## Program 3
Write a program that takes in two strings from the user and outputs whether they are anagrams i.e. cat and act are anagrams
<br>
**Implement** the following function:
* `bool isAnagram(const string &a, const string &s)` - returns true if the two strings are anagrams of each other, have the same **exact** letters
