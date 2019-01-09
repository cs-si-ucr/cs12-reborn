---
title: Week 5 Discussion
permalink: /docs/week5/
---

###### Written by Josh Beto

# Lesson Plan

This week we'll be covering splitting our code into different files (.h, .cpp) and the Makefile

## Preprocessor Directives - `#include`

A pre-processor directive is any statement beginning with a #. A common preprocessor directive you already use is the `#include`.
When you run your compiler on your program, the compiler takes your source code and scans for any pre-processor directives first.
When the compiler encounters a `#include`, you can think of this as a cue for the compiler to copy-paste whatever file you are including
to the source code that has the `#include`. 


## Splitting Your Code


**.h Files** Allows us to specify a header or class definition 

```cpp
#ifndef RECTANGLE_H
#define RECTANGLE_H

class Rectangle {
    private:
        int x, y;
    public:
        int getX() const;
        int getY() const;
        void setX(int);
        void setY(int);

        int calculateArea() const;
        bool isSquare() const;
};

#endif
```

Notice in this example that we have what is known as an *inclusion guard* at the top of the .h file, which is the `#ifndef RECTANGLE_H`.
The `#ifndef RECTANGLE_H` states that if a macro, which you can think of as a variable, is **NOT** defined, include this file. If the macro
is defined, then don't include this file. The first time you include this .h file, this macro `RECTANGLE_H` is not defined, so the file is included
and then creates a macro called `RECTANGLE_H` with the `#define RECTANGLE_H` line. Any future calls to `#include` will then *skip* over including our
class thanks to the `#ifndef RECTANGLE_H` line.

What this essentially means is that in your program, you are only ever having a single copy of your `Rectangle` class
and that it is not ever being redefined. If you didn't have this inclusion guard, you may accidently redefine your `Rectangle` class.

**.cpp Files** Allows us to implement a .h file or main()
```cpp
#include "Rectangle.h" // Notice the "" instead of the <> in the #include !

int Rectangle::getX() const {
    return x;
}

int Rectangle::getY() const {
    return y;
}

void setX(int x) {
    this->x = x;
}

void setY(int y) {
    this->y = y;
}
// ....
```

## Compiling

When your .cpp files are compiled, the compiler creates what is known as *object* files, or .o files. From there on, the compiler links 
these .o files together to create a binary, executable program such as *a.out*. Understanding this process will prove helpful in understanding
makefiles.

**Note:** Make sure to always `#include` the .h files, but compile the .cpp files!


## Makefiles

Makefiles are a way you can better automate the compilation process. With a makefile, you can specify which .cpp files to re-compile if any of the
source code changes and not have to recompile source code that has not changed. We will be going over the specific syntax of makefiles during session this week.

