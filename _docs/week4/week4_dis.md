---
title: Week 4 Discussion
permalink: /docs/week4_dis/
---

###### Written by John Pham

# Lesson Plan

This week we will be covering:

* Operator Overloading
* Classes within classes
* What preprocessors do
* Splitting up your code into separate files

## Operator Overloading

Operator overloading allows you to add functionality to operators. Operator overloading takes this form:

`<ClassName> operator<operator>();`

An example of this is adding 2 rationals:

```cpp
class Rational {
  public:
    int numerator;
    int denominator;

    Rational operator+(Rational rhs);
}

Rational Rational::operator+(Rational rhs) {
  Rational sum;

  sum.numerator = this.numerator + rhs.numerator;
  sum.denominator = this.denominator + rhs.denominator;

  return sum;
}
```

With operator overloading, we can define mechanisms to support the classes we create.

## Friend Keyword

The friend keyword allows you to declare a non-member function with access to a classes private varaibles.

For example:
```c++
class Rectangle {
    int width, height;
  public:
    Rectangle() {}
    Rectangle (int x, int y) : width(x), height(y) {}
    int area() {return width * height;}
    friend ostream& operator<<(ostream &out, const Rectangle& rhs);
};
```

In the above class definition, we are overloading the `operator<<` function and declaring it as a friend.

We declare `operator<<` as a friend and not member function because operators are members of their left-hand arguments class. 
In this case we call the << operator with the line: `cout << "hello"`. 
The << operator is member of the cout class.

Since this function is not a member function of the Rectangle class, we do not include the `Rectangle::` when defining the function.

The function is defined like such below:
```c++
ostream& opserator<< (ostream& out, const Rectangle& rhs){
	//write code here
}
```

## Classes within classes

Classes are simply new data types that we can create. Just as we have ints, strings, and such as data members
of our classes, we can also have the classes we defined in other classes.

Let's take a look at an example of a class roster program:

```cpp
class Roster {
  private:
    vector<Student> roster;
}

class Student {
  private:
    string name;
}
```

## Preprocessors

Preprocessors allow us to modify our source files before they get compiled. Preprocessors start with `#`. You
have been using preprocessors since day one. So what does `#include <>` do? It takes whatever code you are
including into your program and replaces that line with the code from that file.

## Splitting up your code into separate files

Why should we split up our program into multiple files? Let's image we write Facebook in 1 file. Imagine how
many lines that would be. What if we want to change a feature? How do we find that feature?

We can follow the convention of splitting up our code into different files based on what functionality/feature
it is. This will make it easier to find portions of the code base that we want to modify.

When we split our code into different files, different parts of our code might need to use the same 
functionality. To minimize the size of our code, we can use **header file guards** to prevent the same file
from being imported more than once.

View the examples below:
```c++
// main.cpp

#include "Class.h"

/* rest of file */
```

```c++
// Class.h
#ifndef __CLASS_H__
#define __CLASS_H__

/* Class declaration here */

#endif
```

```c++
// Class.cpp

#include "Class.h"

/* Class definitions here */
```

To compile a program that is split into multiple files

```bash
g++ main.pp Class.cpp
```

To compile individual classes into object files, and then link them together.

```bash
# compile Class into an object file:
g++ -c Class.cpp
# compile main into an object file:
g++ -c main.cpp
# link all object files together:
g++ *.o
```
