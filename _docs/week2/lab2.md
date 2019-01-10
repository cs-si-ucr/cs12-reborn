---
title: Lab
permalink: /docs/lab2/
---

###### Written by John Pham

## Parsing Command Line Arguments

For some applications, it is useful to pass in arguments from the command line to your program. Up until this point, you've been writing the `main()` but `main()` actually takes 2 arguments, `int argc` and `char* argv[]`.

`argc` is called the argument counter which counts the number of arguments passed in. Note that the program name itself counts as an argument so any additional arguments will be in index 1, 2, ..., and so on.

`argv[]` is called the argument vector which holds all of the passed in arguments. `argv[0]` will always be the name of the program. Additional arguments will be stored in index 2+.

### Program 1

You will write a program that prints all of the command line arguments that are passed.

**Example:** We have a program called `cmdArgs.cpp` which compiles to `a.out`. If we called `./a.out hello world this is my input` then the program will print:

```
hello
world
this
is
my
input
```

**DO NOT PRINT THE PROGRAM NAME**

### Program 2

You will write a program that reads <a href="{{site.baseurl}}/docs/intInputData.txt">this text file</a> and creates a new file called `squaredData.txt` where the numbers from the input file is squared.

**Example:**

Given this input file:

```
4
3
6
8
```

Your program will create this output file:

```
16
9
36
64
```

### Program 3

You will extend program 2 by checking the values of the input file. Since squaring only makes sense with numbers, we will write to the output file `"string" is not a number, cannot be squared`. You will use <a href="{{site.baseurl}}/docs/intStringInputData.txt">this text file</a> for input.

**Example:**

Given this input file:

```
4
5
0
hi
3
6
foo
3
```

Your program will create this output file:

```
16
25
0
"hi" is not a number, cannot be squared
9
36
"foo" is not a number, cannot be squared
9
```
