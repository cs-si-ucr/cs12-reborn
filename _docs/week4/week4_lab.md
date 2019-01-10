---
title: Week 3 Lab
permalink: /docs/lab3/
---

###### Written by John Pham

# Program 1

Create a class modeled after a car. Your class should include the following data members:

* Car brand
* Year
* Type
* Miles Driven

You will then create a program that allows a user to populate a list of the cars they own. After the user is done, your program will output the cars they own.

Here's a sample of how your program should function.

```
Hello! I'm a program that will help you keep track of your car inventory. Let's get started.

What's your car's brand?
"Hyundai" // words in "" is user input

When was your car made?
"2009"

What type of car is it?
"Coupe"

How many miles have you driven in it?
"321563"

That's a pretty cool car. Do you have any other cars? If so enter 'c' or to exit enter 'q'.
"c" // this will repeat the program
"q" // this will end the loop causing the program to output

Car Inventory:
1: Hyunday, 2009, Coupe, 321563
2: ...
...
```

You should use `private` and `public` properly along with creating the appropiate getters, setters, and methods.

# Program 2

Extend program 1 by allowing the user to export their car inventory to a file after they enter 'q'. It is in the same format as the output to standard output.

```
That's a pretty cool car. Do you have any other cars? If so enter 'c' or to exit enter 'q'.
"q" // this will end the loop causing the program to output

Do you want to export your inventory to a file? 'y' for yes and 'n' for no
"y"

Your inventory was exported to a file called "car-inventory.txt"
```
